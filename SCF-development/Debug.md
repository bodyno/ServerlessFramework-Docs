---
title: '远程调试'
menuText: '远程调试'
layout: Doc
---

> 当前该指令只支持通过 Serverless Framework 云函数组件部署的函数项目，其它组件的支持也在计划中

Serverless Framework 云函数组件支持通过 `invoke` 命令触发云函数进行调试。对于`sls deploy`部署成功的云函数，进入对应函数的项目目录下，执行函数调用命令，即可完成云上函数资源的远程调试，调试结果会在命令行进行输出：

```
sls invoke  --inputs function=functionName  clientContext='{"weights":{"2":0.1}}'
```


>- `invoke`命令必须在该函数部署的 serverless.yml 文件同目录下执行。
>- `clientContext`为触发函数时传递的 json 字符串。可以根据 [触发事件模板](https://cloud.tencent.com/document/product/583/14572) 的 json 字符串格式模拟不同触发事件。