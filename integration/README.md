# AI Canvas integration notes

This is an independent API asset example and integration contract. It is not an official upstream provider, and the contract JSON is not a validated upstream settings import. API output validation is separate from in-app acceptance.

Pinned upstream SHA: 2a5dc6632ce8af58dcaf3d69530d5fc032f29f29

- [src/services/ai/mediaProviderRegistry.ts](https://github.com/Tenney95/AI-Canvas-tauri/blob/2a5dc6632ce8af58dcaf3d69530d5fc032f29f29/src/services/ai/mediaProviderRegistry.ts)
- [src/services/ai/providers/standardImage.ts](https://github.com/Tenney95/AI-Canvas-tauri/blob/2a5dc6632ce8af58dcaf3d69530d5fc032f29f29/src/services/ai/providers/standardImage.ts)
- [src/services/ai/generateVideo.ts](https://github.com/Tenney95/AI-Canvas-tauri/blob/2a5dc6632ce8af58dcaf3d69530d5fc032f29f29/src/services/ai/generateVideo.ts)

Images: authenticate with Bearer, submit once and persist the id, poll the image generations/{id} route, and download result.data[0].url. Resolution fields differ by model; changing Base URL alone is insufficient.

Video: MiniMax-H3, 5s/768p, first frame via image_with_roles, separate videos/generations submit/poll routes. A task id alone is not a successful clip: validate completion, a playable file, and settled billing.

In-app checklist: model selection → duplicate-safe submission → task recovery → save originals → import/display in the original UI → reconcile billing. Full upstream UI acceptance remains pending.
