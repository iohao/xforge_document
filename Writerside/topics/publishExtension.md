# 如何发布扩展包

## npm

扩展包是基于npm实现的，所以你需要：

1. 确保你已经在npm上注册账号。如果没有，请访问 [npm官网](https://www.npmjs.com/) 注册。
2. [创建自己的组织](https://www.npmjs.com/org/create)(比如@gamex/cc-request中的gamex就是组织名)
3. 在命令行中登录到你的npm账号。

```
npm login
// 之后按照提示输入你的用户名、密码和电子邮件地址等信息。
```

## 规范

扩展包有3种类型的定义——`模块`、`组件`、`控件`：

- 模块：单纯的库，扩展包名以`cc-`开头，如`cc-request`。
- 组件：有继承cc.Component的类，扩展包名以`cc-comp-`开头，如`cc-comp-rich-text`（组件的类名不需要以cc开头）。
- 控件：在组件的基础上，配套了相应的Prefab、图片等资源，扩展包名以`cc-ctrl-`开头，如`cc-ctrl-toast`。

如果有组件的话，需要注意：

1. ccclass装饰器中要以'pkg:'开头。
2. menu装饰器中要以'pkg/'开头。

```
@ccclass('pkg:RichText')
@menu('pkg/RichText')
export class RichText extends Component {
}
```

## 创建

我们这里以组织名为gamex，要创建一个名为cc-request的用于网络请求的库。

1. 将 [扩展包模版](https://gitee.com/cocos2d-zp/cococs-creator-frame-pkg) fork 到自己的git中。
2. 通过 `master` 创建新的分支 `cc-request`。
3. 通过CocosCreator打开项目。
4. 在菜单栏中选择 `pkg -> 创建`。
   ![输入图片说明](https://foruda.gitee.com/images/1711552828304389338/6fb85856_542337.png "iShot_2024-03-27_22.12.03.png")
5. 在打开的面板中，name填入`@gamex/cc-request`，description填入`网络请求模块`，然后点击创建。
   ![输入图片说明](https://foruda.gitee.com/images/1711552847526487515/b629e2ca_542337.png "iShot_2024-03-27_22.12.49.png")
6. 创建成功后，在资源管理器中就可以看到如下目录结构。
   ![输入图片说明](https://foruda.gitee.com/images/1711552861825381634/a939ea13_542337.png "iShot_2024-03-27_22.15.31.png")
7. 在代码编写完毕并测试用例通过后，确认版本号是否正确、index.ts中是否导出后，就可以通过命令行进行发布了(注意需要先cd到当前扩展包的目录下)
   ![输入图片说明](https://foruda.gitee.com/images/1711552874366885699/792ae9d3_542337.png "iShot_2024-03-27_22.18.12.png")
8. 别忘了git push

## 安装

发布成功后，在项目根目录下执行

```
npm run pkg:add @gamex/cc-request
```

或者

```
// 这种方式可以指定 registry
npm run pkg:add @gamex/cc-request --registry=https://registry.npmmirror.com
```

## 注意

1. 扩展包的assets目录下不光可以存放代码，还可以有Prefab、图片、音频，甚至是Asset Bundle。
2. 扩展包的test目录不会通过`npm publish`发布上去。
3. 与其它Web发布npm的流程不同，我们这里不需要将TS代码构建为JS，直接发布即可。