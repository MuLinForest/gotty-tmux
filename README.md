# gotty-tmux

GoTTY + tmux Docker image — Web terminal with session persistence.

Based on [sorenisanerd/gotty](https://github.com/sorenisanerd/gotty) with `tmux` installed on top.

## Usage

```bash
# Default: bash shell with random URL
docker run -d --rm -p 8080:8080 mulin/gotty-tmux

# With tmux session persistence and password auth
docker run -d --rm -p 8080:8080 \
  mulin/gotty-tmux \
  gotty -w -c admin:secret tmux new -A -s main
```

Open http://localhost:8080 in your browser.

## Why tmux?

GoTTY without tmux starts a new process per connection. Close the browser tab — the process dies. With tmux:

- **Persistence**: disconnect and reconnect without losing your session
- **Sharing**: multiple people can view the same terminal
- **Long-running tasks**: `docker build`, file transfers, etc. survive browser closure

## Build locally

```bash
docker build -t mulin/gotty-tmux .
```

## License

MIT
