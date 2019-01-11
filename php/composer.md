# Composer

## in Windows
### Install
### Config
* Set COMPOSER_HOME
	1. Open Command prompt window, and run ```composer -vvv```
		- See ```Failed to initialize global composer: Composer could not find the config file: C:\Users\razy\AppData\Roaming\Composer\composer.json```
	1. In Search, search for and then select: System (Control Panel)
	2. Click the **Advanced system settings** link.
	3. Click **Environment Variables**. In the section **System Variables**.
		- find the **COMPOSER_HOME** environment variable and select it. Click **Edit**.
		- If the **COMPOSER_HOME** environment variable does not exist, click **New**.
	4. In the Edit System Variable (or New System Variable) window, specify the value of the **COMPOSER_HOME** environment variable.
		- eg> ```D:\02.WorkEnv\0.XAMPP\composer```
		- Click OK. Close all remaining windows by clicking OK.
	5. Create
	5. Reopen Command prompt window, and run ```composer -vvv```.
		- See ```Failed to initialize global composer: Composer could not find the config file: D:\02.WorkEnv\0.XAMPP\composer\composer.json```

---
## in Linux
### Install
```
]# mkdir /usr/share/composer
]# curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/share
]# ln -s /usr/share/composer.phar /usr/local/bin/composer
```

### Config

