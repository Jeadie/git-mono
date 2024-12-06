# monogit
A tool for monorepo people in a multi-repo world

## Introduction
Suppose you love monorepos, but you join a company only to find they use three separate git repositories!

```console
mono@git:~$ monogit repo_a repo_b repo_c

mono@git:~$ git add repo_a/main.rs
mono@git:~$ git add repo_b/docs/src/index.md
mono@git:~$ git add repo_c/python/client.py
```


Just use regular git
```console
mono@git:~$ git commit -m "add new feature with docs and SDK change"
[repo_a main 456def7] add new feature with docs and SDK change
 1 file changed, 15 insertions(+)

[repo_b docs 012jkl3] add new feature with docs and SDK change
 1 file changed, 10 insertions(+), 2 deletions(-)

[repo_c sdk 678pqr6] add new feature with docs and SDK change
 1 file changed, 20 insertions(+)
```

Automaticate linking between repositories
```console
mono@git:~$ /usr/bin/git --git-dir repo_a/.git log
commit 456def7805b6eb5018c6a2528d2bfa85210b5ca3
Author: jeadie <jackeadie@duck.com>
Date:   Fri Dec 6 16:39:45 2024 +1000

    add new feature with docs and SDK change

    Related commits:
    - repo_b [docs branch]: 012jkl3
      🔗 https://github.com/jeadie/repo_b/commit/012jkl3
    - repo_c [sdk branch]: 678pqr6
      🔗 https://github.com/jeadie/repo_c/commit/678pqr6
```

And push to all repositories at once
```console
mono@git:~$ git push
Starting multi-repo push...
repo_a:
   ✔ Updated 123abc4 → 456def7 (1 object, 150 bytes)
   🔗 https://github.com/jeadie/repo_a.git

repo_b:
   ✔ Updated 789ghi1 → 012jkl3 (2 objects, 300 bytes)
   🔗 https://github.com/jeadie/repo_b.git

repo_c:
   ✔ Updated 345mno5 → 678pqr6 (3 objects, 450 bytes)
   🔗 https://github.com/jeadie/repo_c.git

✅ Push successful for (3/3) repositories!
```
