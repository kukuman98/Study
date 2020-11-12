# Custom Django  manage.py Command

1.首先認識Django的manage.py指令集，可以使用一下指令觀察目前已有的指令集與分類

```text
python3 manage.py help
```

2.可以看出每一個api底下都會有某些特別的指令，所以需要用某些指令控制那個api時，就必須把該指令歸類於該api底下。

3.創建新的自訂義指令很簡單，只需要在該api目錄底下創建必要文件架構

```text
api/
    management/
        commands/
            "your command name".py
```

4.以及將該api已放入**settings.py的INSTALL\_APPS**內

5.你的指令.py文件架構需要如下

```text
from django.core.management.base import BaseCommand, CommandError

class Command(BaseCommand):
    help = 'your command help message'

    def add_arguments(self, parser):
        parser.add_argument('command_item', nargs='+', type=int/str/...)

    def handle(self, *args, **kwargs):
        try:
            # kwargs['command_item'][0] 是一個list[],可以取得在指令後面拿到的可能是str或者int
            # do something ...
        except Exception as e:
            raise CommandError(e)

        self.stdout.write(self.style.SUCCESS('your command success message'))
```

6.其中add\_arguments function是可/不可加入，作用是取得指令後面的功能或者文件，比如

```text
python3 manage.py "your command name".py -h/file path/... -h/file path/.... 
```

### 線上資源參考

[Django documentation](https://docs.djangoproject.com/en/3.1/howto/custom-management-commands/) 

