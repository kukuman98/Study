# Django css 問題

1. override方式改寫css檔案在stg沒有問題
2. 在prod，只會對到project/static/admin/css/的路徑
3. stg，可以對到project/api/static/admin/css/的路徑
4. 然後一般網頁會cache css或js檔案，所以需要開無痕或者清除cache就可以看到更改後的結果。
5. 清除cache，google設定，清除遊覽資料，選擇快取圖片和檔案，按下清除資料





### 老大補充，

1.因為uwsgi跑的是staticfile，所以只會抓到app/static底下的資料，這個時候我們就需要一個酷東西

```text
./manage.py collectstatic
```

2.他可以收集所有api底下的static資料存進app底下的static file內。

