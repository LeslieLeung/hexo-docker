# hexo-docker

Deploying Hexo environment in Windows with Docker. (Managing nodejs versions with docker is a way more elegant way than using nvm-windows, lol)

## Usage

> Suppose you have a directory `/your/hexo/path` on Windows that created using native Windows nodejs, something that looks like the screetshot below. Some of the plugins is installed in this directory, so you should mount this whole directory into the container.

![](https://bucket.ameow.xyz/img/markdown/2022/2/19/202202191621374.png)

### Initializing container

```bash
docker run -d -v /your/hexo/path:/hexo -p 4000:4000 --name hexo-docker leslieleung/hexo-docker:latest
```

### Getting into the container

```bash
docker exec -it hexo-docker /bin/sh
```

Then you can do whatever you need with hexo, like `hexo s` or `hexo g -d`.

### (Recommended) Install `hexo-admin`

> Use [hexo-admin](https://github.com/jaredly/hexo-admin) to manage posts and pages.

```bash
# RUN INSIDE THE CONTAINER
npm install --save hexo-admin
```

This should save whatever it need for hexo-admin in your mounted dirctory, so you only have to run this once.

### Accessing hexo-admin from host machine

`http://localhost:4000` should do the job.