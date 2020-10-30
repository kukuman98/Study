# django model反向查詢

### 1. 使用Django默認外來鍵的屬性

```text
# Django默认每个主表对象都有一个外键的属性
# 可以通过它来查询所有属于主表的子表信息
# 查询方式：主表.子表_set()
# 返回值为一个queryset对象
Model.SubModel_set().all()
```

### 2.  通过在外键中设置related\_name属性值既可

```text
from django.db import models

class TestModel(models.Model):
    name = models.CharField(max_length=64)
    field = models.CharField(max_length=64)

class TestSubModel(models.Model):
    owner = models.Foreignkey(Person, related_name='test-related')
    name = models.CharField(max_length=64)
    price = models.FloatField()
    
# Using

TestModel.test-related.all()
```



