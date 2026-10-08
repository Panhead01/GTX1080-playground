# Playground chat page (set up 9 October 2026)

The playground = the GTX 1080 AI Playground project. Its chat page lets Boss talk to the local model on Mimir from his desktop browser.

## What is running (CONFIRMED, tested 9 Oct 2026)

| Part | Detail |
|---|---|
| Host | VM 101 "Mimir", 192.168.0.58 |
| Chat page | Hollama, a browser-side chat UI, built from reviewed source (tarball sha256 `c27d4970eca344dcd975260ffd5fe00856a7b6619bc8ecd4d9c55eb716fd0c77`, commit `9baa056d8f8f7ab2c0ccb58d7319a9374862b966`), run as a rootless podman container through a quadlet (`~/.config/containers/systemd/hollama.container`) |
| Front door | nginx on port 80; `/` goes to Hollama, `/ollama/` goes to Ollama on 127.0.0.1:11434 |
| Access control | nginx allows 192.168.0.249 (Boss's desktop) only; everyone else gets 403 |
| Model server | Ollama v0.40.0 as a systemd service, bound to localhost only |
| Model | qwen3:8b |

## Browser settings (done)

Settings page, Servers: connection type Ollama, Base URL `http://192.168.0.58/ollama`, "Use models from this server" ticked, Verify passed ("Connection has been verified and is ready to use"). "Automatically check for updates" is off, so the page makes no outside calls.

## Still to do by hand

Add a Proxmox firewall rule on VM 101: default drop in, allow TCP port 80 from 192.168.0.249 only.

## Undo

Stop the container (`systemctl --user stop hollama`), remove the nginx site, or restore Proxmox snapshot `pre-chat-ui` on VM 101.

## Note

Hollama keeps chats in the browser, so history lives in that browser only. Nothing is stored on Mimir.
