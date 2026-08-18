---
name: vpn-subscription-github
description: Maintain a GitHub-hosted VPN subscription file while preserving every supplied server separately. Use when adding, refreshing from the configured source subscriptions, renaming, ordering, or publishing VPN and whitelist server configurations to a repository.
---

# VPN subscription + GitHub publishing

Use this workflow for a subscription file managed in a GitHub repository.

## Required setup

Read `supporting-files/setup.md` before making changes. It records the service access, publishing approach, and components intentionally not used by this workflow.

Read `supporting-files/subscription-rules.md` before editing any configuration. These rules are mandatory and override convenience operations such as deduplication.

## Workflow

1. Obtain the current subscription file from the repository and inspect its format and ordering.
2. When refreshing servers, fetch every configured source subscription in `subscription-rules.md`. Use the fetched configurations to update the old server set; do not leave stale configurations from the previous source version.
3. Read each supplied configuration independently. Determine its country before naming it.
4. Apply the naming and ordering rules exactly as written in `subscription-rules.md`.
5. Preserve all fetched or supplied configurations as distinct entries, including byte-for-byte or semantically identical duplicates.
6. Remove per-server descriptions only when preparing the requested clean subscription output; otherwise do not make unrelated changes.
7. Validate that the resulting file parses and that every source or supplied server is present once per input occurrence.
8. Publish by creating a dedicated branch and pull request. If further edits are requested before merge, update the same branch.
9. Report the PR link and clearly state whether a manual merge is still required.

## Change discipline

- Do not silently replace the repository version with a local file without checking the current source first.
- Do not combine servers into auto-selection groups unless the requester explicitly asks for that exact grouping.
- Keep the change limited to the requested subscription file unless the requester asks for documentation or application changes too.
