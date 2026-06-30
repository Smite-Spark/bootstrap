# Smite Spark — Bootstrap

Contains the current license server URL. The launcher fetches `bootstrap.txt`
from this repo on startup to know where the server is.

## To move the server

1. Edit `bootstrap.txt` with the new URL
2. Commit + push to main
3. All launchers pick up the new URL on next launch

## Format

Single line, no trailing content:
```
http://your-server:3000
```
