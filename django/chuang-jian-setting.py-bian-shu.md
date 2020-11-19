# 創建setting.py 變數

1.在setting.py創建變數

```text
BUNDLE_ID = "<%= BUNDLE_ID %>"
```

2.在data.js帶入 npm run config執行參數

```text
common:{
...
...
...
..
BUNDLE_ID:"xxxxxxxx",

}

stg:{
.
.
.
BUNDLE_ID:"xxxxxxxa",
}

prod:{
.
.
.
.
}
```

這樣的話，npm run config:prod會拿到common的BUNDLE_ID，反之stg會拿到自己的BUNDLE \__ID。

