# 摇杆控件

## 介绍

摇杆控件。

![输入图片说明](https://foruda.gitee.com/images/1720414541081217191/1c8f4fb9_542337.gif "2024-07-08 125415.gif")

## 安装

在项目根目录执行```npm run package```，选择```控件```，找到```cc-ctrl-rocker```。

## 使用

将cc-ctrl-rocker/assets下的Rocker.prefab放到你的UI中，或者你也可以完全自己拼Rocker的UI

```TS
import { Rocker, RockerEventType, RockerType } from 'db://pkg/@gamex/cc-ctrl-rocker';

const rocker = this.rocker.getComponent(Rocker);
// 摇杆类型
rocker.type = RockerType.Free;
// 摇杆半径
rocker.radius = 100;
// 监听摇杆事件
this.rocker.on(RockerEventType.Change, (vec2, ratio) => {
    // vec2 - 方向单位向量
    // ratio - 该方向上的比例
});
// 监听摇杆事件
this.rocker.on(RockerEventType.Stop, () => {

});
...
```
