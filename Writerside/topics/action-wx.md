# 微信小游戏平台分包策略最佳实践

## 一、面临的问题

**CocosCreator3.x的引擎体积越来越大(以下数据基于3.8.2版本)：**

- 2D游戏开启全部功能(除了龙骨和物理引擎)，引擎基础资源在2.5M左右
- 3D游戏在不启用物理引擎的情况下，引擎基础资源在3M左右

**而小游戏平台对于分包体积有以下限制：**
[整个小游戏所有主包+分包大小不超过 20M（开通虚拟支付后的小游戏不超过30M）](https://developers.weixin.qq.com/minigame/dev/guide/base-ability/subPackage/useSubPackage.html)：

- 主包不超过 4M
- 单个普通分包不限制大小
- 单个独立分包不超过 4M

**开发2D游戏仅剩余1.5M左右的空间，而3D游戏更是仅剩1M。**

## 二、XForge做了什么

```XForge```在设计时就已经考虑到了这个问题，它是这样做的：

- 框架、扩展包以及不在[Asset Bundle](https://docs.cocos.com/creator/manual/zh/asset/bundle.html?h=bundle)中的资源，在CocosCreator中都会被认为在主包内。

> 正常来说构建后会占用小游戏主包空间，但构建时可以设置主包压缩类型为“小游戏分包”，这样「Cocos的主包」就会作为小游戏的分包存在。

- 由于小游戏平台仅对总体积有限制，而对分包数量没有限制，```XForge```在创建 **Manager**、**Control**、**Model**、**View的native** 时会将它们都设置为“小游戏分包”。

> View 比较特殊，它由两个 **Asset Bundle** 构成———其中 **native** 目录用于存储脚本及UI预制体，它默认会以“小游戏分包”的形式存在； **resources** 目录用于存储图片等资源，它默认会以"远程分包"的形式存在。

- 小游戏总包体是有上限的，这些宝贵的空间需要尽可能的留给脚本资源，所以```XForge```在创建 **Sound**、**View的resources** 时，会将它们默认设置为"远程分包"。

## 三、最佳实践

1. ```XForge```会自动帮你搞定内部的分包逻辑，你无需操心。
2. 通过```XForge```或开发者自己创建的Asset Bundle、resources目录(Cocos内置的Asset Bundle目录)，需要开发者自己注意选择合适的压缩类型，如果是脚本资源设置为“小游戏分包”，其它资源设置为"远程分包"。
3. 构建时「主包压缩类型」选为「小游戏分包」。
   ![输入图片说明](https://foruda.gitee.com/images/1711083889079617378/911c3fe0_542337.png "iShot_2024-03-21_22.26.04.png")

> **如果你确认你的小游戏总包体没有超过20M(或30M)，那可以在项目设置->Bundle配置中将app-res的小游戏配置改为「小游戏分包」，这样就可以不需要部署远程资源服务器了。**

## 四、特殊注意

目前来看，虽然文档中没有写，但是实际上微信小游戏限制分包数量不能超过100个。
由于xforge中每个ui会存在1个小游戏分包，对于游戏中最多的ui应当是pop类型。
所以如果项目内弹窗数量很多，需要做好归类，一类的弹窗最好只创建一个pop目录。
> 比如，你想要pop-act1-begin、pop-act1-over、pop-act1-reward这4个弹窗。
> 可以只创建一个pop-act1的UI目录，将pop-act1-begin、pop-act1-over、pop-act1-reward做成prefab，在pop-act1中动态加载。

