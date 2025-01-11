# 弹簧臂

- [gitee](https://gitee.com/shpoz/spring-arm-example)
- [论坛](https://forum.cocos.org/t/topic/157150)

## 介绍

弹簧臂组件，可用于防止摄像机穿透物体。
![输入图片说明](https://foruda.gitee.com/images/1712764617184061477/f5d95fb7_542337.gif "2ebf7bb3aa2f99ea19361f5cf070d01872df44b1.gif")

## 安装

在项目根目录执行```npm run package```，选择```组件```，找到```cc-comp-spring-arm```。

## 使用

**给节点添加组件**
选中节点 -> 添加组件 -> pkg -> SpringArm组件

```TS
import { SpringArm } from 'db://pkg/@gamex/cc-comp-spring-arm';
const springArm = node.getComponent(SpringArm);
```
