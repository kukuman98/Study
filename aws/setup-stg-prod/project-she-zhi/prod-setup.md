# prod setup

1.需要在機器的home目錄（～）下載公司的快捷鍵

```text
git clone https://github.com/revtel/revtools
```

2. 更改~/.bashrc，在最後一行加上

```text
export PATH=~/revtools/:${PATH}
```

3.去到專案底下

```text
cd "path by your project"
```

4.確認scripts/data.js的model file 路徑

```text
module.exports= {
    .
    .
    .
    ,
    {
      filename: "server-config.template.cfg",
      path: "./",
      destname: "server-config.cfg"
    },
    .
}
```

5.再跑一次

```text
npm run config:prod
```

6.更改docker-start.sh權限

```text
chmod +x docker-start.sh 
```

7.使用公司快捷鍵建立uwsgi

```text
rev-aws-backend-pull.sh 
```

8.輸入4 選擇restart server

9.檢查是否已經啟動uwsgi

```text
netstat -ntlp
```

10.回到[project 設置](./)

