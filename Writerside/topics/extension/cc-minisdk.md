# 小游戏 SDK

小游戏SDK模块，目前支持插屏广告、激励视频广告、banner广告、分享，兼容微信和抖音/头条。

## 安装

在项目根目录执行
```Shell
npm run package
```

选择```模块```，找到```cc-minisdk```。

## 使用

```TS
import { miniSDK, MiniSDK } from 'db://pkg/@gamex/cc-minisdk';
// 直接使用单例
miniSDK.init({
    videoID: '1234567890',
    bannerID: '1234567890',
    interstitialID: '1234567890',
})
miniSDK.showRewardedVideoAd();

// 也可以创建实例
const miniSDK = new MiniSDK({
    videoID: '1234567890',
    bannerID: '1234567890',
    interstitialID: '1234567890',
});
miniSDK.showRewardedVideoAd();
...
```