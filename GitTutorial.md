# Git Install and Config

## 配置全局变量

* `git config --global user.name "username"` 

* `git config --global user.email "useremail"`

* `git config --global credential.helper store`

## 创建新的代码仓库

```
git init
touch README.md
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/username/respname.git
git push -u origin master
```

## 提交新的更改

1. 点击 + 号，将所有文件提交暂存区

2. 打开菜单，提交已暂存的 (Commit Staged)

3. 在消息框中添加提交说明，然后 `Ctrl + enter` 提交

4. 点击 `Push` 将代码推送到云端