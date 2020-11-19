# Django資料庫刪除migrations保存之前資料

1.首先要先確保makemigrations沒有任何資料需要遷移。使用

```text
./manage.py makemigrations
>> No changes detected
```

2.使用顯示遷移資料庫檔案查看目前使用的資料遷移文件

```text
./manage.py showmigrations
>>admin
>>[X] 0001_initial
>>[X] 0002_logentry_remove_auto_add
>>auth
>> ..
>> .
```

3.製作虛擬空的資料庫給想要刪除model的app

```text
./manage.py migrate --fake "app_name" zero
```

4.再次使用檢索資料遷移文件查看文件的使用，可以看到有些\[x\] --&gt; \[ \]

```text
./manage.py showmigrations
>>admin
>>[X] 0001_initial
>>[X] 0002_logentry_remove_auto_add
>>auth
>> ..
>> .
>>payment
>>[ ] 0001_initial
>>[ ] 0002_xxxxx
>>xx
>>[ ] 0001_xxx
```

5.如果看到只想要刪除某個model的app，結果其他app也被製作虛擬資料庫。這時候不用慌張！因為有可能是因為資料庫的關係所以導致牽連。所以才會統一使用虛擬資料

