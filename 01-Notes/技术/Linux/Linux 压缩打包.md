---
date: "2026-05-28"
tags: [Linux, 命令, 基础]
---

# Linux 压缩打包

## tar（打包 + 压缩）

```bash
# 压缩
tar -czvf archive.tar.gz ./dir/     # gzip 压缩（最常用）
tar -cjvf archive.tar.bz2 ./dir/    # bzip2 压缩（更小但更慢）

# 解压
tar -xzvf archive.tar.gz            # 解压 gzip
tar -xjvf archive.tar.bz2           # 解压 bzip2
tar -xvf archive.tar                # 解压纯 tar

# 查看包内容（不解压）
tar -tzvf archive.tar.gz
```

记忆技巧：`-c` create / `-x` extract / `-z` gzip / `-j` bzip2 / `-v` verbose / `-f` file

## zip / unzip

```bash
zip -r output.zip ./dir/            # 压缩
unzip output.zip                     # 解压
unzip -l output.zip                  # 只列内容不解压
```

## gzip / gunzip

```bash
gzip file.txt                        # 压缩 → file.txt.gz（原文件被删除）
gzip -k file.txt                     # 压缩但保留原文件
gunzip file.txt.gz                   # 解压
```

## 速查

| 需求 | 命令 |
|------|------|
| 打包目录为 .tar.gz | `tar -czvf a.tar.gz ./dir/` |
| 解压 .tar.gz | `tar -xzvf a.tar.gz` |
| 打包目录为 .zip | `zip -r a.zip ./dir/` |
| 解压 .zip | `unzip a.zip` |
| 压缩单个文件 | `gzip file.txt` |

← [[Linux 网络命令]] | → [[Linux 进程与后台]]
