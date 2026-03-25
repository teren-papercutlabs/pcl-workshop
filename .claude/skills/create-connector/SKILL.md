---
name: create-connector
description: "Build a CLI tool that wraps an external API. Walks through API analysis, permission scoping, and CLI generation. Trigger for: /create-connector, connect to API, build a connector, wrap this API, integrate with."
---

# Create Connector

Build a CLI tool that wraps an external API with appropriate safety boundaries.

## Procedure

### Step 1: Understand the API

Ask the user for their API details. They might provide:
- API documentation (URL or file)
- An API key or OAuth credentials
- A description of what the service does

Read the documentation. If they gave you a URL, fetch it. If they gave you a file, read it. Understand the full surface area.

### Step 2: Present What You Found

List every capability you discovered, grouped by category. For example:

**Read operations** (safe — just fetching data):
- List all orders
- Get customer details
- View inventory levels

**Create operations** (creates new things in their system):
- Create a new order
- Add a customer
- Create an invoice

**Update operations** (modifies existing data):
- Update order status
- Change customer details

**Delete operations** (removes data — potentially dangerous):
- Delete an order
- Remove a customer

**Send operations** (reaches out to the external world — emails, messages, notifications):
- Send an invoice email
- Send a notification

### Step 3: Scope the Permissions

Ask the user explicitly:

> "Here's everything this API can do. Which of these do you want your CLI to support?"
>
> "Specifically — is there anything you do NOT want me to have access to? Common things people restrict:"
> - **Send operations** (sending emails, messages, notifications)
> - **Delete operations** (removing data permanently)
> - **Create operations** that affect external parties (creating invoices that get sent, placing orders)
>
> "It's fine to start narrow and add more later."

Wait for their answer. Do not proceed until they've explicitly confirmed what's in and what's out.

### Step 4: Build the CLI

Create a CLI tool in the project directory. Use whatever language makes sense (Node.js, Python, Bash — pick based on the API client libraries available).

The CLI should:
- Have a clear command for each approved operation
- Include `--help` for every command
- Store API credentials in an environment variable (never hardcoded)
- Print human-readable output by default
- Support `--json` flag for machine-readable output where useful

Structure: one file per command group, a main entry point, a README.

### Step 5: Test Together

Run through 2-3 operations with the user to verify they work. Fix anything that breaks.

### Step 6: Commit

Once working, commit the CLI to git with a clear commit message describing what it connects to and what it can do.

## Key Principle

**The user decides what the tool can do, not you.** Your job is to present the full picture clearly so they can make an informed decision. Never include operations they didn't approve. When in doubt, leave it out and ask.
