# Subscription rules

## Server preservation

- Treat every supplied file or server as one independent configuration entry.
- Never deduplicate, merge, omit, or delete repeated configurations merely because they are identical.
- Combine servers into an auto-selection entry only after an explicit request to do so.

## Ordering

1. Place all whitelist-bypass entries first.
2. Place ordinary VPN entries after all whitelist-bypass entries.
3. Preserve the requested/source ordering within each category when no more specific order is given.

## Names

- Whitelist-bypass entry: `(<flag>)Белые Списки | (<country>)`
- Ordinary VPN entry: `(<flag>)(<country>) Vpn`
- If the requester asks for a suffix, append it consistently, for example: ` | Для ИИ`.

Use the actual country determined from the configuration; do not infer it from a filename alone when configuration metadata or endpoint data can establish it.

## Descriptions

Do not add server descriptions. When asked to prepare a cleaned subscription, remove existing per-server descriptions without altering the configuration itself.
