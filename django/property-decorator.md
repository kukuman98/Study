# @property——decorator

### property是class的裝飾器，一般只有讀取的屬性。若要更改資料需要使用setter、deleter。

* 範例

```text
class Bank_acount:
    def __init__(self):
        self._password = ‘預設密碼 0000’

    @property
    def password(self):
        return self._password

    @password.setter
    def password(self, value):
        self._password = value

    @password.deleter
    def password(self):
        del self._password
        print('del complite')
```

* getter

```text
andy = Bank_acount()
print(andy.password)
>>> 預設密碼 0000
```

* setter

```text
andy.password = '1234'
print(andy.password)
>>> 1234
```

* deleter

```text
del andy.password
print(andy.password)
>>> del complite
```

## @property是要實現物件導向中設計中封裝的實現方式

不理解什麼是封裝以及物件導向還有哪些觀念可以看 [python教學——物件導向](https://www.maxlist.xyz/2019/12/12/python-oop/)

