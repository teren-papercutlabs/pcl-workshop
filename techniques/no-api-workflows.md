# No-API Workflows

When the external platform the participant depends on has **no API, an inaccessible API, or an API they can't get credentials for** — you can still automate. The technique is HAR capture and replay.

## When to Use This

The participant has an external platform in their workflow (internal tool, third-party SaaS, legacy system), and one of:

- The platform has no public API
- The API exists but the participant can't access it (IT gate, no admin, licensing)
- The API exists but is undocumented and reverse-engineering docs isn't worth it
- The auth is SSO/browser-based and can't easily be replicated with API keys

Signal from `/interview`: the brief flagged "external platform, no API access".

## The Technique: HAR Capture and Replay

A HAR file (HTTP Archive) is a recording of all the HTTP requests a browser makes while the user does something. Chrome, Firefox, Safari, and Edge can all export HAR.

The idea: have the participant do the workflow manually **once** in their browser while recording. You inspect the HAR to see exactly what requests are made, with what auth, with what payloads. Then you write a CLI or script that replays those requests programmatically.

## Procedure

### 1. Have them record the workflow

Guide them:

1. Open the platform in Chrome (or their browser).
2. Open Developer Tools → Network tab.
3. Tick "Preserve log".
4. Do the workflow they normally do — log in, click through, submit the thing, receive the response.
5. Right-click in the Network tab → Save all as HAR with content.
6. Drop the `.har` file into the project folder.

Tell them in plain language: "I need you to do the thing once in your browser while it records what's happening under the hood. It's a one-time recording — once I have it, I can replay the steps without you."

### 2. Inspect the HAR

HAR files are JSON. The `log.entries` array lists each request with method, URL, headers, cookies, payload, response.

Parse it. Look for:

- **The actual business request** — usually a POST or GET that returns the data or performs the action. Not the 200 CSS fetches or the tracking pixels.
- **Auth mechanism** — is it a Bearer token in a header? A session cookie? A CSRF token? If it's a session cookie, figure out where it came from (a login request earlier in the HAR).
- **Request shape** — URL, method, headers, payload structure.
- **Response shape** — what comes back, in what format.

Use PcL's `pcl carbon inspect --file <export>.har --network --auth` if the HAR is big or if you want structured extraction. Otherwise just grep and read.

### 3. Build the script

Write a CLI or script that replicates the key requests. Usually Node.js with `fetch` or Python with `requests`.

- Auth: replicate whatever the browser did. If it's a session cookie, the script either needs the participant to paste a fresh cookie periodically, or you automate login (only if login is API-replicable, not SSO).
- Requests: craft the same method, URL, headers, payload.
- Response parsing: whatever shape the HAR showed.

### 4. Test against the recording first

Before running live, test the script's requests against what the HAR recorded. Same URL? Same method? Same key headers? Same payload structure?

This catches 80% of errors before a live call.

### 5. Run it live

Call the real platform. If it 401s or 403s, the auth is stale — ask for a fresh HAR recording or a fresh cookie.

## Auth Gotchas

- **Session cookies expire.** Most are valid hours to days. The participant will need to refresh the cookie periodically. Document this in `MEMORY.md`.
- **CSRF tokens rotate.** Some platforms require a CSRF token that changes per session. The HAR will show where it's fetched — usually embedded in a HTML page response. Your script may need to scrape it first.
- **SSO** (Okta, Azure AD, Google SSO) is generally not API-replicable. If the login is SSO, you're stuck with the "participant pastes cookie" workflow.

## Key Principle

You're not hacking the platform. You're replaying the exact same HTTP requests the participant's browser already makes when they use it normally. The platform can't tell the difference (that's the point).

If the platform has terms of service that prohibit automated access, that's a decision the participant makes. Flag it. Don't decide for them.
