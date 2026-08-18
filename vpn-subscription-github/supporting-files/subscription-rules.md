# Subscription rules

## Authoritative server sources

When the requester asks to refresh or update the server array, fetch configurations from all of these subscriptions, in the order listed:

1. `https://sub.extravpn.net/NjFJLGbsYggCxueg`
2. `https://auth.easy-api.live/E4U6k-HNN45wrR5-`
3. `https://auth.easy-api.live/1kBe9eH6SskuPase`

Use their current contents to update the old server set. Do not retain stale server configurations that are absent from the refreshed sources, unless the requester explicitly asks to preserve a specific configuration. Treat every configuration occurrence returned by a source as independent: repeated or identical entries must remain separate.

## Server preservation

- Treat every supplied file or server as one independent configuration entry.
- Never deduplicate, merge, omit, or delete repeated configurations merely because they are identical.
- Combine servers into an auto-selection entry only after an explicit request to do so.

## Ordering

1. Place all whitelist-bypass entries first.
2. Place ordinary VPN entries after all whitelist-bypass entries.
3. Preserve the requested/source ordering within each category when no more specific order is given.

## Names

Rename every refreshed or supplied server according to its category:

- Whitelist-bypass entry: `(<flag>)Белые Списки | (<country>)`
- Ordinary VPN entry: `(<flag>)(<country>) Vpn`
- If the requester asks for a suffix, append it consistently, for example: ` | Для ИИ`.

Use the actual country determined from the configuration; do not infer it from a filename alone when configuration metadata or endpoint data can establish it.

## Descriptions

Do not add server descriptions. When asked to prepare a cleaned subscription, remove existing per-server descriptions without altering the configuration itself.
