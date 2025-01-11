# 自定义管理器

**管理器位于assets/app-builtin/app-manager文件夹内。**
> 不需要也不建议手动去创建，可以通过菜单栏App->创建->Manager选项来进行创建，创建好后框架会自动进行加载。

![输入图片说明](https://foruda.gitee.com/images/1720704145112468777/64296504_542337.png "QQ20240711-211918.png")

**管理器继承自BaseManager。**

- 可以通过重写init方法，来初始化一些管理器内部需要用到的资源，完成后需要调用finish表示初始化完成。

- 同时也提供了onInited和onFinished生命周期回调。
  ```ts
  /**
  * [无序] 自身初始化完成, init执行完毕后被调用
  */
  protected onInited(): any

  /**
  * [无序] 所有manager初始化完成
  */
  protected onFinished(): any

  /**
  * [无序] 初始化manager，在初始化完成后，调用finish方法
  * @param {Function} finish 
  */
  protected init(finish?: Function): any
  ```

**管理器一般存放游戏流程控制相关的逻辑。**

- 如登录流程控制、全局状态管理等

**创建好的管理器通过app.manager.xxx来调用。**

- 如app.manager.ui