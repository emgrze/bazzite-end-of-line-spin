# Bazzite End of Line Spin

Custom [Bazzite](https://bazzite.gg) image with **Niri** compositor and **Noctalia** shell.

Dark cyan neon aesthetic inspired by *Tron: Legacy* (End of Line).

**Technical image name:** `bazzite-eol`

## Features

- Base: Bazzite KDE (Atomic) — full gaming stack preserved
- Compositor: Niri (scrollable tiling)
- Shell: Noctalia (Tron-inspired cyan palette)
- Browser: Brave Origin (minimal)
- Light supporting tools: Alacritty, swww, mako, Thunar, etc.
- Unnecessary KDE applications removed
- Custom Niri config with neon border style + optional GLSL shaders
- Noctalia default config shipped via `/etc/skel`

## Installation

1. Install stock **Bazzite** (KDE variant recommended).
2. Rebase to this image:

```bash
# First time (unsigned → get signing keys)
sudo bootc switch --transport ostree-unverified-registry ghcr.io/<your-username>/bazzite-eol:latest

# After reboot, switch to the signed image
sudo bootc switch ghcr.io/<your-username>/bazzite-eol:latest
```

Or the classic way:

```bash
sudo rpm-ostree rebase ostree-image-signed:docker://ghcr.io/<your-username>/bazzite-eol:latest
```

3. Reboot.
4. At the login screen (SDDM) select the **niri** session.
5. For an existing user, copy the default Noctalia config if needed:

```bash
cp -r /etc/skel/.config/noctalia ~/.config/
```

## Building your own

This repository uses [BlueBuild](https://blue-build.org/).

1. Click **Use this template** (or fork).
2. Generate a cosign keypair and add the private key as repository secret `SIGNING_SECRET`.
3. Edit `recipes/recipe.yml` (packages, base image, etc.).
4. Put configuration files under `files/system/` (they are copied into the image root).
5. Push to `main` — GitHub Actions builds and publishes to GHCR.

## Notes

- This is an unofficial community image.
- Not affiliated with Disney or the Tron franchise.
- Avoid using trademarked names (Tron, ENCOM, Flynn, etc.) in public branding.
