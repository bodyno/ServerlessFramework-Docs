---
title: '环境管理'
menuText: '环境管理'
layout: Doc
---

由于云上不同服务对环境的概念不同，Serverless Framework 支持通过 `stage` 参数配置，实现多环境模拟，此处以 `Express` 项目为例，示例 `serverless.yml` 文档如下：

```
component: express
name: expressDemo
app: appDemo
stage: test  #想要模拟多环境时，此参数必填，代表不同环境

inputs: 
   functionName: expressDemo-${stage} #想要模拟多环境，此参数必填
   src: ./ #需要上传的项目路径
   region: ap-guangzhou
   runtime: Nodejs10.15
   apigatewayConf:
      protocols:
        - http
        - https
      environment: test 
      # 该参数为 API 网关产品环境参数，仅支持 test（测试环境）、prepub（预发布环境）和 release（发布环境），建议和 stage 一致
```

除了基本的必填参数之外，为了实现多环境配置，以下参数也是必填的：

1）`stage` 参数：关键参数，规定不同环境

2）`functionName` 参数：函数名称，需要写为 `FunctionName-${stage}` 格式，其中的 `stage` 变量必须引入，如果没这个变量，则不同环境的函数会相互覆盖。

3）`environment`: 是配置云函数的调用 API 环境，仅支持 test（测试环境）、prepub（预发布环境）和 release（发布环境），为方便管理，建议和 stage 一致

完成 yml 配置后，只需更新 `stage` 参数，即可完成应用不同环境的切换。
