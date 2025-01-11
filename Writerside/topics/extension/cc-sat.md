# 碰撞检测-SAT

碰撞检测可分为 Broad Phase （粗略检测）与 Narrow Phase （精细检测） 两个阶段。
SAT(Separating Axis Theorem)分离轴定理，适用于任意2D凸多边形的 **精细检测** 阶段。

**同屏200个三角形、200个矩形和200个圆相互间碰撞检测性能对比**

- Cocos自带的碰撞检测
  ![Cocos自带的碰撞检测](https://foruda.gitee.com/images/1716354015430330562/1489b9d0_542337.png "QQ20240522-125729.png")
- SAT碰撞检测
  ![SAT碰撞检测](https://foruda.gitee.com/images/1716354028682329357/607cab02_542337.png "QQ20240522-125749.png")

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-sat```。

## 使用

```TS
import { Circle, Box, Polygon, checkCollision } 'db://pkg/@gamex/cc-sat';
const center = { x: 0, y: 50 };
const box = new Box( [
    {x: 0, y: 0},
    {x: 0, y: 100},
]，center);
const polygon = new Polygon([
    {x: -100, y: 0},
    {x: 0, y: 100},
    {x: 0, y: 0},
]，center);
const circle = new Circle(100，center);

// 移动
box.move(10, 10);
// 旋转
polygon.rotate(Math.PI / 2);
// 缩放
circle.scale(2);

// 碰撞检测
checkCollision(box, polygon);
checkCollision(polygon, circle);
checkCollision(box, circle);

// 获取轴对称包围盒
box.aabb
polygon.aabb
circle.aabb
...
```