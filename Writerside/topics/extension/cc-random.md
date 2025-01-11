# 种子随机

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-random```。

## 使用

```TS
import { Random, random } from 'db://pkg/@gamex/cc-random';
random.setSeed(seed);
// 随机[0,1)的浮点数
random.random();
// 随机[0,100)的浮点数
random.random(100);
// 随机[0,10)的整数
random.randomInteger(0, 10);
// 根据权重随机一个下标
random.randomWeights([100, 20, 30, 40, 50]);

// 创建一个实例
const rnd = new Random(seed);
rnd.random();
...
```