# Playground backlog (jobs for later)

Boss's order of priority applies; nothing here is started until he says so.

## Share Gitea with someone outside the network (added 9 Oct 2026)

Boss wants to share his Git with a person outside his network. **Decided 9 Oct 2026 (Boss, evening, revised the same evening):** no tunnel and nothing inbound. Gitea **push mirrors** send `hermes-build` and `GTX1080-playground` one-way to private repositories in a free GitHub organisation (owner: Boss's GitHub account); the person is added to that organisation with the Read role. `workstation` is left out entirely. Why an organisation: collaborators on a personal GitHub repository can always push; GitHub's docs say there is no read-only collaborator on personal repos (CONFIRMED). The mirror force-pushes on every merge and on a timer, so GitHub is a copy, never the source. A content scan of all three repos on 9 Oct found no secrets, emails, phone numbers or surnames; LAN addresses, hostnames and usernames are present and accepted for a private mirror. Vendor route (GitHub holds the copy), flagged and accepted. Steps with exact values: `~/Documents/Workstation/Gitea/github-mirror-steps-2026-10-09.md`. Still needed from Boss: the person's GitHub username, and the hand steps (organisation, two empty repos, fine-grained token with Contents read and write on those two repos, the two push mirrors in Gitea, invite with Read role). The earlier Cloudflare tunnel plan is kept for reference in `git-tunnel-access-steps-2026-10-09.md`.

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
