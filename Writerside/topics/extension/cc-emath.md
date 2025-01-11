# 精确的数学运算

精确的数学运算模块。

提供了一个emath导出，包含了

- toFixed，对number进行指定位数截取的方法。
- sin、cos、tan、asin、acos、atan、atan2三角函数运算，以避免不同的解释器所带来的误差问题。

> 安装后会直接替换掉原生Math下的sin、cos、tan、asin、acos、atan、atan2方法。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-emath```。

## 使用

```TS
import { emath } from 'db://pkg/@gamex/cc-emath';
emath.toFixed(0.1, 0.2); // 0.3

// 三角函数计算
emath.cos(121);
```