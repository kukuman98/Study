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

3.使想要調整的資料庫回到零的migrations history

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

5.如果看到只想要刪除某個model的app，結果其他app也被製作虛擬資料庫。這時候不用慌張！因為有可能是因為資料庫的關係所以導致牽連。所以才會統一使用虛擬資料。

6.這時候需要刪除所有\[ \]的資料文件為了重新創建全新的資料遷移文件。

7.刪除完畢後，接下來需要刪除該model，或者將remote上更改好後的app更新也可以，總之就是更改自己想要有哪些model的存在。

8.更改完畢後接下來需要創建遷移文件使用

```text
./manage.py makemigrations
```

9.製作完後，再生成新的0001\_\_initial。

```text
./manage.py migrate --fake-initial
```

10.再次使用檢索遷移資料庫文件就可以看到

```text
./manage.py showmigrations
>>>>admin
>>[X] 0001_initial
>>[X] 0002_logentry_remove_auto_add
>>auth
>> ..
>> .
>>payment
>>[X] 0001_initial
>>xx
>>[X] 0001_initial
```

11.表示你已經成功刪除model了！再開啟你的server到admin site去查看資料，都還保留著原本的資料。





