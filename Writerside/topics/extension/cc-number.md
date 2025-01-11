# 防内存挂数字类型

防内存挂数字类型，可以防止一些纯前端计算的数值被内存挂监测修改。
> 与cc-store不兼容

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-number```。

## 使用

```TS
import { SafeVarNumber,SafeConstNumber } from 'db://pkg/@gamex/cc-number';
const n1 = new SafeVarNumber(1);
const n2 = new SafeVarNumber(2);
const n3 = new SafeConstNumber(3);

n1.value = n1.value + n2.value;
n2.value = n1.value + n2.value + n3.value;

console.log('n1', n1.value);
console.log('n2', n2.value);
...
```