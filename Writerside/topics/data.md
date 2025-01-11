# 数据

**数据位于assets/app-builtin/app-model文件夹内。**
> 不需要也不建议手动去创建，可以通过菜单栏App->创建->Model选项来进行创建。

![输入图片说明](https://foruda.gitee.com/images/1720703997646967527/b046643a_542337.png "QQ20240711-211901.png")

框架内置了数据管理，分为store、data和config类型，可以通过app.data、app.config和app.store来访问。

- 【推荐】store类型的数据，**可以定义方法**，所有属性都是**只读**，用于存储安全的数据(数据只允许在内部修改，外部只有访问权限)。
- config类型的数据，**不可以定义方法**，所有属性都是**只读**，用于存储静态配置。
- data类型的数据，**不可以定义方法**，所有属性都是**可读可写**，用于存储不安全的数据(因为可以在任何地方修改它)。

**store类型的引入是借鉴了Web前端框架中全局状态管理的思路，意图是让数据更安全，更可控。同时框架中还提供了数据绑定的扩展包[cc-store](https://gitee.com/cocos2d-zp/cococs-creator-frame-3d/wikis/%E6%89%A9%E5%B1%95%E5%8C%85/%E5%AE%98%E6%96%B9%E6%89%A9%E5%B1%95%E5%8C%85/cc-store)，可实现「数据->视图」的单向绑定。**
