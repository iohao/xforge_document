# 控制器


**管理器位于assets/app-builtin/app-controller中。**

> 不需要也不建议手动去创建，可以通过菜单栏App->创建->Controller选项来进行创建。

![输入图片说明](https://foruda.gitee.com/images/1720704122485028069/e37ddbd9_542337.png "QQ20240711-211930.png")

**控制器继承自BaseController。**

- 控制器内部可以新建变量和方法，在外部通过app.controller.xxx调用时，变量和方法会显示为只读属性。

- 控制器内部有emit和call方法，用来发射事件，这两个方法只能在内部或绑定了控制器的UI内部使用。两个方法区别在于call方法只会执行第一个注册的事件并获得返回值。

- UI需要通过继承BaseView.BindController(XXXController)来绑定一个控制器(此时控制器必须以import的方式引入)，并通过this.controller访问到这个控制器实例，与app.controller调用不同的是，它是不受限的(属性等都不是只读)，而且可以通过this.controller中的on、once、off、targetOff来接收和关闭emit或call的事件。

- **与cc.Node的事件不同，通过controller注册的事件，需要通过off或targetOff手动销毁**。

**控制器与管理器的区别**

- 控制器可以被多个UI绑定，起到UI间共享内部数据、相互内部通信的目的。同时控制器也是一组UI的对外导出，通过对外提供方法的方式，让外部可以向UI内部传递数据。
- 管理器是公开的，可以被任何人随意的调用，一般用于游戏流程控制。