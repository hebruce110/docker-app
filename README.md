# docker-app

1. 进入到Dockerfile所在目录

2. 执行编译命令: `docker build -t repository_name:tag_name .`，例如编译php:pp5.6-fpm

```
docker build -t heyuan110/php:pp5.6-fpm .
```

注意最后的.符号

3. 如果要推送到dockerhub, 执行`docker push repository_name:tag_name`命令. 注意需要先在dockerhub创建repository，或者用下面的命令(docker tag)

```
docker tag local-image:tagname new-repo:tagname
docker push new-repo:tagname
```

docker hub 地址: <https://hub.docker.com/u/heyuan110>