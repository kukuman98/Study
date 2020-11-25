# 更新Package

1.首先在更新前需要有wheel，安裝：

```text
pip install wheel
```

2.檢查\_\__init\_\_.py_ 是否更新版號碼

3.然後查看setup.py的變數

4.使用setup.py來將這個package推上去pypi，sdist是讓它不會build整個上傳

```text
python setup.py sdist bdist_wheel
```

5.然後要publish上去檔案，檔案會在dist內

```text
twine upload dist/revpayment-2.4.4*
```

6.輸入pypi帳號與密碼就可以上傳了～～結束。

