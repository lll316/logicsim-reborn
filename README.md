# LogicSim Reborn — 逻辑模拟器

一个基于 **逆波兰逻辑表达式** 的纯静态逻辑电路模拟器。输入逆波兰逻辑表达式，一键解析并自动渲染为规范的逻辑电路图，支持缩放、平移、节点编辑与文件存取。

本项目为纯静态站点，无需构建工具，可直接在浏览器中运行。

---

## ✨ 功能特性

- **逆波兰表达式解析**：支持五种逻辑运算符
  - `.`：逻辑与（AND）
  - `,`：逻辑或（OR）
  - `<`：逻辑非（NOT）
  - `>`：逻辑推出（蕴含，IMPLICATION）
  - `=`：逻辑等价 / 同或（EQUIVALENCE）
- **自动出图**：将表达式解析为 JSON 模型，并自动布局生成规范逻辑电路图
- **图形交互**：
  - 画布缩放（滚轮 / 快捷键）
  - 画布平移与导航
  - 小地图（Minimap）概览与定位
  - 节点选中、重命名、备注编辑
- **文件操作**：
  - 载入 / 保存文本
  - JSON 模型与图形双向转换（文本转图 / 图转文本）
- **现代 UI**：基于 Tailwind CSS 的卡片式布局，简洁美观

---

## 🚀 运行方式

本程序为纯静态站点，**无需 `npm install` / `npm build`**，有以下几种运行方式：

### 方式一：直接打开（推荐本地调试）

```bash
git clone <仓库地址> logicsim
cd logicsim/public
```

直接双击打开 `public/index.html` 即可在浏览器中运行。

### 方式二：本地启动 HTTP 服务

在项目根目录执行以下命令，启动一个简单的本地静态服务器：

```bash
python -m http.server 8000
```

然后浏览器访问：

```
http://localhost:8000/public/
```

### 方式三：在线访问（GitHub Pages 部署）

本项目已部署为 **GitHub Pages** 静态站点，线上访问地址：

```
https://lll316.github.io/logicsim-reborn/
```

项目源码仓库：

```
https://github.com/lll316/logicsim-reborn
```

> 部署方式：在仓库 **Settings → Pages** 中选择 **Deploy from a branch**，分支选 `main`，目录选 `/public`（⚠️ `index.html` 位于 `public/` 子目录，不可选 `/ (root)`）。

---

## 🧮 使用说明

1. 在顶部「输入区」文本框内输入**逆波兰逻辑表达式**；
2. 点击 **「解析文本」**，将表达式解析并转换为适合图形表示的 JSON 模型；
3. 点击 **「文本转图」**，渲染生成最终的规范逻辑电路图。

### 表达式规则

**五种逻辑运算符**

| 运算符 | 含义 | 写法示例 |
|--------|------|----------|
| `.` | 逻辑与 | `a b .`（a 与 b） |
| `,` | 逻辑或 | `a b ,`（a 或 b） |
| `<` | 逻辑非 | `a <`（非 a） |
| `>` | 逻辑推出 | `a b >`（a 推出 b） |
| `=` | 逻辑等价/同或 | `a b =`（a 等价于 b） |

**组合示例**

- `a b . fe >` 即代表逻辑表达式：**a 与 b 推出了 fe**
- `a b . fe ge > =` 即代表逻辑表达式：**a 与 b 等价于 fe 推出了 ge**

---

## 🗂 项目结构

```
.
├── public/                 # 静态站点根目录（部署目录）
│   ├── index.html          # 入口页面（Tailwind CSS 重构）
│   ├── style.css           # 布局样式
│   ├── LogicParser.js      # 逆波兰表达式 → 逻辑真值表模型
│   ├── ViewGen.js          # 模型 → JointJS 图形渲染
│   ├── latch.json          # 示例模型文件
│   ├── assets/             # 图标与 SVG 资源
│   └── lib/                # 第三方依赖（JointJS、jQuery 等）
├── README.md
└── .gitlab-ci.yml
```

---

## 🛠 技术栈

- **JointJS** — 图形 / 画布渲染
- **jQuery / Lodash / Backbone** — 交互与基础工具
- **Dagre** — 有向图自动布局
- **Select2** — 搜索选择控件
- **Tailwind CSS** — 现代 UI 样式

---

## 📄 License

© LogicSim Reborn. 仅供学习交流使用。