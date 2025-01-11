# 内置管理器

**框架有内置的管理器，包括：UI、音频、下载、事件、定时器。**

- **UIManager**：通过app.manager.ui访问，用于控制UI显示。

  ```js
  // 显示一个UI
  app.manager.ui.show<UI类>({
      name: '自动提示UI名',
      data: 自动提示onShow方法需要的参数,
      onShow: () => {

      },
      onHide: (result) => { 
        //result自动识别为onHide的返回值类型 
      },
      onError: () => {

      }
  });
  // 关闭一个UI
  app.manager.ui.hide<UI类>({
      name: '自动提示UI名',
      data: 自动提示onHide方法需要的参数,
      onHide: (result) => { 
        //result自动识别为onHide的返回值类型 
      },
  })
  ```

- **SoundManager**：通过app.manager.sound访问，用于控制声音播放。

  ```js
  app.manager.sound.playMusic({name:'自动提示音频名'});

  app.manager.sound.stopMusic();

  const id = app.manager.sound.playEffect({name:'自动提示音频名'});

  app.manager.sound.stopEffect(id);

  app.manager.sound.stopAllEffects();
  ```

- **TimerManager**：通过app.manager.timer访问，用于创建全局定时器。

  ```js
  // 创建或获取定时器
  // app.manager.timer.get返回值的类型是cc.Component的子类
  const timer = app.manager.timer.get(自定义标识);

  timer.schedule // 同cc.Component.prototype.schedule
  timer.scheduleOnce // 同理
  timer.unschedule // 同理
  timer.unscheduleAllCallbacks // 同理

  // 注册每日触发器(基于本地时间，使用cc.Component.prototype.update驱动)
  timer.registerDailyTrigger('8:00:01-9:00',()=>{ 
    console.log('8点01点到9点整之间每帧触发') 
  })
  // 取消每日触发器
  timer.unregisterDailyTrigger

  // 删除定时器
  app.manager.timer.delete(自定义标识);
  // 删除所有定时器
  app.manager.timer.clear();
  ```

- **EventManager**：通过app.manager.event访问，用于创建全局事件。

  ```js
  // 创建或获取事件管理器
  // app.manager.event.get返回值的类型是cc.EventTarget
  const event = app.manager.event.get(自定义标识);

  event.on('event', ()=>{}, target) // 同cc.EventTarget.prototype.on
  event.once('event', ()=>{}, target) // 同理
  event.off('event')或event.off('event', ()=>{}) // 同理
  event.targetOff(target)  // 同理

  // 删除事件管理器
  app.manager.event.delete(自定义标识);
  // 删除所有事件管理器
  app.manager.event.clear();
  ```

- **LoaderManager**：通过app.manager.loader访问，用于加载资源。

  ```js
  app.manager.loader.load({
    bundle: 'xxx', // 不传入bundle，默认为resources
    path: 'xxx/xxxx'
    type: Asset,
    onComplete(asset){
      
    }
  })
  ```