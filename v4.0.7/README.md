# 微信小游戏 SDK v4.0.7

2026-11-23

基础包和全量包均支持巨量引擎微信小游戏 IAP 全渠道归因的冷启动上报。保留 v4.0.6 的 IAA 用户标签、回调和上报行为。

| 下载目录 | index.js 的 SHA-256 |
| --- | --- |
| [微信基础包](./微信基础包) | `07651865309bbc6020215d792428f09d23d3a47bd361100c84a490659be781c4` |
| [微信全量包](./微信全量包) | `c945857df026969642e93314290edf15b900447499538d89ca99f196a145cea8` |

1. 沿用项目现用包型，下载该目录的文件并替换小游戏工程里的 `channelSDK`。
2. 沿用项目已有的 SDK 初始化参数。默认关闭新归因。试点应用完成瑞雪归因配置后，再加 `oceanSignalEnabled: true`。
3. 重新构建微信小游戏。用测试应用验运行版本和登录，冷启动后比对 SDK 请求与瑞雪归因记录。投放同事在巨量工作台核对对应资产上的回执。

```js
const ChannelSDK = require('./channelSDK/index.js')
const sdk = new ChannelSDK({
  ...sdkConfig,
  oceanSignalEnabled: true
})
```

本版在隔离环境通过仓库 Demo、归因专项和 IAA 对照验证。实际游戏联调使用经授权的测试应用和测试订单。 [完整接入指南](https://doc.ruixueyun.com/main/#/view?path=6044c196-dcb3-4ee4-af0f-ce147a50b009) · [上一版微信制品](../v4.0.6)
