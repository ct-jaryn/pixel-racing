# 像素赛车 (Pixel Racing)

> 一款基于 Three.js 的像素风俯视视角弯道竞速小游戏：在 4 车道弯道上狂飙，躲避车流、电瓶车与行人，氮气加速、近距超车，挑战最高得分。

![Three.js](https://img.shields.io/badge/Three.js-0.160.0-000000?logo=three.js&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-Canvas%20%2F%20WebGL-E34F26?logo=html5&logoColor=white)
![Web%20Audio](https://img.shields.io/badge/Web%20Audio-API-FF6F00)
![Build](https://img.shields.io/badge/Build-无需构建-brightgreen)

## 🎮 游戏简介

《像素赛车》是一款纯前端实现的俯视视角无限竞速游戏。你驾驶一辆赛车行驶在一条无尽延伸的弯曲公路上，需要在 4 条车道间穿梭，躲避迎面而来的轿车、公交、卡车与货车，还要小心非机动车道上的电瓶车和人行道上的行人。车速越快得分倍率越高，贴身超车还有额外奖励——撞到行人则直接出局。活下去，跑得越远、越快，得分越高！

## ✨ 功能特性

- **弯道公路**：道路由正弦曲线实时弯曲生成，车道线、护栏、路灯等全部贴合弯道走向
- **多种敌方车辆**：轿车 / 公交 / 卡车 / 货车 4 种车型精灵图，运行时自动洪泛填充去除白边背景，难度随得分提升（刷车更快、更密集）
- **生命值系统**：5 颗爱心血量，撞车 / 撞电瓶车扣 1 HP 并附带短暂无敌闪烁、屏幕震动与红色受击闪光；**撞到行人直接游戏结束**
- **氮气加速**：按住 Shift 消耗氮气条冲刺（+60 极速），伴随粒子尾焰、FOV 拉伸与音效，松开缓慢回充
- **计分机制**：里程持续计分，时速 >180 km/h 得分 ×1.5、>250 km/h 得分 ×2.0；近距超车 +50 分，拾取绿色十字血包 +1 HP 并 +30 分
- **丰富路侧场景**：程序化生成的树木、房屋、广告牌、路牌、护栏、路灯、漂移云朵与速度线特效
- **程序化像素纹理**：路面、草地、车辆、行人、电瓶车等纹理全部由 Canvas 2D 逐像素绘制（NearestFilter 采样保持像素风）
- **Web Audio 合成音效**：无需任何音频文件，引擎轰鸣随速度变调，碰撞 / 氮气 / 拾取均有合成音效
- **完整 HUD**：时速 / 得分 / 里程三栏仪表、速度表、车道指示器、氮气条、血条，开局 3-2-1-GO 倒计时
- **移动端适配**：响应式布局 + 屏幕虚拟按键（左 / 刹车 / 右），触屏即玩

## 🕹️ 操作说明

### 键盘

| 按键 | 功能 |
| --- | --- |
| `空格` / 鼠标点击 | 开始游戏 / 重新开始 |
| `W` / `↑` | 加速 |
| `S` / `↓` | 刹车 |
| `A` / `←` | 向左转向 |
| `D` / `→` | 向右转向 |
| `Shift`（按住） | 氮气加速 |

### 触屏 / 移动端

- 点击屏幕：开始游戏；对局中点击为短暂加速
- 屏幕底部虚拟按键：`◀` 左转、`刹车`、`▶` 右转

## 🛠️ 技术栈

- **渲染**：[Three.js 0.160.0](https://threejs.org/)（CDN 引入，WebGL，ACESFilmic 色调映射）
- **语言**：原生 HTML5 / CSS3 / JavaScript（ES6+，单文件实现，零框架）
- **纹理**：Canvas 2D 程序化像素纹理 + PNG 精灵图（运行时去白底）
- **音频**：Web Audio API 振荡器实时合成
- **构建**：无构建工具、无 npm 依赖，纯静态站点

## 🚀 快速开始

本项目为纯静态页面，无需安装任何依赖。但由于游戏通过 `THREE.TextureLoader` 加载本地精灵图，需通过 HTTP 服务访问（直接双击 `index.html` 以 `file://` 打开会导致贴图跨域加载失败）。

### 方式一：Python（任选其一）

```bash
cd games/pixel-racing
python -m http.server 8000
```

### 方式二：Node.js

```bash
cd games/pixel-racing
npx serve .
# 或
npx http-server -p 8000
```

启动后在浏览器打开 `http://localhost:8000` 即可开始游戏。

### 部署

整个目录即为成品，将 `index.html` 与 `assets/` 原样上传到任意静态托管（GitHub Pages、Vercel、Nginx 等）即可。

## 📁 项目结构

```
pixel-racing/
├── index.html          # 游戏本体：样式 + HUD + 全部游戏逻辑（约 2300 行单文件）
├── assets/             # 车辆精灵图素材
│   ├── carside.png     # 车侧贴图（运行时重着色）
│   ├── car_sports.png  # 敌方轿车
│   ├── car_bus.png     # 敌方公交
│   ├── car_truck.png   # 敌方卡车
│   ├── car_van.png     # 敌方货车
│   └── ...             # 其他备用素材
└── README.md
```

## 📜 License

暂未指定。
