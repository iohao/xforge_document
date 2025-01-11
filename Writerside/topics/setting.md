# 设置

**设置UIManager和SoundManager，位置位于assets/app/setting.ts内**

```js
// 预加载的UI(符合app.lib.task.createAny规则)
UIManager.setting.preload = ['PageHome', 'PaperHomeIndex'];
// 默认UI, 会在首屏流程后自动show(根据自己界面的名字自行修改)
UIManager.setting.defaultUI = 'PageHome';
// 控制全局背景遮罩透明度与动画
UIManager.setting.shade = { ... };

// 预加载的音频(按数组顺序依次预加载)
SoundManager.setting.preload = [];
// 默认音乐, 会在首屏流程后自动play
SoundManager.setting.defaultMusicName = '';
// 默认音效, 会在Button被点击后播放
SoundManager.setting.defaultEffectName = '';
```