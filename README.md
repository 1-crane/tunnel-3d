<div align="center">

# 轨道交通隧道三维可视化系统

**将隧道纹理、病害检测与激光扫描成果组织为可浏览、可定位、可分析的三维巡检场景。**

![Showcase](https://img.shields.io/badge/Repository-Showcase%20Only-111827?style=flat-square)
![Three.js](https://img.shields.io/badge/Three.js-0.152-000000?style=flat-square&logo=threedotjs&logoColor=white)
![Electron](https://img.shields.io/badge/Electron-Desktop-47848F?style=flat-square&logo=electron&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-Web-646CFF?style=flat-square&logo=vite&logoColor=white)

<img src="./assets/images/high-speed-rail-tunnel.png" alt="高铁隧道三维巡检场景" width="100%">

</div>

> [!IMPORTANT]
> 本仓库仅用于产品与技术成果展示，不提供源代码、安装包或原始工程数据。

## 项目概览

隧道巡检数据通常分散在纹理影像、病害 JSON、断面扫描和轨道结构等不同来源中，数据命名、空间基准与粒度也并不一致。本系统先将矿山法隧道、盾构法隧道与激光扫描项目归一为统一数据集，再通过 Three.js 构建连续的隧道场景，让巡检人员能够沿里程浏览内壁纹理、查看病害位置与详情，并结合收敛曲线和里程跳转完成快速复核。

它既可以在浏览器环境中运行，也可以封装为 Electron 桌面客户端。工程重点不只是“把隧道画出来”，而是让长距离、高分辨率纹理和密集标注在交互过程中保持可管理、可定位和可扩展。

## 动态演示

<p align="center">
  <img src="./assets/gifs/straight-tour.gif" alt="直线隧道自动漫游" width="760">
</p>
<p align="center"><sub>直线隧道自动漫游</sub></p>

<p align="center">
  <img src="./assets/gifs/curved-tour.gif" alt="曲线隧道连续漫游" width="760">
</p>
<p align="center"><sub>曲线隧道连续漫游</sub></p>

<p align="center">
  <img src="./assets/gifs/shield-tour.gif" alt="盾构隧道与病害标注浏览" width="760">
</p>
<p align="center"><sub>盾构隧道与病害标注浏览</sub></p>

<p align="center">
  <img src="./assets/gifs/disease-inspection.gif" alt="病害近距离检查与路径展示" width="760">
</p>
<p align="center"><sub>病害近距离检查与路径展示</sub></p>

## 核心能力

### 1. 多源数据统一接入

一键式导入、多源兼容：面向标准数据集、矿山法、盾构法和激光扫描数据提供统一入口，自动完成纹理、里程、环号、断面与病害信息解析，并直接进入三维场景，实现常规展示数据的秒级重建体验。

<p align="center">
  <img src="./assets/screenshots/import-home.png" alt="多源数据导入首页" width="760">
</p>
<p align="center"><sub>统一导入入口：选择已有数据集或进入对应生成流程</sub></p>

<details>
  <summary><strong>01 · 矿山法数据生成</strong>　从壁面纹理与病害数据生成标准化隧道数据</summary>
  <p align="center">
    <img src="./assets/screenshots/mine-import-form.png" alt="矿山法数据生成表单" width="760">
  </p>
</details>

<details>
  <summary><strong>02 · 盾构法数据生成</strong>　兼容盾构纹理、道床纹理与病害检测结果</summary>
  <p align="center">
    <img src="./assets/screenshots/shield-import-form.png" alt="盾构法数据生成表单" width="760">
  </p>
</details>

<details>
  <summary><strong>03 · 激光扫描数据导入</strong>　解析 TLS-D 项目并读取 slice、image、track 数据</summary>
  <p align="center">
    <img src="./assets/screenshots/laser-import-form.png" alt="激光扫描数据导入表单" width="760">
  </p>
</details>

### 2. 多类型隧道场景重建

系统根据直径、分段长度、里程和壁面纹理重建隧道内壁、轨道或道床，兼容直线与曲线场景，在统一渲染框架下保留不同数据来源的结构与纹理特征。

<p align="center">
  <img src="./assets/images/research-tunnel.png" alt="国自然基金实验场景" width="760">
</p>
<p align="center"><sub>国自然基金实验</sub></p>

<p align="center">
  <img src="./assets/images/high-speed-rail-tunnel.png" alt="高铁隧道场景" width="760">
</p>
<p align="center"><sub>高铁隧道</sub></p>

<p align="center">
  <img src="./assets/images/shield-tunnel.png" alt="盾构隧道场景" width="760">
</p>
<p align="center"><sub>盾构隧道</sub></p>

<p align="center">
  <img src="./assets/images/laser-scan-tunnel.png" alt="激光扫描隧道场景" width="760">
</p>
<p align="center"><sub>激光扫描隧道</sub></p>

### 3. 病害空间映射与复核

病害适配层将不同来源的裂缝、渗漏水、混凝土浇筑缝等记录统一到里程与管片局部坐标系，再生成可拾取的标注和路径。点击标注可查看病害类型、环号、起止里程、长度或面积；当前环的病害列表也可以集中展开，支持从“全局巡检”下钻到“单条复核”。

<p align="center">
  <img src="./assets/screenshots/disease-detail.png" alt="单条病害详情" width="760">
</p>

### 4. 里程导航与状态分析

浏览过程中，信息面板持续同步当前里程、环号与结构状态；小地图支持选点和里程跳转；收敛曲线则按环展示变形趋势。视图菜单还可以调节漫游速度、前进灵敏度、亮度、纹理对比度、雾化与病害标注强度。

<p align="center">
  <img src="./assets/screenshots/convergence-chart.png" alt="收敛变形趋势曲线" width="760">
</p>
<p align="center"><sub>收敛变形趋势曲线</sub></p>

<p align="center">
  <img src="./assets/screenshots/viewer-overview.png" alt="三维场景与里程导航" width="760">
</p>
<p align="center"><sub>三维场景与里程导航</sub></p>

## 数据管线

<table>
  <thead>
    <tr>
      <th>阶段</th>
      <th>输入 / 处理</th>
      <th>阶段产物</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>01 · 数据接入</strong></td>
      <td>壁面与道床纹理、病害检测 JSON、TLS-D 项目与 RLS 断面</td>
      <td>多源原始数据</td>
    </tr>
    <tr>
      <td><strong>02 · 适配解析</strong></td>
      <td>识别纹理命名、里程区间、环号、断面和病害坐标</td>
      <td>结构化中间数据</td>
    </tr>
    <tr>
      <td><strong>03 · 标准化</strong></td>
      <td>统一空间基准与字段，完成数据完整性校验</td>
      <td><code>profile</code> / <code>segments</code> / <code>diseases</code></td>
    </tr>
    <tr>
      <td><strong>04 · 三维呈现</strong></td>
      <td>按里程组织场景，加载纹理、病害标注和分析组件</td>
      <td>可漫游、可定位、可分析的隧道场景</td>
    </tr>
  </tbody>
</table>

标准数据集以四个文件为边界，便于导入、渲染和后续分析模块独立演进：

```text
dataset/
├── profile.json                 # 隧道直径、分段方式、数据来源等全局配置
├── segments.json                # 环/分段、里程、纹理引用与收敛量
├── diseases.normalized.json     # 标准化病害、尺寸、里程与坐标点
└── import-report.json           # 解析结果、统计信息与数据质量警告
```

## 项目亮点

这是一个面向轨道交通巡检场景的完整三维可视化项目，重点体现数据工程、三维渲染与交互产品化能力：

- **一键式工作流**：从原始数据导入、标准化处理到三维展示形成连续链路。
- **多源兼容**：统一适配矿山法、盾构法、高铁隧道和激光扫描成果。
- **秒级重建体验**：通过预处理、分段组织和渐进式纹理加载，快速进入可浏览状态。
- **沉浸式巡检**：支持自动漫游、里程跳转、病害拾取、路径标注和收敛趋势分析。
- **工程化交付**：同一套前端能力覆盖 Web 与 Electron 桌面端，具备持续扩展基础。

## 交互闭环

```text
选择或生成数据集
        ↓
解析并校验统一数据契约
        ↓
按相机里程挂载当前窗口
        ↓
低精度快速可见 → 高精度渐进替换
        ↓
漫游 / 小地图跳转 / 病害点击 / 收敛趋势复核
        ↓
切换数据集或释放当前场景资源
```

## 技术栈

| 层级 | 技术 | 用途 |
| --- | --- | --- |
| 三维渲染 | Three.js 0.152 | 场景、相机、隧道几何、纹理、标注拾取与宽线病害路径 |
| 应用构建 | Vite 8 | Web 开发与生产构建 |
| 桌面运行时 | Electron 35 | 本地文件选择、IPC、文件桥接与桌面分发 |
| 桌面更新 | electron-updater 6 | 更新检查、下载进度与安装状态管理 |
| 界面样式 | Tailwind CSS 3 + 原生 CSS | 导入界面、控制面板与响应式布局 |
| 数据处理 | Node.js ES Modules | 矿山法、盾构法与 TLS-D 数据解析及标准化 |

## 展示仓库结构

```text
.
├── README.md
└── assets/
    ├── images/          # 典型隧道场景
    ├── gifs/            # 漫游与病害交互演示
    └── screenshots/     # 导入、分析与控制界面
```

## 展示边界

- 本仓库不是开源发行版，不包含源码、依赖清单、构建脚本、安装包或可运行数据集。
- 截图中的示例数据仅用于说明交互流程，不代表真实线路的当前检测结论。

---

<div align="center">

**让分散的隧道巡检数据，进入同一条可浏览、可定位、可分析的三维链路。**

</div>
