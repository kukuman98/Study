# ssh config

可以記住ssh連結的功能

1.首先需要修改~/.ssh/config的文件

```text
Host aws-dev
HostName ec2-52-196-29-78.ap-northeast-1.compute.amazonaws.com
IdentityFile ~/.ssh/aws-dev.pem
User ubuntu
```

2.Host是之後連結的host

3.HostName是想要連結server的instance

4.IdentityFile 是該instance的private\_key路徑，一般都在.ssh底下

5.User是該instance登入的user，一般都是ubuntu

6.使用

```text
ssh aws-dev
```

