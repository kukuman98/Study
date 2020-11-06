# 自定義css

1. 自定義css的時候必須使用override的方式覆蓋css文件。
2. 必須要參考static/admin的文件架構來創建在api/admin底下
3. 然後在templates/admin的html更改套用的文件路徑

```text
<link rel="stylesheet" type="text/css" href="{% block stylesheet %}{% static "admin/css/<your css path>" %}{% endblock %}">
```

