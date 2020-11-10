# stg setup

1.先檢查出口使用

```text
netstat -ntlp
```

2.然後使用django的runserver指令建立新的出口

```text
./manage.py runserver 0.0.0.0:80xx
```

3.回到[project設置](./)

