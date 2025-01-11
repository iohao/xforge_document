# 界面

**UI位于assets/app-bundle/app-view文件夹内。**
> 不需要也不建议手动去创建，可以通过菜单栏App->创建->View选项来进行创建。

**UI目录包含native和resources两个文件夹。**
![输入图片说明](https://foruda.gitee.com/images/1720703765088660775/42484e20_542337.png "QQ20240711-211546.png")
**native和resources都是Bundle，它们将分别采用不同的分包策略，来达到在各平台上加载性能与体积最优。**
> Bundle的优先级及构建策略会容易让人混乱，这里给出一种[最佳实践方案](https://gitee.com/cocos2d-zp/xforge/wikis/pages?sort_id=13017429&doc_id=6236543)

- native的优先级是1，负责存储UI脚本与Prefab/Scene资源，native/expansion目录存放其它脚本文件。
    - 在`小游戏`环境中，native默认会以`小游戏分包`的形式存在(可以在`项目设置->Bundle配置`中按需调整)。
    - 在`网页`环境中，native默认会以`远程包`的形式存在(可以在`项目设置->Bundle配置`中按需调整)。
    - 在`原生`环境中，native默认会以`本地包`的形式存在(可以在`项目设置->Bundle配置`中按需调整)。
  > **一定不要** 在native的Prefab等资源中引用main包中的资源，因为这会导致构建后资源被拷贝进来。而在小游戏平台native目录会作为小游戏分包的形式存在，这样会 **导致资源文件霸占代码空间** 。

- resources的优先级是4，负责存储除脚本以外的资源，如图片、材质、模型、Spine、Font、Prefab等。
    - 在`小游戏`环境中，native默认会以`远程包`的形式存在(可以在`项目设置->Bundle配置`中按需调整)。
    - 在`网页`环境中，native默认会以`远程包`的形式存在(可以在`项目设置->Bundle配置`中按需调整)。
    - 在`原生`环境中，native默认会以`本地包`的形式存在(可以在`项目设置->Bundle配置`中按需调整)。
  > 1.尽量不在resources的Prefab等资源中可以引用main包中的资源，还是因为会导致构建后资源被拷贝进来。但因为resources默认是远程包，所以并不需要严格要求。
  > 2.多UI通用资源请存放在Cocos默认的resources目录或其它优先级>4的Bundle中。

**UI继承自BaseView，在Cocos原有的生命周期函数外，又增加了一些框架的生命周期函数。**

- `beforeShow`：UI显示前触发。
  > 可用于在显示前加载或处理某些任务，比如在Page显示之前先显示Paper，可以避免视觉上Page和Paper显示延迟的割裂感。

- `onShow`：UI显示后触发。
  > 设置UI内容的逻辑都写在这个回调里面。

- `beforeHide`：UI卸载前触发。

- `onHide`：UI卸载后触发。

- `onFocus`：UI获取焦点时触发。
  > 需要勾选UI脚本所在的编辑器面板中的Capture Focus选项。

- `onLostFocus`：UI失去焦点时触发。
  > 需要勾选UI脚本所在的编辑器面板中的Capture Focus选项。

- `onError`：可以监听当前UI加载报错。

- `onShade`：可以控制当前UI背景遮罩的颜色和动画。

**UI分为4类：Page、Paper、Pop和Top，同Camera下层级顺序Top > Pop > Paper > Page**

- Page区分3D与2D类型，3D类型的Page会以cc.Scene的形式存在，2D类型以cc.Prefab的形式存在。

- Paper是Page的扩展，往往一个大型页面可以拆分部分功能区到Paper中，最终通过Page+Paper的方式共同完成渲染(单人开发或小页面可以不使用Paper)。

- Pop用于创建业务弹窗。

- Top用于创建一些系统级的弹窗。

> 简单总结：Page相当于场景的概念。Paper并不总是被需要，只有大型页面才需要使用Paper对Page的功能进行分割，分配给多人同时开发。Pop是各类业务弹窗。Top是最顶级的弹窗，可用于错误提示、转场Loading等。


**UI脚本所在编辑器面板的选项。**
![输入图片说明](https://foruda.gitee.com/images/1720702915804971609/b701bfed_542337.png "QQ20240711-205834.png")

- Hide Event
    - 如果选择active，节点只会被隐藏，第二次加载的速度会更快，建议经常打开的UI选择active。

    - 如果选择destroy，节点会被销毁，会自动清理自身所有的资源，不管是静态还是动态引用的。

- Singleton

    - 如果勾选的话，则重复通过app.manager.ui.show来加载此UI的话，全局只会有一份UI实例。

    - 如果去掉勾选的话，则重复通过app.manager.ui.show来加载此UI的话，会重复创建UI。

- Capture Focus

    - 勾选后，才可以触发UI的onFocus和onLostFocus回调。

- Shade

    - 勾选后，才会在UI下面生成一个黑色(可设置透明度)的遮罩。

- Block Input

    - 勾选后，会使触摸无法穿透此UI。
