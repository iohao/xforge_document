# 碰撞检测-SAP

碰撞检测可分为 Broad Phase （粗略检测）与 Narrow Phase （精细检测） 两个阶段。
SAP(Sweep and Prune)正交分离轴算法，适用于基于AABB的 **粗略检测** 阶段。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-sap```。

## 使用

```TS
import { SAP, Body, SortType } from 'db://pkg/@gamex/cc-sap';
const winSize = view.getVisibleSize();
// 初始化SAP
const sap = new SAP(SortType.Auto);

// 添加碰撞体
const body = new Body();
body.setRect(node.getComponent(UITransform).getBoundingBoxToWorld());
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
