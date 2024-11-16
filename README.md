# homelab

Some services to run on local home server

Common variables that are expected at `.env` file:

```env
PUID=1000
PGID=1000
TZ=Etc/UTC
DOWNLOADS_PATH=/home/${USER}/Downloads
```

## Plex

Expected variables at `.env` file:
- `PLEX_CLAIM` - token from https://www.plex.tv/claim/ to add the server to your account

> [!warning]
> - By default Plex will be looking for files at `DOWNLOADS_PATH`
> - All movies and TV series should be in different folders e.g. `${DOWNLOADS}/movies` and `${DOWNLOADS}/tv_series`
