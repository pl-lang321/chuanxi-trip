# 川西自驾手册 · 发布项目

单文件静态站点：`public/index.html`（零外部依赖，无 CDN、无字体、无地图瓦片，可离线打开）。

## 本地预览

把 `public/index.html` 拖进浏览器即可，或起个静态服务：

```bash
npx wrangler dev           # 需要 Node 18+，会临时下载 wrangler
```

也可以直接双击 index.html —— 离线状态下同样完整可用。

## 发布流程

仓库已配好 `wrangler.toml`，采用 Cloudflare Workers **静态资源托管**（`[assets]`）。
GitHub 仓库连上 Cloudflare Workers Builds 后，每次 push 到 main 分支自动上线，**不需要手动跑任何命令**。

Cloudflare 上的构建配置：

| 配置项 | 值 |
| --- | --- |
| Build command | 留空（本项目没有构建步骤） |
| Deploy command | `npx wrangler deploy`（默认即可） |
| 根目录 | 仓库根目录（不要填 `public`） |

## 修改页面

只改 `public/index.html` 一个文件。改完 `git commit` 并 `git push`，两三分钟后线上自动更新。

注意：页面是**公开**的，任何拿到链接的人都能看到。
确认号、证件号、房间号一律不要写进这个文件。
