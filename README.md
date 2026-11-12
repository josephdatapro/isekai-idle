# Isekai Idle Clicker — update home (publish-ready, NOT yet published)

This folder is the complete update shelf for the game, staged locally on
Nov 12, 2026. Publishing was blocked by a GitHub sign-in wall (see below);
the moment GitHub access exists, publishing is one push.

## What goes where

Publish the contents of this folder (except this README) to either:

- **Option A (preferred):** a new public repo `josephdatapro/isekai-idle`
  with GitHub Pages enabled on the `main` branch, root folder, or
- **Option B:** an `isekai-idle/` folder inside the existing
  `josephdatapro/josephdatapro.github.io` repo.

Both produce the same live addresses:

- `https://josephdatapro.github.io/isekai-idle/version.json` ← the game's
  UPDATE_URL (baked into the NEXT build; the shipped v4 still points at a
  placeholder and can never check successfully)
- `https://josephdatapro.github.io/isekai-idle/Isekai-Idle-Clicker-v4.apk`
- `https://josephdatapro.github.io/isekai-idle/` (landing page)

## Contents

- `version.json` — `{ "version": "4.0.0", "notes": "…" }`. The shipped
  client reads ONLY `version` (numeric dotted compare against its own
  VERSION); `notes` is informational. To ship a future update: raise
  `version` above the installed build's VERSION, and put the new APK
  beside it.
- `Isekai-Idle-Clicker-v4.apk` — the shipped v4 build, 12,590,251 bytes,
  md5 `3351820281740103d4b8d40d7e1bb2cf`, sha256
  `39935325031cbffcc679f3fa5caa095fa9f656ca8ab8ad429534b75a87c35a39`.
- `index.html` — small landing/download page.

## Honest limits of the shipped client (v4 code, game.js)

The update system is a *notifier*, not a downloader: on open (and on
button tap) the game fetches version.json; if a newer version exists it
shows a banner and the button becomes "UPDATE TO vX". Tapping it only
shows a toast and reloads the game page — the client has NO code to
download or install an APK, and the Android shell has no download
handling. So the button tells the player an update exists; the actual
install still happens by opening the APK link (above) in a browser.
A future client revision could add an `apk` field to version.json and
open it — that is a game-code change for a future build, not hosting.

## Publish commands (after GitHub sign-in exists)

```sh
cd ~/workspace/games/i-died-isekai-idle/update-home
git push origin main   # remote already points at josephdatapro/isekai-idle
# then enable Pages: repo Settings → Pages → main / root
# (or via API: POST /repos/josephdatapro/isekai-idle/pages {"source":{"branch":"main","path":"/"}})
```

## The gate that blocked publishing (Nov 12, 2026)

Every route needs Joseph's GitHub sign-in, which does not exist on this
machine: `gh` not logged in; GH_TOKEN/GITHUB_TOKEN empty; the
~/.ssh/id_ed25519 key is not registered on the account (Permission
denied); the GitHub connector reports `not_connected` (OAuth tap is
Joseph's). No workarounds were attempted.
