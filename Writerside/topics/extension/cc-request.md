# http 请求

网络请求模块，用于处理http请求。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-request```。

## 使用

```
import { request } from 'db://pkg/@gamex/cc-request';
const {error, response} = await request({
  url: 'https://www.baidu.com/',
  method: 'GET'
})
```