#### Steps to fixing git object error


show the empty/corrupt object file
```
git status
```

remove it
```
rm .git/objects/08/3834cb34d155e67a8930604d57d3d302d7ec12
```

I got fatal: bad object HEAD message
```
git status
```

I remove the index for the reset
```
rm .git/index
```

fatal: Could not parse object 'HEAD'.
```
git reset
```

just to check whats happening
```
git status
git pull
```

prints the last 2 lines tail -n 2 of log branch to show my last 2 commit hash
```
tail -n 2 .git/logs/refs/heads/MY-CURRENT-BRANCH-NAME
```

I pick the last commit hash
```
git update-ref HEAD 7221fa02cb627470db163826da4265609aba47b2
```

shows all my file as deleted because i removed the .git/index file
```
git status
```

continue to the reset
```
git reset
```

verify my fix
```
git status
```
