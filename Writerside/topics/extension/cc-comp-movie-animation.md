# MovieClip 播放

MovieClip播放组件(白鹭引擎的动画格式)。

## 安装

```Shell
npm run package
```

，选择```组件```，找到```cc-comp-movie-animation```。

## 使用

```TS
import { MovieAnimation } from 'db://pkg/@gamex/cc-comp-movie-animation';
// 播放
node.getComponent(MovieAnimation).play('animation', 10, {
    onComplete: res => { log(res) },
    timeScale: 1
});
// 播放一次
node.getComponent(MovieAnimation).playOnce('animation', {
    onComplete: res => { log(res) },
    timeScale: 2
});
// 循环播放
node.getComponent(MovieAnimation).playLoop('animation');
// 停止并回到第一帧
node.getComponent(MovieAnimation).stop();
// 暂停
node.getComponent(MovieAnimation).pause();
// 恢复
node.getComponent(MovieAnimation).resume();
```