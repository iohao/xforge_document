# 快速开始

## 环境安装

- [git环境安装](https://git-scm.com/book/zh/v2)
- [node环境安装](https://www.nodejs.com.cn/)(```16```或```18```版本，建议```18```版本，开发使用的版本是```18.18.2```)

## 视频介绍

[https://www.bilibili.com/video/BV138bXeNEUt](https://www.bilibili.com/video/BV138bXeNEUt)

## 创建项目

创建 **空文件夹** (必须是空文件夹)，用来存放项目，我们这里创建文件夹名为`game`
![空文件夹](https://foruda.gitee.com/images/1706117113579532056/c271d122_542337.png "WX20240125-012418.png")

使用```VSCode```打开```game```文件夹，并开启控制台界面，执行：
```npx --registry=https://registry.npmmirror.com @gamex/cc-cli@latest```

![创建开始,75%](https://foruda.gitee.com/images/1706117522075536440/1a490b1c_542337.png "WX20240125-013028.png")

选择 **创建空白项目** 或者 **创建示例项目** ，这里选择 **创建空白项目**。（新手用户可以通过创建示例项目快速学习框架）

![输入图片说明,75%](https://foruda.gitee.com/images/1706117754395194002/70d47d64_542337.png "WX20240125-013536.png")

等待创建完成后，在vscode左侧区域可以看到文件列表。

将`game`文件夹导入到Cocos Dashboard中，然后通过Dashboard启动项目(对应版本的引擎需要存在)

![输入图片说明,75%](https://foruda.gitee.com/images/1706118124376968982/f3f5226b_542337.png "WX20240125-014146.png")

## 创建界面

**框架中所有内容都可以通过菜单栏中的App来创建**。
打开创建工具窗口后，选择View菜单，其中类型选择page，模版选择2D(`2D是Prefab类型，3D是Scene类型`)，**名字输入main**，点击创建按钮，然后在二次确认框中选择「创建并打开」。

![输入图片说明,75%](https://foruda.gitee.com/images/1706684840444887219/7189ac17_542337.png "WX20240131-150626@2x.png")

## 编辑界面

现在Cocos已经自动打开了PageMain，可以在页面中添加Label、Sprite等内容。

## 配置首页

**你需要让框架知道你使用哪个界面作为首页**。
在assets/app/setting.ts文件中编辑：
UIManager.setting.preload = ['PageMain']; // 框架会在初始化过程中按数组顺序进行预加载
UIManager.setting.defaultUI = 'PageMain'; // 设置首页

![输入图片说明,75%](https://foruda.gitee.com/images/1706684750538832585/56355d6c_542337.png "WX20240131-150530@2x.png")

## 预览

使用Cocos Creator的预览功能，在浏览器中进行预览。

## 创建弹窗

点击菜单栏App->创建，选择View菜单，其中类型选择pop，**名字输入test**，点击创建按钮，然后在二次确认框中选择「创建并打开」。

![输入图片说明,75%](https://foruda.gitee.com/images/1706684857327451809/cfe304c2_542337.png "WX20240131-150609@2x.png")

## 编辑弹窗

现在Cocos已经自动打开了PopTest，在页面中添加一个Button，在PopTest.ts中添加按钮点击方法，并与按钮绑定，代码如下：

```ts
onHide(data: number) {
  return data;
}
onClick() {
  // 关闭并传递数据
  // this.hide中的参数类型会自动读取onHide中参数的类型，如果类型不一致会报错
  // this.hide('123'); // 错误，原因是onHide中指定data为number类型，这里为字符串类型
  this.hide(123); // 正确
}
```

## 在首页中打开弹窗

在PageMain中添加一个Button，在PageMain.ts中添加按钮点击方法，并与按钮绑定，代码如下：

```ts
onClick() {
  app.manager.ui.show<PopTest>({
    name: 'PopTest',
    onHide(result) {
      // 打印返回的数据
      console.log('弹窗关闭', result);
    }
  })
}
```

## 预览

使用Cocos Creator的预览功能，在浏览器中进行预览。