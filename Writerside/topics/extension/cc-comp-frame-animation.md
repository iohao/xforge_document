# 帧动画播放

帧动画播放组件。

## 安装

```Shell
npm run package
```

，选择```组件```，找到```cc-comp-frame-animation```。

## 使用

```TS
import { FrameAnimation } from 'db://pkg/@gamex/cc-comp-frame-animation';
// 播放
node.getComponent(FrameAnimation).play('animation', 10, {
    onComplete: res => { log(res) },
    timeScale: 1
});
// 播放一次
node.getComponent(FrameAnimation).playOnce('animation', {
    onComplete: res => { log(res) },
    timeScale: 2
});
// 循环播放
node.getComponent(FrameAnimation).playLoop('animation');
// 停止并回到第一帧
node.getComponent(FrameAnimation).stop();
// 暂停
node.getComponent(FrameAnimation).pause();
// 恢复
node.getComponent(FrameAnimation).resume();
```