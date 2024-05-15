# Decrease spacing between macos menu bar

```bash
defaults -currentHost write -globalDomain NSStatusItemSpacing -int 2
ps -A | grep Core | awk '{ print $1 }' | xargs kill -9 # so you don't have to sign out
```