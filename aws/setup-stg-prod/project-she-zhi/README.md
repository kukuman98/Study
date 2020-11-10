# project 設置

1.利用.pem private key登入。可以利用AWS ec2 instance選取connect查看

```text
ssh -i "your key" ubuntu@"Public IPv4 DNS"
```

2.去到project file底下clone新的專案

```text
git clone https://xxxxxx.com
```

3.創建虛擬環境並且啓動

```text
python3 -m venv .env
source .env/bin/active
```

4.安裝專案需求

```text
pip install -r requirements.txt
```

5.安裝npm，並且渲染一次setting.py

```text
npm install
npm run config:stg/prod/your custom
```

6.model建立

```text
./manage.py makemigrations
./manage.py migrate
```

7.確認DNS對接網域，修改 scripts/data.js檔案

```text
common:{
    .
    .
    .
    stg:{
        ENV:'stg',
        API_HOST:'https://greenjump-api.revtel2.com',    # BE stg DNS
        WEB_HOST:'https://greenjump.revtel2.com',    # FE stg DNS
        DOMAIN:''
    },
    prod:{
        ENV:'prod',
        API_HOST:'https://api.greenjump.app',    # BE prod DNS
        WEB_HOST:'https://www.greenjump.app',    # FE prod DNS
        DOMAIN:''
    }
}
```

7.[stg 執行](stg-setup.md)

8.[prod 執行](prod-setup.md)

