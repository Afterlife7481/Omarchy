# Omarchy machine setup

Personal setup scripts for a fresh [Omarchy](https://omarchy.org) install.

## Bootstrap a new machine

```bash
cd ~
curl -fsSLO https://raw.githubusercontent.com/Afterlife7481/Omarchy/main/omarchy-machine-setup
bash omarchy-machine-setup          # or: SUDO=pkexec bash omarchy-machine-setup
rm omarchy-machine-setup            # from here on use the PATH copy
```

`omarchy-machine-setup` is idempotent — re-run it any time. On its first run
it clones this repo to `~/Gitrepos/Afterlife7481/Omarchy` and symlinks its
scripts into `~/.local/bin`, so the downloaded copy is a one-shot bootstrap:
delete it once the real command is on `PATH`. From then on, edits happen in
this working tree and are git-tracked automatically.

Cloning uses anonymous HTTPS, since a brand-new machine has no key on GitHub
yet. The script then points this repo's push URL at SSH and generates a
dedicated key — see the printed public key, or re-run to see it again with
`cat ~/.ssh/Afterlife7481.pub`. Add it at GitHub → Settings → SSH and GPG
keys, and `git push` / `git pull` work from here on.

## Scripts

- **omarchy-machine-setup** — system baseline: directories, this repo +
  symlinks, GitHub SSH key, web-app/package removal, package installs,
  Chromium extension policy, screensaver banner, Hyprland input tweaks.
- **omarchy-workspace-setup** — lay out apps across workspaces 1–4 on a fresh
  Hyprland session. Run per session, not part of the machine baseline.

Everything each script does is configured in the CONFIG block near the top of
its own file — read the comments there before changing anything.
