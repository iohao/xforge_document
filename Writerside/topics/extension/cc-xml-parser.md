# XML解析器

XML解析器模块

## 安装

```Shell
npm run package
```

，选择```组件```，找到```cc-xml-parser```。

## 使用

```TS
import { parseXML } from 'db://pkg/@gamex/cc-xml-parser';
const xml = '<root><item a=1 b=true c>text1</item><item>text2</item></root>';
const tree = parseXML(xml);
console.log(tree.children);
console.log(tree.toJSON());
```
