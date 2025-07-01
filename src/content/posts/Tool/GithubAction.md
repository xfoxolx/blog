---
title: GitAction の Usage
published: 2024-07-01
description: "GitAciton用法"
tags: ["Tool","GitAction"]
category: Tool
draft: false
---

## GithubAction usage

### 1. What is GithubAction 😕

:::note  
`GitHub Actions` 是一种持续集成和持续交付 （CI/CD） 平台，可用于自动执行生成、测试和部署管道。您可以创建工作流，以便在将更改推送到仓库时运行测试，或者将合并的拉取请求部署到生产环境。  
:::

> `GithubAction`还有[官方市场](https://github.com/marketplace?type=actions)和[awesome action](https://github.com/sdras/awesome-actions)可以让其他开发者引用

:::note[GithubAction基本概念]  
- workflow:持续集成一次运行的过程，就是一个 workflow
- job:一次持续集成的运行可以运行多个任务
- step:执行的任务由多个步骤
- action:每个步骤可以依次执行一个或多个命令
:::

### 2. Writing workflow file

- 在`.github/workflows`中创建yml文件。基本语法如下：

```yml collapse={6-11}
# repository/.github/workflows/example.yml
name: workflow-name # 工作流名称
run-name: Run CI for ${{ github.event_name }} by @${{ github.actor }} 
# 定义workflow运行时的名称，可以使用表达式动态生成名称，提高可读性
# 支持的表达式如下
${{ github.event_name }}: 触发事件名称（如 push、pull_request）。
${{ github.actor }}: 触发工作流的用户或机器人名称。
${{ github.sha }}: 触发工作流的提交 SHA（可以截取短 SHA，如 ${{ github.sha }} 的前 7 位）。
${{ github.ref_name }}: 分支或标签名称（如 main、feature/xyz）。
${{ github.repository }}: 仓库名称（如 owner/repo）。
${{ github.event.head_commit.message }}: 最新的提交信息。
```

- `拉取推送特定分支触发，及推送特定tag和定时触发`

```yml
on: # 指定触发工作流的事件
  push: # 推送到特定分支时触发
    tags:  # 推送标签时触发
      - v2
      - v1.*  
    branches:
      - main
      - 'feature/*' #使用过滤器筛选
  pull_request: # 拉取主分支时触发
    branches:
      - main
  schedule:
    - cron: '0 0 * * *'  # 特定时间触发
  workflow_dispatch: #支持手动触发
```

```yml
# 以上缩写可以指定多个事件，注意分支与on同级
on: [push, pull_request]
branches: [main]
```

- `特定路径触发`

```yml
on:
  push:
    paths:
      - 'sub-project/**'  #包括路径
      - '!sub-project/docs/**' # 排除路径内修改提交不触发
# sub-project文件夹及其子文件夹除docs文件夹中的修改其它修改才触发
```
- `标签事件触发`

```yml collapse={6-8}
on:
  label:
    types:
      - created
# 创建标签时事件触发 
# created：标签被添加。
# edited：标签被修改（比如标签名称或描述变化，通常较少用）。
# deleted：标签被移除。
```

---

- `Job 任务和步骤示例`

```yml
permissions:  # 控制GITHUB_TOKEN 的权限范围
  contents: read
  pull-requests: write
jobs: # 定义任务
  job1-name: # 任务1名称
    name: job1 descriptive name #描述名称可选
    runs-on: ubuntu-latest # 指定运行环境
    steps: # 定义具体步骤
      - name: steps-name
      - uses: <action-name>@<version> # 引用并调用action
      #可以是官方的也可以是自定义的
        with:
          date
      # 定制Action行为传递数据
      shell: bash # 显式指定shell环境
      - run: command # 执行单行命令
      - run: |
          command1
          command2
      # 执行多行命令
  job2-name:
    name: job1 descriptive name
    env:
      variable:value
    runs-on: ubuntu-22.0 # 可指定不同的环境
    needs: job1-name # 指job2依赖job1执行完成控制job顺序
    if: github.event_name == 'push' # 使用if控制条件执行
```

```yml title="设置工作流或 job 的默认配置"
defaults:
  run:
    shell: bash
    working-directory: ./app
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: npm install
```
