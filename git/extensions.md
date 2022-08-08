# Extensions

```bash
npm install --global git-recent
npm install --global git-open
npm install --global diff-so-fancy

git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"
git config --global interactive.diffFilter "diff-so-fancy --patch"
```