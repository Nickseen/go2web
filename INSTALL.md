# go2web Installation Guide

This guide explains how to install `go2web` for any Linux user and run it from any directory.

## 1. Clone and enter the repository

```bash
git clone <your-repo-url>
cd tum-web
```

## 2. Install the CLI to user-local bin

```bash
mkdir -p "$HOME/.local/bin"
cp ./go2web "$HOME/.local/bin/go2web"
chmod +x "$HOME/.local/bin/go2web"
```

## 3. Ensure ~/.local/bin is in PATH

```bash
grep -q 'export PATH="$HOME/.local/bin:$PATH"' "$HOME/.bashrc" || \
  echo 'export PATH="$HOME/.local/bin:$PATH"' >> "$HOME/.bashrc"
```

## 4. Optional: add short alias `g2w`

```bash
grep -q 'alias g2w=' "$HOME/.bashrc" || \
  echo 'alias g2w="go2web"' >> "$HOME/.bashrc"
```

## 5. Reload shell config

```bash
source "$HOME/.bashrc"
```

## 6. Verify installation

```bash
command -v go2web
command -v g2w
go2web -h
```

If `g2w` is not found, either open a new terminal or run:

```bash
source "$HOME/.bashrc"
```

## Troubleshooting

### A) "alias: g2w: not found"

This means `g2w` is not an alias yet. Add it using Step 4.

### B) Bash startup error for missing completion file

If you see an error like:

```text
bash: /home/<user>/.openclaw/completions/openclaw.bash: No such file or directory
```

replace a direct `source` with a guarded one in `~/.bashrc`:

```bash
[ -f "$HOME/.openclaw/completions/openclaw.bash" ] && source "$HOME/.openclaw/completions/openclaw.bash"
```

This prevents bash from failing when that file does not exist.
