# Setup specific to this workflow

## Connection: GitHub

Connect the agent to the GitHub account that owns or has write access to the target repository. The connection must be granted access to that repository and permission to write repository contents.

Use the connection as follows:

- Read the current subscription file before every change.
- Create a new branch and pull request when publishing a new change.
- Push later amendments to that pull request's branch.
- If the available GitHub actions do not include merging pull requests, leave merging to a repository collaborator and provide the PR link.

If GitHub reports an access error, have the repository owner enable the app installation, select the target repository (or all repositories), grant repository-content write access, and refresh the connection authorization.

## Automations

No automation is required or configured for this workflow. Changes are performed when a requester supplies a configuration and publishing instruction.

Do not add a scheduled or event-driven automation unless the requester defines a concrete trigger, source, and desired publishing behavior.

## Database

No database is required or used. The subscription file in the repository is the source of truth; transient working copies may be kept only while processing a requested update.

## Custom instructions

No account-specific custom-instruction file is required. The portable operational rules for this setup are in `subscription-rules.md` and must be followed for every update.

If an agent-wide instruction file is later used, keep it generic and do not put repository names, usernames, tokens, private URLs, or other account-specific details in the shared skill.
