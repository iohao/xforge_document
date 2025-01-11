# 目录结构

## 视频介绍

[https://www.bilibili.com/video/BV1nP8peeE9B/](https://www.bilibili.com/video/BV1nP8peeE9B/)

```
├─assets
│   ├─app
│   │  ├─app.ts     // app单例(框架中的所有单例都绑定在app下)
│   │  ├─handle.ts  // 初始化回调
│   │  └─setting.ts // 配置文件
│   │
│   ├─app-appinit   // 首屏
│   │
│   ├─app-builtin
│   │  ├─app-admin  // 框架自动生成的内容
│   │  ├─app-manager// 管理器
│   │  ├─app-controller// 控制器
│   │  └─app-model  // 数据
│   │
│   ├─app-bundle    // 框架资源包
│   │  ├─app-view   // 界面
│   │  └─app-sound  // 声音
│   │
│   ├─app-scene     // 初始场景
│   │
│   ├─res-bundle    // Bundle动态资源目录
│   └─res-native    // 静态资源目录
│
├─app               // 框架代码
│
└─pkg               // 扩展包
```