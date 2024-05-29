# Global settings

```bash
git config --global fetch.prune true
git config --global core.excludesfile ~/.gitignore_global

# Automatically set upstream
# https://stackoverflow.com/questions/6089294/how-to-avoid-having-to-do-git-branch-set-upstream-and-instead-default-to-au
git config --global push.autoSetupRemote true
```