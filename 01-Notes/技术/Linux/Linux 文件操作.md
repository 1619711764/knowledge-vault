---
date: "2026-05-28"
tags: [Linux, 文件操作, 命令]
---

# Linux 文件操作

## 查看文件和目录

```bash
ls          # 列出当前目录
ls -la      # 详细列表（含隐藏文件）
ls -lh      # 人类可读的文件大小
pwd         # 显示当前路径

tree        # 树形显示目录结构（需安装）
```

## 目录导航

```bash
cd /path/to/dir      # 进入目录
cd ..                # 上级目录
cd ~                 # 回到 home 目录
cd -                 # 回到上一个目录
```

## 文件操作

```bash
touch file.txt       # 创建空文件（或更新修改时间）
mkdir dir            # 创建目录
mkdir -p a/b/c       # 递归创建嵌套目录

cp source dest       # 复制文件
cp -r src/ dest/     # 递归复制目录

mv old.txt new.txt   # 移动/重命名

rm file.txt          # 删除文件
rm -rf dir/          # 递归强制删除目录（危险！）
```

## 查看文件内容

```bash
cat file.txt         # 一次显示全部
less file.txt        # 分页查看（q 退出，/ 搜索）
head -n 10 file.txt  # 前 10 行
tail -f log.txt      # 实时跟踪日志尾部
```

## 查找

```bash
find . -name "*.py"           # 按文件名查找
find . -type d -name "src"    # 查找目录
find . -mtime -1              # 最近 1 天修改的文件

locate filename               # 更快的查找（需 updatedb）
```

← [[Linux 常用命令]] | → [[Linux 文本处理]]
