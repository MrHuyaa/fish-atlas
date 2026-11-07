# 长江流域淡水鱼图鉴

18 种淡水鱼的图文图鉴：左侧大图配右侧名称、学名、科属与简介，支持左右切换、键盘方向键、底部缩略图预览和点击放大。

图片统一为 1000 × 750，已去除右下角水印，鱼头朝向统一向左。

## 在线访问

<https://mrhuyaa.github.io/fish-atlas/>

> 仓库名使用 ASCII slug `fish-atlas`：GitHub 不支持纯中文仓库名（会被规范化为 `-`）。中文全名保留在网页标题与仓库描述中。

## 本地运行

直接用浏览器打开 `index.html`，无需构建、无需服务器、无外部依赖。

## AMOLED 圆屏版（ESP32）

把同一套 18 种鱼搬上 **ESP32-S3-Touch-AMOLED-1.75** 的 466 × 466 圆屏，做成不联网、开机就能翻的科普小图鉴，给小孩认鱼用。后续会按同一套模板继续做常见鸟类、常见植物、汽车等图鉴。

- [介绍 · 用途 · 后续规划](amoled/readmez.md)
- [技术说明与换图鉴模板](amoled/README.md)
- [下载完整工程包 / 资源镜像（Release v1.0.0）](https://github.com/MrHuyaa/fish-atlas/releases/tag/v1.0.0)

> 完整包（zip 与 LittleFS 镜像）走 Release 附件，仓库只放说明、配置模板与预览图。

## 目录说明

| 路径 | 说明 |
| --- | --- |
| `index.html` | 单文件页面，数据与样式均内联 |
| `assets/` | 18 张 1000 × 750 主图 |
| `assets/thumb/` | 18 张 260 × 195 缩略图 |
| `amoled/` | 圆屏版说明、换图鉴模板与预览图 |
| `pool/` | 原始母版图，体积较大，已在 `.gitignore` 中排除 |
