# dotfiles

My Ubuntu desktop and terminal setup for a ThinkPad P14s Gen 5 (AMD), running Ubuntu 26.04 LTS with GNOME 50. The theme is red and black: minimal, but with live system stats and a techy terminal.

## What's in here

| File | What it does |
| --- | --- |
| `starship.toml` | Two-line red Starship prompt with git branch, git status, Python version, and command duration |
| `.bashrc` | Bash config that loads Starship and runs fastfetch on terminal open |
| `gnome-extensions.dconf` | Saved settings for all GNOME extensions (Vitals, Just Perfection, Blur my Shell, dock) |

## Setup overview

**Desktop**
- Accent color: red, dark style (Yaru-red-dark)
- Icons: Papirus-Dark with red folders (via `papirus-folders`)
- Cursor: Bibata-Modern-Classic
- Extensions: Vitals (CPU temp, CPU usage, RAM, network in the top bar), Just Perfection (slimmer panel, faster animations), Blur my Shell
- Dock: bottom, floating, auto-hide

**Terminal**
- Terminal: Ptyxis with the Linux palette at 90% opacity
- Font: JetBrainsMono Nerd Font Mono
- Prompt: Starship
- Extras: fastfetch, btop, eza (ls with icons), bat (cat with highlighting), zoxide (smart cd), fzf (fuzzy search)

## Restoring on a new machine

1. Install the tools:
```bash
sudo apt install starship fastfetch btop eza bat zoxide fzf papirus-icon-theme gnome-tweaks gnome-shell-extension-manager
```
2. Install JetBrainsMono Nerd Font from [nerdfonts.com](https://www.nerdfonts.com/) into `~/.local/share/fonts`, then run `fc-cache -f`.
3. Copy the Starship config:
```bash
   mkdir -p ~/.config
   cp starship.toml ~/.config/starship.toml
```
4. Add these lines to the end of `~/.bashrc` (or compare with the included `.bashrc`):
```bash
   eval "$(starship init bash)"
   fastfetch
```
5. Install the extensions through Extension Manager, then restore their settings:
```bash
   dconf load /org/gnome/shell/extensions/ < gnome-extensions.dconf
```
6. Log out and back in.

## Notes

- VS Code installed as a Snap won't see fonts in `~/.local/share/fonts`. Copy the font to `/usr/local/share/fonts` and run `sudo fc-cache -f`.
- Set VS Code's terminal font to `'JetBrainsMono Nerd Font Mono', monospace` so the prompt icons render.
