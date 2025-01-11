# 定点数 sap 碰撞检测算法

**可以保证各平台计算一致性(可用于帧同步)**
基于定点数的sap碰撞检测算法。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-decimal-sap```。

## 使用

```TS
import { DecimalSAP, DecimalBody, SortType } from 'db://pkg/@gamex/cc-decimal-sap';
const winSize = view.getVisibleSize();
// 初始化SAP
const sap = new DecimalSAP(SortType.Auto);

// 添加碰撞体
const body = new DecimalBody();
body.setBox({ ... })
sap.insert(body);

// 设置碰撞分组和掩码
body.group = 1 << 0
body.mask = 1 << 0 + 1 << 1;

// 更新碰撞体
body.setAABB(aabb);

// 移除碰撞体
sap.remove(body);

// 碰撞检测
sap.trigger((a, b) => {

});

// 清空
sap.clear();
...
```