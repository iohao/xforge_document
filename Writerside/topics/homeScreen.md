# 首屏

**游戏的首屏位于assets/app-appinit文件夹内。**

- res目录用于存放资源。

- view目录用于存放预制体和脚本。

**AppInit继承自BaseAppInit。**

- 需要注意的是在BaseAppInit中是通过Cocos的生命周期start来进行框架的初始化工作，所以如果在AppInit中重写了start方法，一定要调用super.start或this.startInit。

- 可以通过重写getUserAssetNum、onUserInit、onProgress、onFinish，来实现自定义初始化流程(一般是在onUserInit中异步加载资源，完成的回调中调用一次nextInit来触发下一步)。
  ```ts
  /**
  * 监听进度
  * @param {Number} completed
  * @param {Number} total
  */
  protected onProgress(completed: number, total: number): any

  /**
  * 监听开始处理用户初始化数据
  * @param {Number} index
  */
  protected onUserInit(): any 

  /**
  * 获得用户资源总量，这里返回几，就需要自行调用几次nextInit
  */
  protected getUserAssetNum(): number

  /**
  * 初始化完成
  */
  protected onFinish()
  ```