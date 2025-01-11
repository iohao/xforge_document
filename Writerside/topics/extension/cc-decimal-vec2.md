# 定点数二维向量

**可以保证各平台计算一致性(可用于帧同步)**
基于定点数的二维向量。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-decimal-vec2```。

## 使用

```TS
import { Decimal } from 'db://pkg/@gamex/cc-decimal';
import { DecimalVec2 } from 'db://pkg/@gamex/cc-decimal-vec2';
const x = new Decimal('1');
const y = new Decimal('2');
const vec2 = new DecimalVec2(x, y);
...
```