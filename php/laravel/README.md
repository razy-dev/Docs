# Laravel
## Install
* https://laravel.kr/docs/5.7/installation

---
## Create Project
```console
> composer create-project --prefer-dist laravel/laravel [YOUR_PROJECT_FOLDER]
```
[@see Composer](../composer.md)

---
## Laravel Layout

---
## Deploy Project
### 0. httpd config
* create service (add user)
  ```
  ]# adduser -d /data/www/SERVICE_NAME SERVICE_OWNER
  ]# passwd SERVICE_OWNER
  ******
  ```

### 1. Upload
 * upload
 * change directory permission
  ```
  ]$ su - SERVICE_OWNER
  ]$ cd ~
  ]$ chmod 755 .

  ]$ cd ~/SERVICE_HOME
  ]$ chmod 777 -R ./storage
  ```

### 2. Update Package
  ```
  ]$ su - SERVICE_OWNER
  ]$ composer install
  ```

### 3. Migration
* Create .env File
  ```
  ]$ su - SERVICE_OWNER
  ]$ cd ~/SERVICE_HOME
  ]$ vi .env
  ...
  ```

### 4. Build Assets
