# 定点数 sat 碰撞检测算法

**可以保证各平台计算一致性(可用于帧同步)**
基于定点数的sat碰撞检测算法。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-decimal-sat```。

## 使用

```TS
import { Decimal } from 'db://pkg/@gamex/cc-decimal';
import { DecimalVec2 } from 'db://pkg/@gamex/cc-decimal-vec2';
import { Box, Circle, checkCollision } from 'db://pkg/@gamex/cc-decimal-sat';

const box_center = new DecimalVec2(new Decimal(), new Decimal());
const box_min = new DecimalVec2(new Decimal('-2'), new Decimal('-2'));
const box_max = new DecimalVec2(new Decimal('2'), new Decimal('2'));
// 创建盒子碰撞体
const box = new Box(box_center, [box_min, box_max]);

const circle_center = new DecimalVec2(new Decimal(), new Decimal());
const circle_radius = new Decimal('4');
// 创建圆碰撞体
const circle = new Circle(circle_center, circle_radius);

// 碰撞检测
checkCollision(box, circle);
...
```
