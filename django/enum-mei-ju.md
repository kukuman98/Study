# Enum 枚舉

Enum 是集的列舉，是列出某些有窮序列集的所有成員的程式。列舉是一個被命名的整型常數的集合，列舉在日常生活中很常見，例如表示星期的SUNDAY、MONDAY、TUESDAY、WEDNESDAY、THURSDAY、FRIDAY、SATURDAY就是一個列舉。

```text
from enum import Enum

class A:
    a = 'aa'
    command = 'This is class A'

A.a
>> 'aa'
A['a']
>> 'aa'
A.a = 'bb'
>> AttributeError: Cannot reassign members.
```



