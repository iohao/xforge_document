# Animation 动画

Animation组件。

## 安装

在项目根目录执行```npm run package```，选择```组件```，找到```cc-comp-animation```。

## 使用

```TS
import { Animation } from 'db://pkg/@gamex/cc-comp-animation';
node.getComponent(Animation).play('animation', 20, {
    onComplete: (success) => {
        console.log('onComplete', success)
    }
});
node.getComponent(Animation).playOnce('animation', {
    onComplete: (success) => {
        console.log('onComplete', success)
    }
});
node.getComponent(Animation).playLoop('animation', {
    onComplete: (success) => {
        console.log('onComplete', success)
    }
});
```