# Tmux Command

## Command

### New session

```bash
tmux new -s 'name'
```

### Kill session

```bash
tmux kill-session -t 'name'
```

### Attach session

```bash
tmux a -t 'name'
```

## Quick Reference

* ctrl + b,d -- 斷連session
* ctrl + b,n -- 切換bash
* ctrl + b,c -- 創建bash
* ctrl + b,, -- 命名bash
* ctrl + b,& -- 關閉bash
* ctrl + b,% -- 垂直切割視窗
* ctrl + b," -- 水平切割視窗
* ctrl + b,o -- 切換視窗
* ctrl + b,x -- 關閉當前視窗
* ctrl + b,\[ -- 使用滾輪

