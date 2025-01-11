# 定点数种子随机

**可以保证各平台计算一致性(可用于帧同步)**
基于定点数的种子随机模块。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-decimal-random```。

## 使用

```TS
import { Decimal } from 'db://pkg/@gamex/cc-decimal';
import { DecimalRandom, decimalRandom } from 'db://pkg/@gamex/cc-decimal-random';

decimalRandom.random(min, max);

const seed = Decimal.createInt(473);
const random = new DecimalRandom(seed);

const min = Decimal.createInt(1);
const max = Decimal.createInt(10);
const result = random.random(min, max);
...
```