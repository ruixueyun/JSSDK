# 微信小游戏 SDK v4.0.8

2026-11-27

适用包型为微信基础包和微信全量包。新版首次调用 `getUserLabel` 时才加载微信 IAA 插件 `MiniGameCommon`，成功后复用。已有 `initIAAPlugin()` 显式初始化调用可继续使用。

## 下载与换包

1. 选择项目原有包型，下载同一文件夹里的 `index.js` 和 `tencent-sdk.js`，完整替换工程 `channelSDK` 中对应的 SDK 文件。重新构建后确认实际加载版本为 `4.0.8`。
2. 只接巨量 IAP 归因时，保留原有初始化和登录、支付调用。试点已获准开通的项目继续使用 `oceanSignalEnabled: true`，启动无需注册 IAA 插件。
3. 同时使用 IAA 用户标签时，保留小游戏 `game.json` 顶层的 `plugins.MiniGameCommon` 声明和当前 AppID 的插件授权，保持现有 `getUserLabel(params, callback)` 调用。实际使用 IAA 时如果加载失败，查询回调仍返回 `code: 9000`。
4. 用微信真机冷启动并登录。纯 IAP 检查 SDK 初始化和登录成功、启动时无 IAA 插件告警、归因请求已发出。瑞雪配置生效后核对 `queued: true`、测试付费与巨量回执。同时接 IAA 的项目再核对首次标签查询成功以及后续上报。

[巨量 IAP 快速接入](https://doc.ruixueyun.com/main/#/view?path=6044c196-dcb3-4ee4-af0f-ce147a50b009) · [IAA 插件申请、配置与使用](https://doc.ruixueyun.com/main/#/view?path=c9eac907-d906-4d18-b9b3-8dda5491b371)

## 文件校验

| 文件 | 字节 | SHA-256 |
| --- | ---: | --- |
| [微信基础包/index.js](./微信基础包/index.js) | 170,444 | `2871f8802f0cfa4d77de0b995f607f98b28ca148be9f5a578a53a569314fc042` |
| [微信基础包/tencent-sdk.js](./微信基础包/tencent-sdk.js) | 63,756 | `01b40ac17a9dc054eb222246db2faff46460bbdf3c5a2a3a1bad0d091b9ffbf6` |
| [微信全量包/index.js](./微信全量包/index.js) | 191,619 | `9eba392660cf0dd22ef1af79ad5133e7e7f976066243a413ad6d274c32d6b116` |
| [微信全量包/tencent-sdk.js](./微信全量包/tencent-sdk.js) | 63,756 | `01b40ac17a9dc054eb222246db2faff46460bbdf3c5a2a3a1bad0d091b9ffbf6` |

[构建源码与回归用例](https://git.jiaxianghudong.com/rx-frontend/Rxsdkv3/-/commit/96dcd5b2da478693785430bc96f160e6984a11da)。采用 v4.0.7 正式微信包的构建源码和锁文件。两个包型通过了隔离环境的初始化、登录、归因、IAA 查询与失败回调检查。真机与真实媒体回执按试点联调。
