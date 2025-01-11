# 入口场景

**入口场景位于assets/app-scene/main.fire。**
![输入图片说明](https://foruda.gitee.com/images/1720704240131068906/06456c0e_542337.png "QQ20240711-212339.png")

##### Root2D

- 2D的根节点,同时它也是常驻节点。

##### Root2D/CameraCleaner

- 它不负责渲染任何内容，它的Priority为 **0**、Visibility为 **Nothing**、ClearFlags为 **SOLID_COLOR**。
- 它存在的目的是为了简化多相机的使用，开发过程中不用关心它的存在。

> 比如n个人分别开发n个页面，每个页面都有一个摄像机，这n个页面的展示时机不同、渲染顺序不同，这种情况要区别哪个相机是首个渲染的相机很麻烦(因为首个相机需要负责清理工作)

##### Root2D/CameraDefault

- 它负责渲染UI内容，它的Priority为 **1000**、Visibility为 **UI2D**、ClearFlags为 **DEPTH_ONLY**。

> 在多相机的使用场景中，如果你想渲染的内容在UI下面，则相机的0 < Priority < 1000。如果在UI上面，则相机的Priority > 1000。

##### Root2D/AppInitLayer

- 首屏的容器，AppInit是其子节点(AppInit.ts也是入口脚本)

##### Root2D/UserInterface

- 2D界面的根节点。

##### Root2D/MainManager

- 框架内置管理器的根节点。

> 管理器是以`Prefab+Script`的形式存在，这使得管理器的能力更加强大。

##### Root2D/UserManager

- 用户自定义管理器的根节点。