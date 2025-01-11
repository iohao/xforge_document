# 3D骨骼动画

3D骨骼动画组件。

## 安装

在项目根目录执行```npm run package```，选择```组件```，找到```cc-comp-skeletal-animation```。

## 使用

```TS
import { SkeletalAnimation } from 'db://pkg/@gamex/cc-comp-skeletal-animation';
node.getComponent(SkeletalAnimation).play('animation', 20, {
    onComplete: (success) => {
        console.log('onComplete', success)
    }
});
node.getComponent(SkeletalAnimation).playOnce('animation', {
    onComplete: (success) => {
        console.log('onComplete', success)
    }
});
node.getComponent(SkeletalAnimation).playLoop('animation', {
    onComplete: (success) => {
        console.log('onComplete', success)
    }
});
```