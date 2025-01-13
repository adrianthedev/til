# Decrease spacing between macos menu bar

```bash
defaults -currentHost write -globalDomain NSStatusItemSpacing -int 2

# so you don't have to sign out
# but might have side-effects
ps -A | grep Core | awk '{ print $1 }' | xargs kill -9
```

# Print all the ports that are in use

```bash
sudo lsof -iTCP -sTCP:LISTEN -n -P | awk 'NR>1 {print $9, $1, $2}' | sed 's/.*://' | while read port process pid; do echo "Port $port: $(ps -p $pid -o command= | sed 's/^-//') (PID: $pid)"; done | sort -n
```

# SVG to PNG

From: https://discussions.apple.com/thread/255717253?sortBy=rank

```bash
sips -s format png -o logo_maybe.png -z 327 2000 logo_maybe.svg
```

# Use ffmpeg to convert files to webm

```bash
ffmpeg -i input-file.mp4 -c:v libvpx -crf 10 -b:v 1M -c:a libvorbis output-file.webm
```
