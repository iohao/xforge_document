# 虚拟列表

虚拟列表。

## 安装

在项目根目录执行```npm run pkg:add @colayue/cc-comp-list-view```。

## 使用

```TS
import { ListView } from 'db://pkg/@colayue/cc-comp-list-view';

@ccclass('CustomItem')
export class CustomItem extends Component {
    @property(Label)
    label1: Label = null;

    @property(Label)
    label2: Label = null;

    // 真实创建的 item
    setLabel1(text: string) {
        this.label1.string = text;
    }

    // 虚拟的 item
    setLabel2(text: string) {
        this.label2.string = text;
    }
}

@ccclass('test')
export class test extends Component {
    @property(ListView)
    list: ListView = null;
    private createCount = 0;
    start() {
        this.list.node.on('create-item', (item) => {
            this.createCount++;
            let customItem = item.getComponent(CustomItem);
            customItem?.setLabel1(this.createCount.toString());
        });
        this.list.node.on('update-item', (item, index) => {
            // console.log(item, index);
            let customItem = item.getComponent(CustomItem);
            customItem?.setLabel2(index.toString());
        });
        this.list.count = 100;
    }

    update(deltaTime: number) {}
}
```