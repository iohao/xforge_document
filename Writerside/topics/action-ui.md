# UI 层级的最佳实践

**框架内只有Page、Paper、Pop、Top4个预设的层级，且不支持自定义添加。**

Q: 按照框架规范，如果有两个Top但是其中A必须在B上面显示，该怎么办？
A: 可以在onLoad或onShow中设置UI的 **z坐标** ，z坐标越大的UI层级越高，设置z坐标的方式同样适用于Page、Paper、Pop。

```
class TopA extends BaseView {
    onLoad(){
        this.node.z = 2;// 2比1大，且AB为同类型UI，则A永远显示在B上面
    }
}
class TopB extends BaseView {
    onLoad(){
        this.node.z = 1;
    }
}
```