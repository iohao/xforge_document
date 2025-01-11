# 富文本

富文本组件，拥有比自带富文本组件更优的换行逻辑与更快的初始化速度。

## 安装

```Shell
npm run package
```

，选择```组件```，找到```cc-comp-rich-text```。

## 使用

```TS
import { RichText } from 'db://pkg/@gamex/cc-comp-rich-text';
// 设置富文本
node.getComponent(RichText).string = '<label size=60>文本</label>';
// 追加富文本
node.getComponent(RichText).append('<label size=60>文本</label>');

/**
* 内置的标签:
* label:    文本标签            <label size=60>文本</label>
* image:    图片标签            <image frame=0/>
* node:     节点标签            <node prefab=0/>
* line:     整行标签(独占一整行) <line line-height=10/>
* br:       换行标签            <br/>
* 
* br标签(不支持嵌套)
* 
* line标签(不支持嵌套)
* 支持的属性:
* line-height: 行高            line-height=10
* 
* label标签(支持嵌套，嵌套会继承属性)
* 支持的属性:
* click: 点击事件               click=消息
* offset-y: 偏移Y              offset-y=10
* line-height: 行高            line-height=10
* color: 颜色                  color=#000000
* font: font索引               font=下标
* family: 字体                 family=Arial
* size: 字体大小                size=16
* bold: 字体粗体                bold
* italic: 字体斜体              italic
* underline: 字体下划线         underline
* outline-color: 描边颜色       outline-color=#000000
* outline-width: 描边宽度       outline-width=1
* shadow-color: 阴影颜色        shadow-color=#000000
* shadow-offset: 阴影偏移x,y    shadow-offset=1,2
* shadow-blur: 阴影模糊         shadow-blur=1
* vertical-align: 垂直对齐      top center bottom
*
* image标签(不支持嵌套)
* 支持的属性:
* click: 点击事件
* offset-y: 偏移Y
* line-height: 行高
* frame: frame索引
* width: 宽度(默认lineHeight)
* height: 高度(默认lineHeight)
* vertical-align: 垂直对齐
*
* node标签(不支持嵌套)
* 支持的属性:
* click: 点击事件
* offset-y: 偏移Y
* line-height: 行高
* prefab: prefab索引
* width: 宽度(默认lineHeight)
* height: 高度(默认lineHeight)
* vertical-align: 垂直对齐
*/
```