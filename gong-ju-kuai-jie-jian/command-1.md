# Vi Command

## Command

### Open vi

```bash
vi 'name'
```

## Quick Reference

* : -- 啓動編輯模式
* i -- 啓動插入模式
* esc -- 退出插入模式

## Edit Mode

* wq -- 儲存與退出
* w! -- 強制儲存
* q! -- 強制退出
* e! -- 還原

## Generate Mode

* d\(number\)d -- 刪除一行，並且儲存在剪貼板
* p -- 將剪貼板放入該行
* x -- 刪除一個字元
* y\(number\)y -- 拷貝當前行
* u -- undo
* ctrl + r -- redo
* vsp -- 垂直切割開啓其他文件
* sp -- 水平切割開啓其他文件
* ctrl + w + w -- 跳轉其他文件

