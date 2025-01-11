# 常用的数据结构

一些常用的数据结构。

## 安装

在项目根目录执行```npm run pkg:add @colayue/cc-collections```。

## 使用

```TS
import { Dictionary, List, Stack, Queue } from 'db://pkg/@colayue/cc-collections';

let myQueue = new Queue();
myQueue.enqueue(1);
myQueue.enqueue(2);

console.log(myQueue.dequeue()); // prints 1
console.log(myQueue.dequeue()); // prints 2
```