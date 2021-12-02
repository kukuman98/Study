# setup MongoDB

首先先安裝docker 的 mongo

```docker
docker pull mongo
```

然後可以看到這個mongo image 的 detail

```
docker image inspect mongo
```

能夠看到 _ContainerConfig.ExposedPorts_ 出口為27017

接下來建立mongo

```
docker run \
-v ~/docker_file/mongo.conf:/etc/mongo.conf \
-v ~/docker_file/db:/data/db \
-d  --name mongodb  -p 27888:27017 \
-e MONGO_INITDB_ROOT_USERNAME=mongo-admin \
-e MONGO_INITDB_ROOT_PASSWORD=mongo-test mongo
```

* docker run： 執行docker 指令
* \-v：volume 將資料紀錄在local 資料夾
* path:path： 指定建立的local 路徑存到對應的docker 路徑
* \-d：將docker 啟動在 background
* \--name： 建立docker 名字
* \-p 27888:27017：聲明本地27888端口映射到內部27017端口
* \-e：設置環境變數
* mongo： 要執行的image&#x20;

local 的 db 連結會變成

```
mongodb://<username>:<password>@<host>:<port>/?authSource=admin
```

這邊設置的話會是

```
mongodb://admin:aaron98@localhost:27888/?authSource=admin
```

然後將url 貼上 mongodb compass 就可以連結db了

[參考網址](https://www.code4it.dev/blog/run-mongodb-on-docker)
