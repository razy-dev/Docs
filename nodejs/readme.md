# NodeJs
## Install
```
curl -sL https://rpm.nodesource.com/setup_11.x | sudo bash -
yum install nodejs


npm install pm2 -g

cd ~/uix.clesson.net
vi ecosystem.config.js
module.exports = {
  apps : [{
    name      : 'uix.clesson.net',
    script    : 'npm',
    args      : 'start',
    env: {
      NODE_ENV: 'development'
    },
    env_production : {
      NODE_ENV: 'production'
    }
  }],
};
pm2 start ecosystem.config.js
```

## Upgrade NodeJs & npm
---
### Unix/Linux
```console
]$ node -v
v8.11.4

]$ sudo npm cache clean -f
]$ sudo npm install -g n

]$ node -v

```

```console
]$ npm -v
5.6.0

]$ sudo npm install -g npm

]$ npm -v
```

### Windows
```console
> Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force
> npm install -g npm-windows-upgrade
> npm-windows-upgrade
```
