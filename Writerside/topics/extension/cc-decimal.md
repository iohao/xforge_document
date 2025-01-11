# 定点数

**可以保证各平台计算一致性(可用于帧同步)**
定点数模块，用于解决小数计算一致性的问题。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-decimal```。

## 使用

```TS
import { Decimal } from 'db://pkg/@gamex/cc-decimal';
// 结果保留几位小数，默认是6位
Decimal.accuracy = 6;
const num1 = new Decimal('1.2');
const num2 = new Decimal('1.4');
const num3 = num1.add(num2);
console.log('[加法]', 'Decimal:', num3.toNumber(), ' Normal:', 1.2 + 1.4);
```