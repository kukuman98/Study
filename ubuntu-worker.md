# ubuntu worker

這是一個可以自訂時間對server機器定時做某些事情的功能，需要搭配自訂義command指令

1.只需要更改根目錄底下的/etc/crontab 就能對ubuntu進行排程。

2./etc/crontab

```text
# /etc/crontab: system-wide crontab                                                                                                                                                                     
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
* * * * * ubuntu /bin/bash -c "cd /home/ubuntu/projects/seth-api-stg.revtel2.com && source .env/bin/activate && ./manage.py queryexpired"
0 0 * * * ubuntu /bin/bash -c "cd /home/ubuntu/projects/seth-api-stg.revtel2.com && source .env/bin/activate && ./manage.py fetchproductview"  
#
```

3.可以自行在底下加入新的排程

4.[自訂義Django 管理指令](django/custom-django-manage.py-command.md)

### crontab 線上參考資源

[crontab 生成器](https://crontab-generator.org/)    [crontab 時間生成器](https://crontab.guru/)

