# Docker for symfony

Our Docker PHP project is a simple, yet powerful, Docker setup for PHP development. It is based on the official PHP Docker image and is designed to be used with Symfony.

Setup
------------

* Clone the submodule in the root of the project
  ```
  git clone --recurse-submodules -j8 <symfony-repo> app
  ```

* Composer install with docker
  ```
  docker run --rm --interactive --tty -v $(pwd)/app:/app composer install
  ```
  
* Put in your .env.local file 
  ```
    APP_PORT=8300
    MYSQL_PORT=3336
    MYSQL_PASSWORD=secret
    MYSQL_DATABASE=docker-php
    MYSQL_USER=user
    REDIS_PORT=6389
    BUILD_TARGET=app_dev
    DATABASE_URL="mysql://${MYSQL_USER}:${MYSQL_PASSWORD}@db:3306/${MYSQL_DATABASE}?serverVersion=8.0.34&charset=utf8mb4"
    ```
* For a standard build / setup, simply run
```docker compose up -d ```
* For a development build which exposes DB ports and includes Xdebug, you can run the dev-mode shell script like so
```sh ./bin/dev-mode.sh -d```
* For first time setup, run
  ```sh ./bin/dev-mode.sh -d --build```
* To run with Xdebug enabled, run 
```XDEBUG_MODE=debug sh ./bin/dev-mode.sh -d --build```


Branches
-------------

Each branch (except main, dev, and branches prefixed with 'feature') corresponds to an accompanying series lesson.   

Contributing
------------

Docker PHP is an Open Source project and contributions are welcome. The 'main' branch is read-only as this should not differ from the tutorials so please send pull requests to the develop branch.

[1]: https://github.com/GaryClarke/docker-php
[2]: https://youtu.be/qv-P_rPFw4c
