# AI Canvas 接入说明

这是我们原创的独立API素材示例与接入契约，不是原项目官方Provider，契约JSON也不是已验证可直接导入的上游设置文件。真实API出图/出片与产品内验收分开记录。

上游固定SHA：2a5dc6632ce8af58dcaf3d69530d5fc032f29f29

- [src/services/ai/mediaProviderRegistry.ts](https://github.com/Tenney95/AI-Canvas-tauri/blob/2a5dc6632ce8af58dcaf3d69530d5fc032f29f29/src/services/ai/mediaProviderRegistry.ts)
- [src/services/ai/providers/standardImage.ts](https://github.com/Tenney95/AI-Canvas-tauri/blob/2a5dc6632ce8af58dcaf3d69530d5fc032f29f29/src/services/ai/providers/standardImage.ts)
- [src/services/ai/generateVideo.ts](https://github.com/Tenney95/AI-Canvas-tauri/blob/2a5dc6632ce8af58dcaf3d69530d5fc032f29f29/src/services/ai/generateVideo.ts)

图片：Bearer鉴权，提交一次并保存id，轮询对应图片generations/{id}，从result.data[0].url下载。不同模型的resolution在顶层或metadata内，不能只改Base URL。

视频：MiniMax-H3，5秒/768p，image_with_roles首帧，单独的videos/generations提交/查询链路。返回id不等于视频成功；需要完成态、可播放文件和实际消费确认。

接入后检查：模型目录与选项 → 提交/防重复 → 重启恢复查询 → 保存原始图片或视频 → 原界面导入和展示 → 费用核对。现阶段完整原生界面未验收。
