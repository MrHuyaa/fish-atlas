# 鱼类图鉴 · AMOLED 圆屏版（`fish-atlas-amoled.zip`）

## 这个压缩包是什么

[`fish-atlas-amoled.zip`](https://github.com/MrHuyaa/fish-atlas/releases/tag/v1.0.0) 是把本站的 18 种淡水鱼图鉴，搬到微雪 **ESP32-S3-Touch-AMOLED-1.75**（工程按 1.75C 配置，466 × 466 圆形 AMOLED）上显示的固件工程包，约 6.95 MB，在 Release 里下载。

网页版是给电脑/手机看的双栏页面，圆屏既放不下也会裁边。这个包的做法是 **电脑端预渲染、设备端只解码显示**：把每张鱼图和文字重新排成 466 × 466 的 JPEG，烧进 Flash，开机直接画到屏幕上。文字已经烤进图片，设备端不需要中文字库、不需要浏览器、不用联网。

| 页面 | 显示内容 |
| --- | --- |
| 默认页 | 圆形大图 + 鱼名压在图片底部 |
| 点按后 | 鱼头小图 + 名称、别名、科属、拉丁名 + 形态介绍全文 |

左右滑动翻页（18 种循环），点按切换两页，BOOT 键可作兜底。纯黑底在 AMOLED 上是真正熄灯的像素，常亮摆着看也省电。

## 用途：给小孩做科普

这套东西是做给小朋友认鱼用的 —— 一台不联网、不用手机、开机就能翻的小屏幕图鉴，摆在桌上或拿在手里，自己滑一滑就能看到鱼的样子和名字，点一下再读简短介绍。

图片沿用网页版的 18 张写实鱼图（1000 × 750，已去水印、鱼头统一朝左），所以屏幕上的内容和 [在线图鉴](https://mrhuyaa.github.io/fish-atlas/) 是一致的。

## 包里有什么

```
fish-atlas-amoled/
├── README.md              工程自带说明（烧录、引脚、改图）
├── fish_atlas/            固件工程：.ino + platformio.ini + partitions.csv
│   └── data/              36 张页面（p01–p18 默认页 / d01–d18 详情页）
├── configs/               _template.json 通用模板 + fish.json 当前 18 条鱼
├── tools/                 render_atlas.py 通用渲染器（配置驱动）
├── assets/fish/           18 张原图
├── data/pages/            36 张页面备份
├── release/               littlefs.bin 资源镜像 + flash.sh / flash.bat 一键烧录
└── preview/               预览图
```

另外 Release 里还有 [`littlefs.bin.zip`](https://github.com/MrHuyaa/fish-atlas/releases/tag/v1.0.0)：单独打包的 8 MB 资源镜像，只想重刷页面时可以只下这个。

## 怎么用到板子上

```bash
cd fish_atlas
pio run -t upload      # 烧固件
pio run -t uploadfs    # 烧 36 张页面资源
```

也可以用包里 `release/flash.bat`（Windows）或 `flash.sh` 一键把固件和资源镜像一起写完。Arduino IDE 方式、引脚核对、分区表等细节见包内 `README.md`。

想调图片大小，改 `configs/fish.json` 里 `card.fill`（当前 0.92，留一圈黑边保证鱼头鱼尾不被切），用 `tools/render_atlas.py` 重新出图后重烧资源即可，固件不用动。

> 注意：工程生成时未在实机上验证过。第一次建议先烧官方 `05_LVGL_Widgets` 确认屏和触摸正常，再烧这个包。

## 后续规划

这套「网页图鉴 → 圆屏预渲染 → JPEG 直绘」的流程是通用的，换一套数据和图片就能做新图鉴，固件基本不用改。接下来准备按同一模板继续做：

| 主题 | 方向 |
| --- | --- |
| 常见鸟类 | 身边能见到的鸟，外形 + 名称 + 习性 |
| 常见植物 | 常见花草树木，配识别特征 |
| 汽车 | 常见车型 / 车标识别 |

目标是把它们做成同一系列、同一套交互的科普小图鉴，孩子拿起来就会用，不用每套重新学操作。新主题主要工作量在整理数据和图片，[通用模板](configs/_template.json)与固件可以直接复用。

---

相关链接：[在线网页版图鉴](https://mrhuyaa.github.io/fish-atlas/) · [技术说明](README.md) · [下载 Release v1.0.0](https://github.com/MrHuyaa/fish-atlas/releases/tag/v1.0.0) · [仓库首页](../README.md)
