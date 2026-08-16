# Setup: VPN subscription publishing and private access links

This package captures the setup specific to this thread. It deliberately excludes credentials, cookies, authorization keys, connection identifiers, automation identifiers, and account identifiers.

## What must be connected or logged in

### GitHub connection
Connect a GitHub account with read and repository-content write access to the repositories used for subscriptions. The account should be able to read the repositories named `Lite` and `Premium` (sometimes called King in requests), and create branches and pull requests.

Use GitHub to:

- read the current `Sub` file before every change;
- use `Lite/Sub` as the source for Lite links;
- use `Premium/Sub` as the source for King/Premium links;
- publish subscription-file edits using a dedicated branch and pull request;
- update the same PR branch if edits are requested before merging.

Do not assume the agent can merge a pull request. A repository collaborator may need to merge it.

### Short.io
There is no API connection configured. Use an authenticated browser session at Short.io. The user must sign in themselves if the session is absent.

Create one short link for each requested private subscription. The destination must be the appropriate GitHub subscription link obtained above. Do not reuse an existing short link unless the user specifically asks to reuse it.

### Happ
There is no API connection configured. Use an authenticated browser session at Happ. The user must sign in themselves if the session is absent.

Create the private access entry using the short link created in Short.io. The normal workflow is:

`GitHub subscription source → Short.io short URL → Happ private access entry → deliver resulting Happ subscription URL`

Use the device limit requested by the user; default to **2** when none is supplied. Put the user-provided label in the description, not the internal name, unless the user explicitly changes that rule or specifically asks for an available display title.

A prior Happ authorization key was posted in chat. Treat it as potentially compromised: do not echo it, archive it, or use it unless strictly necessary; recommend rotation.

## How to process a request for private links

1. Extract the count, plan, requested labels, and device limit.
2. Ask one clarification only if a material detail is missing (most often Lite versus King/Premium). Device limit defaults to 2.
3. For every requested link independently, obtain the corresponding current `Sub` source from GitHub.
4. Create an independent short link in Short.io.
5. Create an independent Happ entry containing that short link. Do not consolidate several requested people into one entry.
6. Set the requested description. Do not place that text in the entry name by default.
7. Deliver each final Happ URL in its own `.txt` file, one URL per file. Use the requested description as a safe file name where possible.

## Deletion behavior

When the user asks to remove a created private subscription:

- delete its matching short link from Short.io;
- disable the corresponding Happ entry (the observed Happ UI offered disable rather than permanent deletion);
- do not alter the GitHub source subscription file unless the user explicitly requests that.

Report disabled Happ entries as disabled, not deleted.

## Subscription file publishing rules

Read `vpn-subscription-github/SKILL.md` and both files in its `supporting-files` folder before changing any GitHub subscription data. These rules are mandatory:

- Every supplied server/file is a separate configuration entry, including exact duplicates.
- Never deduplicate, merge, omit, or delete a repeated server because it looks identical.
- Make auto-selection groups only on an explicit request.
- Put whitelist-bypass entries before ordinary VPN entries.
- Whitelist name: `(<flag>)Белые Списки | (<country>)`.
- Normal VPN name: `(<flag>)(<country>) Vpn`.
- Do not add server descriptions.
- Determine the country from configuration data where possible, rather than a filename alone.

## Automations

None exist or are required in this thread. Do not add one without a concrete trigger, source, and desired outcome from the user.

## Database

No tables exist and no database is used. GitHub subscription files and the relevant service panels are the sources of truth. Do not introduce a database unless there is a genuine need to track structured state across runs.

## Custom instruction

The agent-wide custom instruction that was active when this package was made is copied verbatim in `agent-custom-instructions.md`. It is not a VPN workflow rule. If setting up a separate agent, apply it only if it remains appropriate there.

## Current historical state (do not recreate automatically)

- A pull request exists or existed for adding a Germany AI whitelist configuration to `Premium/Sub`; its merge status should be checked before any related changes.
- One test Lite private subscription labeled “реклама” was disabled in Happ and its matching Short.io link was deleted. Do not re-enable or recreate it unless explicitly requested.
