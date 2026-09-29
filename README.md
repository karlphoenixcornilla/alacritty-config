# alacritty-config

> **Branches:** `main` tracks the Windows config (Git Bash shell, `...NFM`
> font family). `macos` tracks the macOS config (no shell override, `...Nerd
> Font Mono` family). `starship.toml` is shared and kept identical on both —
> mirror any prompt change to the other branch.

My [Alacritty](https://alacritty.org) terminal config — the
[carbonfox](https://github.com/EdenEast/nightfox.nvim) palette, JetBrainsMono
Nerd Font, and a matching [Starship](https://starship.rs) prompt.

![carbonfox](https://img.shields.io/badge/theme-carbonfox-78a9ff?style=flat-square)
![font](https://img.shields.io/badge/font-JetBrainsMono%20NL-be95ff?style=flat-square)
![prompt](https://img.shields.io/badge/prompt-starship-25be6a?style=flat-square)

## Files

| File            | What it does                                                  |
| --------------- | ------------------------------------------------------------- |
| `alacritty.toml`| Shell, font, key bindings, and the full carbonfox color scheme |
| `starship.toml` | Two-line powerline prompt in the same palette                 |
| `install.md`    | Font, Starship, and shell-init setup for Windows/macOS/Linux   |

## What's in it

- **carbonfox** colors throughout — the same hex values in the terminal palette
  and the prompt, so the two never drift apart.
- **JetBrainsMonoNL NFM** at size 10 — the no-ligature *Mono* variant, which
  keeps every glyph single-width so Nerd Font icons don't break column
  alignment.
- **Git Bash as the shell**, launched with `--login`.
- **Readline key bindings** that Windows terminals otherwise swallow:
  `Ctrl+Backspace` (delete word back) and `Alt+H` (delete to line start).
- **Starship prompt** — blue path, purple git branch and status, grey language
  version, right-aligned command duration, and a green/red `❯` on its own line.

## Setup

```bash
git clone https://github.com/karlphoenixcornilla/alacritty-config.git
```

Copy `alacritty.toml` to your platform's Alacritty config directory and
`starship.toml` to `~/.config/`:

| Platform      | Alacritty config path                |
| ------------- | ------------------------------------ |
| Windows       | `%APPDATA%\alacritty\alacritty.toml` |
| macOS / Linux | `~/.config/alacritty/alacritty.toml` |

See **[install.md](install.md)** for the rest — installing the Nerd Font (the
family name differs per platform, and Alacritty falls back silently when it
doesn't match), installing Starship, and the shell init that Git Bash needs on
Windows.

## Notes

Alacritty hot-reloads config changes; restart the terminal if one doesn't take.

`starship.toml` must be copied to `~/.config/starship.toml` — nothing syncs it
from this repo, so edits in either place need copying to the other.

## License

[GPL-3.0](LICENSE)
