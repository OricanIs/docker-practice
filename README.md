## docker执行


### postgres数据库容器的搭建

#### *创建并启动容器* 

启动容器

```js
docker run --name db -d postgres -P -v ~/project/docker/postgres/:/var/share/ postgres
```
`(可添加参数 -e POSTGRES_PASSWORD=password123)`

连接容器

```js
docker exec -it db /bin/bash

```

容器内执行恢复数据库操作

```js
gunzip -c bookcloud.gz | psql -U postgres

```

### golang + etcd 容器的搭建 etcd主要是golang微服务的发现

可参考当前包下dockerfile/etcd/Dockerfile 文件

#### *创建容器容器*
 
根据Dockerfile创建镜像

```js
	cd dockerfile/etcd/
	docker build  -t golang:orican .
```

创建容器

```js
	
	docker run -v ~/go/src/:/go/src/ -p 8848:8848 -p 8858:8858 -p 8870:8870 -dit --link db:postgres --name app orican bash
```