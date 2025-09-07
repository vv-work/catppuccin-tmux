# Repository Guidelines

## Project Structure & Module Organization
- Root: `catppuccin.tmux` (main plugin script) and `catppuccin-*.tmuxtheme` (per-flavour palettes: latte, frappe, macchiato, mocha).
- Assets: previews in `assets/` used by `README.md`.
- Config: `.editorconfig` defines indentation/line-endings. No build system or test suite.

## Build, Test, and Development Commands
- No build step; iterate live in tmux.
- Reload config after edits: `tmux source-file ~/.tmux.conf`.
- With TPM: update `.tmux.conf` then press `prefix + I` to install/update; `prefix + r` to reload (if bound).
- Inspect options while debugging: `tmux show-options -g | rg catppuccin`.
- Switch flavours quickly: `set -g @catppuccin_flavour 'latte'` then reload.

## Coding Style & Naming Conventions
- Shell: Bash script (`#!/usr/bin/env bash`); prefer portable tmux commands.
- Indentation: 2 spaces; LF line endings (see `.editorconfig`).
- Quotes: always quote variables; use `local` within functions.
- Theme vars: use `thm_*` (e.g., `thm_bg`, `thm_blue`). Hex colors must be lowercase.
- Options: user-facing tmux options are `@catppuccin_*` (e.g., `@catppuccin_window_tabs_enabled`).
- Filenames: flavours as `catppuccin-<flavour>.tmuxtheme`.

## Testing Guidelines
- Manual validation in a tmux session:
  - Toggle window tabs: `set -g @catppuccin_window_tabs_enabled on|off`.
  - Verify separators: `@catppuccin_left_separator`, `@catppuccin_right_separator`.
  - Check optional components: `@catppuccin_user`, `@catppuccin_host`, `@catppuccin_date_time`.
  - Confirm glyphs render using a Nerd Font.
- Test all four flavours for parity; keep status segments aligned and legible.

## Commit & Pull Request Guidelines
- Commits: prefer Conventional Commits (`feat:`, `fix:`, `perf:`, `docs:`). Keep scopes small and messages imperative.
- PRs must include:
  - Clear description of changes and rationale.
  - Before/after screenshot of the statusline (add to PR, not repo).
  - Updates to `README.md` when adding options or changing defaults.
  - Consistent changes across all `catppuccin-*.tmuxtheme` files when applicable.
- Run a quick shell sanity check (e.g., `shellcheck`) if available and ensure tmux reloads without errors.

