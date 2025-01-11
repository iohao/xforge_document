# 碰撞检测-四叉树

碰撞检测可分为 Broad Phase （粗略检测）与 Narrow Phase （精细检测） 两个阶段。
四叉树(quadtree)碰撞检测算法，适用于基于AABB的 **粗略检测** 阶段。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-quadtree```。

## 使用

```TS
import { QuadTree, Body } from 'db://pkg/@gamex/cc-quadtree';
const winSize = view.getVisibleSize();
// 初始化四叉树
const quadTree = new QuadTree(0, 0, winSize.width, winSize.height);

// 添加碰撞体
const body = new Body();
body.setRect(node.getComponent(UITransform).getBoundingBoxToWorld());
quadTree.insert(body);

// 设置碰撞分组和掩码
body.group = 1 << 0
body.mask = 1 << 0 + 1 << 1;

// 更新碰撞体
body.setAABB(aabb);

// 移除碰撞体
quadTree.remove(body);

// 碰撞检测
quadTree.trigger((a, b) => {

});

// 清空
quadTree.clear();
···
```
