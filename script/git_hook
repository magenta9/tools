# git hook配置方式

git hook是适用于git使用时的自动化工具，可以帮助解决很多自动化的问题。
这里简单记录一下git hook的配置方式。

### 背景
git hook是git的一个功能，可以在git的各个阶段执行一些脚本，相关文件配置在.git/hooks目录下。
当前支持hook的场景如下：
```
➜   ls ./.git/hooks
applypatch-msg.sample     fsmonitor-watchman.sample pre-applypatch.sample     pre-commit.sample         pre-push.sample           pre-receive.sample        push-to-checkout.sample
commit-msg.sample         post-update.sample        pre-commit.sample         pre-merge-commit.sample   pre-rebase.sample         prepare-commit-msg.sample update.sample
```


### 配置方式
通常情况下每个项目单独配置成本较高，所以通过`git-template`来让配置对所有项目生效。
1. 在根目录下创建.git/hooks目录
    1. `git config --global init.templatedir '~/.git-templates'`
    2. `mkdir -p ~/.git-templates/hooks`
2. 在.git/hooks目录下创建pre-commit文件，写入脚本内容
```
➜   cat ~/.git-templates/hooks/pre-commit
#!/bin/sh

# format go code
goimports -w .
# update go mod
if [ -e go.mod ]
then
    go mod tidy
fi
```

3. 提供执行权限：`chmod +x ~/.git-templates/hooks/pre-commit`
4. 针对需要使用的项目重新初始化git：`git init`


