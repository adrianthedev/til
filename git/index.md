## Search for a string in previous commits

```bash
git rev-list --all | (
    while read revision; do
        git grep -F '"t->"' $revision
    done
)
```