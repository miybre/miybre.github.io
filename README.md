# 个人主页

一个纯静态的单页个人主页 / 简历站点，无框架、无构建步骤，直接托管在 GitHub Pages。

## 结构

```
personal-site/
├── index.html          页面结构与全部文字内容
├── assets/
│   ├── style.css       样式（配色、排版、响应式、打印）
│   └── main.js         主题切换、滚动动效、导航高亮
├── .nojekyll           告诉 GitHub Pages 不要走 Jekyll 构建
└── README.md
```

## 本地预览

直接双击 `index.html` 即可，或者起一个本地服务：

```bash
python -m http.server 8000
# 打开 http://localhost:8000
```

## 换成你自己的内容

所有文字都在 `index.html` 里，按注释分段，逐段替换即可：

| 位置 | 需要改什么 |
| --- | --- |
| `<head>` 里的 `<title>`、`<meta description>` | 你的名字和一句话介绍 |
| favicon 里的 `%E9%99%88` | 你的姓氏（URL 编码后的一个汉字） |
| `.nav__brand` | 导航栏的名字和首字母方块 |
| `.hero` | 大标题、自我介绍、求职方向 / 城市 / 可入职时间 |
| `#about` | 关于我：三段话，写你的起点、做过什么、想找什么 |
| `#education` | 学校、专业、时间、GPA、排名、课程与荣誉 |
| `#skills` | 三组技能标签，按你的实际情况增删 `<li>` |
| `#projects` | 项目卡片，建议每个项目写 1 段描述 + 2 条量化成果 |
| `#experience` | 时间线，实习 / 社团 / 开源都放这里 |
| `#contact` | 邮箱、GitHub、微信 |

`assets/main.js` 顶部的 `STORAGE_KEY = 'cm-theme'` 里的 `cm` 可以换成你名字的缩写（只是本地存储键名，改不改都行）。

## 换配色

`assets/style.css` 最上面的 `:root` 集中了所有颜色变量，改 `--accent` 就能整体换主色：

- 墨绿 `#10695c`（默认）
- 靛蓝 `#2c4a9a`
- 砖红 `#b4472a`
- 石墨 `#3d4148`

深色模式的对应色在 `[data-theme="dark"]` 里，改 `--accent` 时记得一起改。

## 导出 PDF 简历

点首屏的「下载简历 PDF」，浏览器会调用打印对话框，选择「另存为 PDF」。
打印样式已经单独适配：隐藏导航和按钮、强制展开所有内容、按区块避免分页断裂。

## 部署到 GitHub Pages

```bash
git init
git add .
git commit -m "init: personal site"
git branch -M main
git remote add origin git@github.com:<你的用户名>/<仓库名>.git
git push -u origin main
```

推送后在仓库的 **Settings → Pages** 里，Source 选择 `Deploy from a branch`，分支选 `main`、目录选 `/ (root)`，保存。
等一两分钟，访问 `https://<你的用户名>.github.io/<仓库名>/`。

如果仓库名就叫 `<你的用户名>.github.io`，地址会是 `https://<你的用户名>.github.io/`，不带子路径。
