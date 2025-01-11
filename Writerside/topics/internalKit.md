# 内置工具

框架内只内置了最基本的工具库，其它工具库通过扩展包的形式添加。

`内置工具通过app.lib调用，包含：`

## 1、创建异步、同步任务

```
const task = app.lib.task.createASync();
task.add((next, retry) => {
    if (成功) {
        // 任务成功，继续执行
        next(数据);
    } else {
        // 等待0.5秒后重试
        retry(0.5);
    }
});
task.add((next, retry) => {
    if (成功) {
        // 任务成功，继续执行
        next(数据);
    } else {
        // 任务失败，停止任务
        task.stop();
    }
});
task.start((results, success) => {
    console.log(success ? '任务成功' : '任务失败');
});
```

## 2、本地数据存储

```
// 存取数据
app.lib.storage.set('key', 'value');
app.lib.storage.get('key');
// 存取每天过期数据
app.lib.storage.setDay('key', 'value');
app.lib.storage.getDay('key');
// 存取每周过期数据
app.lib.storage.setWeek('key', 'value');
app.lib.storage.getWeek('key');
```

## 3、输出log

```
app.lib.logger.log('标题', arg);
```