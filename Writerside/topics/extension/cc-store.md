# store，数据与 UI 的单项绑定

基于Mobx实现的状态管理模块，用于与框架中store类型数据配合，实现数据=>UI的单项绑定。
> 与cc-number不兼容

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-store```。

## 使用

```TS
import {createStore, bindStore, stopBind, watchStore, stopWatch} from 'db://pkg/@gamex/cc-store';

// store.game
export default class Game implements IStore<Game> {
    // 将当前实例转成Store
    constructor() { createStore(this); }
    // 状态
    count = 0;
    // 更新状态
    setCount(count: number) {
        this.count = count;
    }
}

// PageHome.ts
onLoad() {
    // 状态与组件属性绑定
    bindStore(this.label, 'string', () => {
        return app.store.game.count.toString();
    });
    // 状态与节点属性绑定
    bindStore(this.label.node, 'active', () => {
        return app.store.game.count % 2 == 0;
    });
    // 监听状态变化
    watchStore(()=> app.store.game.count, this.onCountChange, this);
    app.store.game.setCount(10);
}
onDestroy() {
    // 在节点或组件被销毁后会自动解绑，一般不需要手动解绑
    // 但如果是通过node.removeFromParent方法移除node，这个时候是不会自动解绑的，如果需要请手动解绑
    stopBind(this.label, 'string');
    stopBind(this.label.node, 'active');
    // watchStore必须要手动停止
    stopWatch(this.onCountChange, this);
}
```