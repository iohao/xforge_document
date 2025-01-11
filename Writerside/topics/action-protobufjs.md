# protobufjs

原帖地址：https://forum.cocos.org/t/topic/154256

关于如何在Cocos Creator 各个版本中使用protobufs这一问题，我和大家一样几乎搜遍了互联网所有相关的帖子，到最后我还是没有解决，总是会报出各种问题，我不得不怀疑，那些帖子都没有深入到本质问题上面去，而只是碰巧解决了。

我的项目是3.8.0，经过一番摸索，最终还是在cocos creator的官方文档中找到了答案，此刻我就化身cocos creator讲师，给大家讲一下我是如何解决的：

1.假设大家已经有3.8.0项目了（Typescript）。
2.为了去除一些可变因素，先在项目目录下执行命令:

```
npm remove -g protobufjs // 移除全局安装的protobufjs
npm remove -g protobufjs-cli // 移除全局安装的protobufjs-cli
npm remove -g pbjs // 这个pbjs是可以单独安装的，我也不知道为什么。
npm remove --save protobufjs // 移除项目中的
npm remove --save protobufjs-cli // 移除项目中的
npm remove --save pbjs // 移除项目中的
```

到此，关于protobufjs的可变因素应该已经完全去除了，再让我们从0开始吧，仍然是在项目目录下执行命令：

```
npm install --save protobufjs // 安装到项目中，这会安装最新的protobufjs
npm install --save protobufjs-cli // 安装到项目中，这会安装最新的protobufjs-cli
```

这样，protobufjs相关的库就安装好了。

我们接着在项目目录中新建一个 proto3 格式的proto文件cmd.proto，内容如下：

```
syntax = “proto3”;

package eproto;

enum CommonCmd {
Unkown = 0;

C2S_Heartbeat = 1;
S2C_Heartbeat = 2;
}
```

然后将proto文件生成 proto.js 以及 描述文件 proto.d.ts：

```
./node_modules/protobufjs-cli/bin/pbjs -t static-module -w commonjs cmd.proto -o assets/proto.js
./node_modules/protobufjs-cli/bin/pbts assets/proto.js -o assets/proto.d.ts
```

顺利的话，你会看见assets/目录下面应该已经生成好了这两个文件(proto.js和proto.d.ts)，接下来，很多帖子会告诉你去修改生成出来的文件，去把protobufjs导入为插件等等之类的，其实不用。

我们现在可以直接使用了！具体做法是：
1.在你需要引入proto的class文件中，像这样引入：

```
import { default as root } from “…/…/proto.js”;// 此处你要修改成正确的相对路径，但是请记得一定要是proto.js结尾.
const { eproto } = root;
```

好了，你可以在代码中访问eproto中的数据了

```
console.log(“eproto => %o”, eproto);
```

不出意外的话，这个输出就是你想要的答案了吧。