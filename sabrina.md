---
layout: page
title: Sabrina
permalink: /sabrina/
---

```
cat > swap_aerial.sh <<'SH'
#!/usr/bin/env bash
set -euo pipefail

# -----------------------------
# Inputs (your links)
# -----------------------------
VIDEO_URL="https://connorpasse.com/assets/SabrinaCarpenter.mov"
PNG_URL="https://connorpasse.com/assets/sabrina.png"

# -----------------------------
# Aerial asset locations (per-user)
# -----------------------------
VIDEO_DIR="${HOME}/Library/Application Support/com.apple.wallpaper/aerials/videos"
THUMB_DIR="${HOME}/Library/Application Support/com.apple.wallpaper/aerials/thumbnails"

# Restart agents to encourage macOS to notice the change
RESTART=1

# -----------------------------
# Helpers
# -----------------------------
log() { printf "• %s\n" "$*"; }
die() { printf "✖ %s\n" "$*" >&2; exit 1; }

need_dir() {
  [[ -d "$1" ]] || die "Missing directory: $1
Tip: open System Settings → Screen Saver and preview an Aerial once so assets download."
}

# Pick FIRST alphabetically (excluding any backups we create)
pick_first_mov() {
  shopt -s nullglob
  local files=("$VIDEO_DIR"/*.mov)
  shopt -u nullglob

  (( ${#files[@]} > 0 )) || die "No .mov files found in: $VIDEO_DIR"

  # Filter out backup files, then sort
  local filtered=()
  local f
  for f in "${files[@]}"; do
    [[ "$(basename "$f")" == backup_*.mov ]] && continue
    filtered+=("$f")
  done

  (( ${#filtered[@]} > 0 )) || die "Only backups found; no original .mov candidates in: $VIDEO_DIR"

  # Sort safely (newline-delimited; Aerial filenames virtually never contain newlines)
  local chosen
  chosen="$(printf '%s\n' "${filtered[@]}" | LC_ALL=C sort | head -n 1)"
  printf '%s' "$chosen"
}

# -----------------------------
# Main
# -----------------------------
need_dir "$VIDEO_DIR"
need_dir "$THUMB_DIR"

TARGET_MOV="$(pick_first_mov)"
TARGET_BASE="$(basename "$TARGET_MOV")"
TARGET_STEM="${TARGET_BASE%.mov}"
TARGET_PNG="${THUMB_DIR}/${TARGET_STEM}.png"

[[ -f "$TARGET_PNG" ]] || die "Expected thumbnail not found: $TARGET_PNG"

TS="$(date +%Y%m%d_%H%M%S)"
BACKUP_MOV="${VIDEO_DIR}/backup_${TS}.mov"
BACKUP_PNG="${THUMB_DIR}/backup_${TS}.png"

log "Selected MOV: $TARGET_MOV"
log "Selected PNG: $TARGET_PNG"
log "Backups:"
log "  $BACKUP_MOV"
log "  $BACKUP_PNG"

TMPDIR="$(mktemp -d)"
cleanup() { rm -rf "$TMPDIR" >/dev/null 2>&1 || true; }
trap cleanup EXIT

DOWN_MOV="${TMPDIR}/download.mov"
DOWN_PNG="${TMPDIR}/download.png"

log "Downloading video…"
curl -fL --retry 3 --retry-delay 1 -o "$DOWN_MOV" "$VIDEO_URL"

log "Downloading png…"
curl -fL --retry 3 --retry-delay 1 -o "$DOWN_PNG" "$PNG_URL"

log "Backing up originals…"
cp -f "$TARGET_MOV" "$BACKUP_MOV"
cp -f "$TARGET_PNG" "$BACKUP_PNG"

log "Replacing (keeping original filenames)…"
cp -f "$DOWN_MOV" "$TARGET_MOV"
cp -f "$DOWN_PNG" "$TARGET_PNG"

if [[ "$RESTART" == "1" ]]; then
  log "Restarting wallpaper/screensaver agents…"
  killall WallpaperAgent >/dev/null 2>&1 || true
  killall ScreenSaverEngine >/dev/null 2>&1 || true
fi

log "Done."
SH

chmod +x swap_aerial.sh
./swap_aerial.sh
```
