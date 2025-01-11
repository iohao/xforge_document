# 奖励飞行动画

奖励飞行动画组件。

## 安装

在项目根目录执行```npm run package```，选择```组件```，找到```cc-comp-rewardfly```。

## 使用

```TS
import { RewardFly } from 'db://pkg/@gamex/cc-comp-rewardfly';

node.getComponent(RewardFly).add({
    item: this.item,
    count: 10,
    start: v3(Math.random() * 400 - 200, Math.random() * 400 - 200, 0),
    startRange: [100, 100],
    end: this.end,
    endOffest: [-20, -20],
    highlight: true,
    highlightArea: this.end.parent,
    highlightOffset: [0, -100],
    onFinish: (nodeCopy) => {
        
    }
})
```