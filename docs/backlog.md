# Playground backlog (jobs for later)

Boss's order of priority applies; nothing here is started until he says so.

## Share Gitea with someone outside the network (added 9 Oct 2026)

Boss wants to share his Git with a person outside his network. Not started. Needs from Boss: which repo, and who (their email).

| Option | How | Pros | Cons |
|---|---|---|---|
| Recommended: Cloudflare Access in front of Gitea | New hostname (like `git.<domain>`) through a tunnel, with an Access rule allowing only that person's email; give them a separate read-only Gitea account | same pattern already used for Nextcloud; revoke by removing one email; no login shared | Gitea becomes reachable from the internet behind that login; tunnel and DNS to set up |
| VPN for that person (WireGuard on the router, or Tailscale) | they join the network and open Gitea on the LAN | nothing public | gives them wider network reach unless restricted; more setup for them |
| One-off export | send a repo archive over a link Boss controls | nothing exposed | not live; no collaboration |

Rules that apply: outward-facing, so confirm before any change; self-hosted first; a read-only account for the guest; keep the finance and work material out of any shared repo; reversible (remove the Access rule and hostname to undo).

## Other later jobs

- Daily and security briefs that need internet (kept apart from system access by design).
- Create the read-only TrueNAS API key for the TrueNAS reports.
- Decide which folders may be indexed by the document search.
