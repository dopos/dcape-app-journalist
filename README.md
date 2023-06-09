# dcape-app-journalist

[![GitHub Release][1]][2] [![GitHub code size in bytes][3]]() [![GitHub license][4]][5]

[1]: https://img.shields.io/github/release/dopos/dcape-app-journalist.svg
[2]: https://github.com/dopos/dcape-app-journalist/releases
[3]: https://img.shields.io/github/languages/code-size/dopos/dcape-app-journalist.svg
[4]: https://img.shields.io/github/license/dopos/dcape-app-journalist.svg
[5]: LICENSE

[journalist](https://github.com/mrusme/journalist) application package for [dcape](https://github.com/dopos/dcape).

## Docker image used

* [mrusme/journalist](https://hub.docker.com/r/mrusme/journalist)

## Addons

Instead using [Redacteur](https://github.com/mrusme/journalist#redacteur), you may use make:

Add user:
```
$ make user-add USER=johndoe PASS=MySecretPassword123
{"success":true,"user":{"id":"...","username":"johndoe","role":"user"},"message":""}
```
Add token:
```
$ make token-add USER=johndoe PASS=MySecretPassword123 TOKEN_NAME=mobile
{"success":true,"token":{"id":"...","type":"qat","tokenname":"mobile","token":"..."},"message":""}
```
Add feed:
```
$ make feed-add USER=johndoe PASS=MySecretPassword123 FEED_NAME=habr-best FEED_GROUP=IT FEED_URL=https://habrahabr.ru/rss/best/
{"success":true,"feed":{"id":"...","name":"habr-best","url":"https://habrahabr.ru/rss/best/","group":"IT"},"message":""}
```

## Requirements

* linux 64bit (git, make, sed)
* [docker](http://docker.io)
* [dcape](https://github.com/dopos/dcape) v2
* Git service ([github](https://github.com), [gitea](https://gitea.io) or [gogs](https://gogs.io))

## Install

### By mouse (deploy with drone)

* Gitea: Fork or mirror this repo in your Git service
* Drone: Activate repo
* Gitea: "Test delivery", config sample will be saved to enfist
* Enfist: Edit config and remove .sample from name
* Gitea: "Test delivery" again (or Drone: "Restart") - app will be installed and started on webhook host

### By hands

```bash
git clone --single-branch --depth 1 https://github.com/dopos/dcape-app-journalist.git
cd dcape-app-journalist
make config
... <edit .env.sample>
mv .env.sample .env
make up
```

## License

The MIT License (MIT), see [LICENSE](LICENSE).

Copyright (c) 2023 Aleksei Kovrizhkin <lekovr+dopos@gmail.com>
