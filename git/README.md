# Git
## git init
```console
]$ git init
]$ git remote add origin https://github.com/lazylogic/www.lazylogic.net.git
]$ git add ...
]$ git commit -m "Initialize"
]$ git push
```

```console
]$ vi .git/config
...
[branch "master"]
    remote = origin
    merge = refs/heads/master
```