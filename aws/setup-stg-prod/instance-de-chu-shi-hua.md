# instance 的初始化

1.利用.pem private key登入。

```text
ssh -i "your key" ubuntu@"Public IPv4 DNS"
```

2.安裝某些套件以及更新

```text
sudo apt update && sudo apt upgrade -y && sudo apt install -y build-essential libpcre3 libpcre3-dev exuberant-ctags python3-venv python3.8-dev
```

3.下載node.js

```text
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash - && sudo apt install -y nodejs
```

4.安裝npm

```text
npm install
```

5.創建project file，之後的project都儲存在這

```text
mkdir project
```

