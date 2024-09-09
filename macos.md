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