# Spine

Spine组件。

## 安装

在项目根目录执行```npm run package```，选择```组件```，找到```cc-comp-skeleton```。

## 使用

```TS
import { Skeleton } from 'db://pkg/@gamex/cc-comp-skeleton';
// 播放
node.getComponent(Skeleton).play('animation', 10, {
    onComplete: res => { log(res) },
    timeScale: 1
});
// 播放一次
node.getComponent(Skeleton).playOnce('animation', {
    onComplete: res => { log(res) },
    timeScale: 2
});
// 循环播放
node.getComponent(Skeleton).playLoop('animation');
// 停止并回到第一帧
node.getComponent(Skeleton).stop();
// 暂停
node.getComponent(Skeleton).pause();
// 恢复
node.getComponent(Skeleton).resume();
```
