# Git password error

Using personal token

Github-&gt;setting-&gt;deploy setting -&gt;personal token

check your project git url

```bash
git config -l | grep url
```

Using remote set-url

```text
git remote set-url origin "https://username:token@github.com/path.git"
```

