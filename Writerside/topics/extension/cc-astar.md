# A星巡路

**可以保证各平台计算一致性(可用于帧同步)**

A星巡路模块，支持：

- 四边形的4方向、8方向及自由模式(基于8方向+漏斗算法)巡路
- 六边形的6方向巡路

同时还导出了一个用于路径平滑的函数(不能保证计算一致性)。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-astar```。

## 使用

```TS
import { AStar } from 'db://pkg/@gamex/cc-astar';
const aStar = new AStar(10, 10);
aStar.addObstacle(3, 3);
aStar.addObstacle(3, 4);
aStar.addObstacle(4, 3);
aStar.addObstacle(4, 4);
// 同步模式
const path = aStar.findPath(0, 0, 9, 9, AStar.Mode.Square_Free);
console.log(path);
// 异步模式
const path = await aStart.findPathAsync(0, 0, 9, 9, AStar.Mode.Square_Free, 50);// 每次迭代搜寻50次，直至搜到结果
console.log(path);
```
