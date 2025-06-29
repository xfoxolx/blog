---
title: Git の Usage
published: 2024-06-29
description: "Git用法"
tags: ["Tool","git"]
category: Tool
draft: false
---

## Git Usage

### Git Initialization
- Git installation

```sh title="ubuntu"
sudo apt update
sudo apt install git
git --version
```
---
```ps title="Windows"
winget install --id Git.Git -e --source winget
// upgrade git
winget upgrade --id Git.Git
git --version
```
---
```sh title="Arch"
sudo pacman -Syu
sudo pacman -S git
git --version
```

- Configure Git
```sh
git config --global user.name "Your name"
git config --global user.email "Your email"
git config --list
```

- Generate SSH keys
```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
cat ~/.ssh/id_rsa.pub
```

- Testing the SSH connection
```ps
ssh -T git@github.com
```

### Git Command

```sh title="基本命令"
mkdir workfolder & cd workfolder
git init
# 初始化项目目录为git仓库，将创建.git目录存储版本历史
git add file
# 将文件添加到暂存区
git add .
# 将所有文件添加到暂存区
git commmit -m "Submit information"
# 将暂存区中的更改提交到本地仓库
git commit -a -m "Submit information"
# 自动暂存已跟踪文件的更改并提交
git remote add origin git@github.com:user/repo.git
# 添加远程仓库
git push origin main
# 推送本地分支到远程
git push -u origin main
# 指定要推送到的上游分支
```
---
```sh title="查看操作"
git status
# 显示工作区和暂存区的状态（如修改、未跟踪文件）。
git log
# 查看提交日志
git log --graph --oneline --all
# 显示图形化分支
git log -- file.txt
# 查看特定文件历史
git diff
# 查看工作区与暂存区的差异
git diff --staged
# 查看暂存区与最后提交的差异
```
---
```sh
git restore .
# 撤销工作区所有文件的更改恢复到最后一次提交（HEAD）的状态。
# 仅影响工作区未暂存的更改会被丢弃。
git clean -fd
# 当工作区还有未跟踪的新文件或目录时额外清理
# 会永久丢弃工作区的更改（未提交的修改和未跟踪文件）
```
:::warning  
以上操作会永久丢弃工作区的更改建议先使用`git stash`临时保存，
使用`git stash pop`恢复。  
:::
```sh title="三种撤销操作"
git restore file.txt
# 撤销工作区更改
git restore --staged file.txt
# 撤销暂存
git reset --soft HEAD^1
# 撤销上次提交
```
---
```sh title="分支管理"
git branch feature-branch
# 创建分支
git checkout feature-branch
# 切换到分支
git switch -c feature-branch
# 创建并切换
git branch
# 列出所有分支
git checkout main
git merge feature-branch
# 合并分支首先要切换到目标分支然后将特征分支合并到目标分支
git branch -d feature-branch
# 删除已合并的分支
git branch -D feature-branch
# 强制删除未合并分支
```
---
```sh
git pull
# 拉取远程更改
git fetch origin
# 获取远程更新
git clone git@github.com:user/repo.git
# 克隆
```
:::note
`Git`的命令有多，以上只是大致了解。还有一些高级功能适合复杂的项目，建议通过实际项目练习。可以仅先了解简单工作流克隆、创建功能分支、编辑提交、推送功能分支到远程、然后创建PR请求合并、最后删除此功能分支。
:::

- Git Flow
    - main：主分支，保持稳定。
    - develop：开发分支，集成新功能。
    - feature branches：为新功能创建分支（如 feature/login）。
    - release branches：用于发布前的调整。
    - hotfix branches：快速修复生产问题。
- Fork 和 Pull Request
    - Fork 仓库到个人账户。
    - 克隆 Fork 的仓库，修改并推送。
    - 在 GitHub 上创建 PR 提交到原仓库。

```sh
git clone git@github.com:user/repo.git
cd repo
git checkout -b feature/add-readme
git add README.md
git commit -m "Add README file"
git push origin feature/add-readme
# Github上创建PR、合并到main
git branch -d feature/add-readme
```

:::note  
`Windows`下注意换行符可以使用以下配置Git
git config --global core.autocrlf true    
:::

---

### Submit information specifications

```markdown title="提交信息格式"
<类型>(<范围>): <简短描述>
<空行>
<详细描述（可选）>
<空行>
<脚注（可选）>
```

- feat：新功能（Feature）。
- fix：修复 Bug。
- docs：文档更改。
- style：代码风格调整（不影响功能，如格式化、空格）。
- refactor：代码重构（不新增功能、不修复 Bug）。
- test：添加或修改测试代码。
- chore：杂项（例如更新依赖、配置工具）。
- perf：性能优化。
- ci：持续集成相关更改。
- build：构建系统或外部依赖更改。
- revert：回滚某次提交。

```markdown title="示例"
feat(auth): add user login endpoint
Add a new endpoint for user authentication with JWT.
Includes input validation and error handling.

Closes #45
```

:::note
简短描述动词开头首字母小写
详细描述提供更多上下文说明“为什么”和“如何”更改
脚注用于关联问题（Issue）或重大变更（Breaking Change）
:::

### Git config & .gitgnore

- Git config

:::tip  
你可以在Git配置目录创建一个提交信息模板文件,并配置使用模板。
`git config --global commit.template ~/.gitmessage.txt`
当你运行`git commit`时你可以根据模板填写提交信息。你可以将你的config和template保存方便后续使用。  
:::

:::note  
你可以在.gitgnore忽略不需要版本控制的文件
每行指定一个忽略模式。
以 / 结尾表示目录
以 # 开头的行为注释
使用通配符  
:::


