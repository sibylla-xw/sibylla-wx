<div align="center">

# 王希 Sibylla Wang — Personal Portfolio

**Travel Tech · Commercialization · AI Innovation**

一个数据驱动、可直接部署到 GitHub Pages 的单页个人作品集网站，全站中英双语对照，用于展示旅游科技与商业化领域的经验、客户案例与持续探索。

[![Live Site](https://img.shields.io/badge/Live%20Site-GitHub%20Pages-2ea44f?style=for-the-badge&logo=github)](https://sibyllawang.github.io/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-sibyllawang-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/sibyllawang/)

</div>

---

## ✨ 特性

- 🎬 **电影感首屏** — 全屏背景视频（个人形象视频）+ 大字体排版，深空科技蓝主题
- 🌐 **全站中英双语** — 所有核心文案中英文对照呈现，专业精英感
- 📄 **精简叙事（7 章）** — 关于我 / 个人档案 / 求职亮点 / 工作经历 / 荣誉证书 / 联系（已删除重复的"个人标签 / 工作方法 / 优势"章节，以及"精选项目"整章）
- 🎨 **深空科技蓝主题** — 电光青蓝强调色 + 深空蓝背景，呼应职业形象照与商务气质；配色在 `site-config.js → theme` 中定义
- 📱 **PC / 手机双端优化** — 移动端导航折叠为汉堡菜单、字段单列铺开、字号与行距针对小屏重新调校，无横向溢出
- 🧹 **精简覆盖层** — `custom.css` 统一处理：隐藏"姓名"占位大字与空毕业院校行、删除简历区照片、荣誉区改为简洁科技感列表（每条配图标、禁用点击弹窗、内容全平铺）、联系方式配内联 SVG 图标、字号缩小 + 章节留白压缩
- ⚙️ **数据驱动** — 所有文案与作品集中在两个 JS 文件，改内容不用碰样式代码
- 🚀 **零构建部署** — 纯静态文件，Push 即上线

---

## 📁 项目结构

```
sibylla-wang-portfolio/
├── index.html                 # 入口页（含 SEO / Open Graph 元信息）
├── site-config.js             # ★ 站点内容配置：主题、文案、履历、联系方式
├── portfolio-data.js          # ★ 作品数据（6 个案例，当前整章隐藏，备查）
├── custom.css                 # ★ 精简覆盖层：清理残留 + 矩形职业照 + 字号缩小 + PC/手机响应式
├── assets/
│   ├── index-*.css            # 样式（构建产物，无需修改）
│   ├── index-*.js             # 渲染逻辑（构建产物，无需修改）
│   └── user-media/            # 作品配图（AI 产品 / APP 截图）
├── default-projects/          # 其余作品配图
├── hero-video.mp4             # 首屏背景视频（你的个人形象视频，H.264）
├── portrait.jpg               # 职业形象照（履历区）
├── wechat-qr.jpg              # 你的微信二维码（联系区悬停显示）
├── contact-topography.png     # 联系区装饰
├── honor-trophy-default.png   # 荣誉区装饰
├── .nojekyll                  # 禁用 Jekyll，确保资源正常加载
└── README.md
```

> 日常只需修改带 ★ 的两个文件，其余为静态资源与构建产物。

---

## ⚙️ 本地预览

任意静态服务器均可，例如：

```bash
# Python 3
python -m http.server 8000
# 然后打开 http://localhost:8000
```

或直接双击 `index.html` 在浏览器打开（部分浏览器对本地视频自动播放有限制，推荐用本地服务器）。

---

## 🚀 部署到 GitHub Pages

1. **新建仓库**：在 GitHub 创建一个名为 `<你的用户名>.github.io` 的仓库（Public）。
   - 例：用户名是 `sibyllawang`，仓库名就是 `sibyllawang.github.io`
   - 这样访问地址就是 `https://sibyllawang.github.io/`
2. **上传文件**：把本目录所有文件（含隐藏的 `.nojekyll`）上传到仓库根目录。
3. **开启 Pages**：仓库 `Settings → Pages → Source` 选择 `Deploy from a branch`，分支选 `main`、目录选 `/ (root)`，保存。
4. **等待部署**：几分钟后访问 `https://<你的用户名>.github.io/` 即可。

也可使用命令行：

```bash
git init
git add .
git commit -m "Initial portfolio commit"
git branch -M main
git remote add origin https://github.com/<你的用户名>/<你的用户名>.github.io.git
git push -u origin main
```

---

## 🔧 如何修改内容

所有内容都在这两个文件里，用编辑器打开即可，是标准的 `key: value` 结构。

### `site-config.js`

| 字段 | 说明 |
|------|------|
| `theme` | 配色：`accent` 强调色、`background` 背景、`surface` 卡片、`text` 文字 |
| `brand.text` | 左上角品牌名 |
| `hero` | 首屏：视频、标题三行、描述、滚动提示 |
| `intro.lines` | "关于我"的滚动叙事，数组每一项是一屏 |
| `resume.profile` | 个人档案表格，`[["字段", "值"], ...]`。按当前设计：已隐藏"姓名"大字行与"毕业院校"行（后者保留空值以阻止模板注入"某某大学"假数据，隐藏规则见 `custom.css`）|
| `resume.folderImages` | 个人照片文件夹动画，当前为 `[]` 空数组（绿色文件夹已删除，改用 `custom.css` 中的简洁矩形职业照）|
| `experience.entries` | 工作经历列表 |
| `work` | 已隐藏（`visibility.work=false`）。6 个项目数据保留在 `portfolio-data.js` 备查，如需恢复改 `visibility.work=true` 即可 |
| `honors.items` | 荣誉与证书 |
| `contact` | **联系方式**：微信、电话、二维码、社交链接 |

### `portfolio-data.js`

每个项目对象的字段：

```js
{
  "number": "01",          // 序号
  "type": "AI AGENT",      // 项目类型标签
  "title": "标题\n副标题",  // \n 换行
  "image": "./...",        // 封面图路径
  "className": "project-wide", // 布局：wide / tall / square / carousel
  "year": "2025",
  "client": "客户名",
  "intro": "项目简介",
  "scope": ["服务项1", "服务项2"],
  "slides": ["./..."],     // 详情页轮播图
  "link": ""               // 项目外链（可选）
}
```

> 修改后刷新浏览器即可看到效果。JS 是标准格式，注意引号与逗号。

---

## 📬 待补充信息（发布前请确认）

当前内容以简历（CN / EN）为基础，并做了开拓创新扩展。以下信息建议本人确认后填入，以获得最佳呈现：

- [x] ~~微信号~~：已填入 `site-config.js → contact.wechat`（`Sibylla Wang`）
- [x] ~~微信二维码~~：已放入根目录 `wechat-qr.jpg` 并配置 `contact.qrCode`（原模板二维码已移除）
- [ ] **微信号精确值**：当前显示名 `Sibylla Wang`，如你希望展示真实微信号（ID），告诉我即可替换
- [x] ~~个人照片~~：已按需求删除简历区照片（绿色文件夹 / 矩形职业照均已移除），`portrait.jpg` 文件保留备用
- [ ] **作品外链**：`portfolio-data.js` 中 `link` 字段，如有线上案例/演示链接可填入
- [ ] **作品配图版权**：`assets/user-media/` 中的图片来自提供的素材，请确认可公开展示
- [ ] **GitHub 用户名**：将 README 与 `index.html` 中的 `sibyllawang` 替换为实际用户名

### 关于首屏视频

✅ **已设置为你的个人形象视频**（黑衣高领 + 青色科技 HUD，约 12 秒），与科技蓝主题高度契合。

你提供的原始视频为 **H.265 / HEVC 编码**，浏览器兼容差，已通过 Windows Media Foundation 转码为全浏览器通用的 **H.264 / AAC（960×540，3.1 MB）**，作为根目录的 `hero-video.mp4`（`site-config.js → hero.video` 指向它）。

- 若日后需从原始 HEVC 视频重新转码，用 ffmpeg：
  ```bash
  ffmpeg -i 原始视频.mp4 -c:v libx264 -pix_fmt yuv420p -vf scale=960:540 -b:v 2200k -c:a aac -movflags +faststart hero-video.mp4
  ```

---

## 📄 License

个人作品集，内容版权归作者所有。模板渲染代码版权归原作者所有。

---

<div align="center">

Built with curiosity, for what's next.

</div>
