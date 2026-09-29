# Install

## Font: JetBrainsMono Nerd Font

`alacritty.toml` uses the **NL** (no-ligature) **Mono** variant of JetBrainsMono
Nerd Font. The Mono variant keeps every glyph single-width, which is what a
terminal needs to avoid broken column alignment.

> **The family name differs per platform.** Windows truncates font names to fit
> its 31-character registry limit, so the same font is `JetBrainsMonoNL NFM`
> there but `JetBrainsMonoNL Nerd Font Mono` under fontconfig on macOS and
> Linux. Alacritty silently falls back to a default font when the name does not
> match, so check the table below after installing.

| Platform      | `family` value in `alacritty.toml` |
| ------------- | ---------------------------------- |
| Windows       | `JetBrainsMonoNL NFM`              |
| macOS / Linux | `JetBrainsMonoNL Nerd Font Mono`   |

### Windows

```powershell
winget install --id DEVCOM.JetBrainsMonoNerdFont
```

Installs the full set (NF, NFM, NFP, with and without ligatures) into
`C:\Windows\Fonts`. Verify the registered family name:

```powershell
Add-Type -AssemblyName System.Drawing
(New-Object System.Drawing.Text.InstalledFontCollection).Families |
  Where-Object { $_.Name -like "*JetBrains*" } |
  Select-Object -ExpandProperty Name
```

Alternatives:

```powershell
scoop bucket add nerd-fonts; scoop install nerd-fonts/JetBrainsMono-NF-Mono
choco install nerd-fonts-jetbrainsmono
```

### macOS

```bash
brew install --cask font-jetbrains-mono-nerd-font
```

Verify:

```bash
fc-list | grep -i "JetBrainsMonoNL"
```

`fc-list` comes from fontconfig (`brew install fontconfig`); without it, look
for the font in Font Book instead.

### Linux

Arch:

```bash
sudo pacman -S ttf-jetbrains-mono-nerd
```

Debian, Ubuntu, Fedora, and most others do not package the Nerd Font patched
build — their `fonts-jetbrains-mono` / `jetbrains-mono-fonts` packages are the
*unpatched* upstream font with no icon glyphs. Install manually instead:

```bash
mkdir -p ~/.local/share/fonts
curl -fLo /tmp/JetBrainsMono.zip \
  https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
unzip -o /tmp/JetBrainsMono.zip -d ~/.local/share/fonts/JetBrainsMono
rm /tmp/JetBrainsMono.zip
fc-cache -fv
```

Verify:

```bash
fc-list | grep -i "JetBrainsMonoNL"
```

## Config

Alacritty reads its config from:

| Platform      | Path                                  |
| ------------- | ------------------------------------- |
| Windows       | `%APPDATA%\alacritty\alacritty.toml`  |
| macOS / Linux | `~/.config/alacritty/alacritty.toml`  |

Config changes are hot-reloaded; restart the terminal if one does not take
effect.
