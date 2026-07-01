# Smite Spark — Bootstrap

Public distribution hub for Smite Spark. Contains manifests and release
binaries that the launcher and server read without authentication.

## Files

| File | Read by | Purpose |
|------|---------|---------|
| `bootstrap.txt` | Launcher | Current license server URL |
| `launcher-update.json` | Launcher (auto-updater) | Latest launcher version + download URL + signature |
| `dll-update.json` | Server (dll-sync) | Latest DLL version + download URL |

## Releases

| Tag pattern | Content |
|-------------|---------|
| `v*` (e.g. `v0.1.0`) | Launcher installer (`*-setup.exe`) |
| `dll-v*` (e.g. `dll-v0.14.0`) | DLL (`spark.dll`) |

## To move the server

1. Edit `bootstrap.txt` with the new URL
2. Commit + push to main
3. All launchers pick up the new URL on next launch

## To release a new DLL

```bash
cd smite-spark
git tag -a v0.14.0 -m "v0.14.0: description"
git push origin v0.14.0
```

The CI builds `spark.dll`, uploads it here as `dll-v0.14.0`, and updates
`dll-update.json`. The server picks it up automatically within 5 minutes.

## To release a new launcher

```bash
cd smite-spark-launcher
git tag -a v0.2.0 -m "v0.2.0: description"
git push origin v0.2.0
```

The CI builds the launcher, uploads it here as `v0.2.0`, and updates
`launcher-update.json`. Launchers auto-update on next startup.

## bootstrap.txt format

Single line, no trailing content:
```
http://your-server:3000
```
