# homelab

Some services to run on local home server

Common variables that are expected at `.env` file:

```env
PUID=1000
PGID=1000
TZ=Etc/UTC
```

## Plex

Expected variables at `.env` file:
- `PLEX_CLAIM` - token from https://www.plex.tv/claim/ to add the server to your account
- `PLEX_MOVIES_PATH` - path to folders which contains movies that will be shown as available to you
