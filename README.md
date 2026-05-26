# 帕瓦大人 静态主页快照

这是 Portfolio Library 导出的完整静态站点目录。目录内已经包含主页、样式、脚本、公开数据和媒体副本，可以直接用于静态托管。

## 目录内容

- `index.html`：公开主页入口。
- `styles.css`：主页样式文件。
- `main.js`：主页交互逻辑。
- `data/profile.json`：公开个人信息。
- `data/works.json`：公开作品数据。
- `data/homepage.json`：主页配置。
- `data/tags.json`：标签统计。
- `media/`：公开主页使用的图片、视频、音频和文档副本。
- `publish_report.json`：本地发布检查报告。
- `README.md`：当前说明文件。

## 本地预览

可以直接双击打开 `index.html`。如果浏览器限制本地文件加载，建议在当前目录启动一个本地静态服务器：

```bash
python -m http.server 8000
```

然后在浏览器访问：

```text
http://localhost:8000
```

## 部署前确认

部署时请上传整个目录。`index.html` 需要和 `styles.css`、`main.js`、`data/`、`media/` 保持在同一层级，这样页面样式、作品数据和媒体文件才能正常加载。

如果替换过资产文件，请先在 Portfolio Library 里重新 Generate snapshot，再下载新的 zip 进行部署。

## GitHub Pages：网页上传方式

适合不熟悉 Git 命令的用户。

1. 在 GitHub 新建一个仓库，例如 `my-portfolio-site`。
2. 解压本 zip。
3. 打开仓库页面，点击 `Add file -> Upload files`。
4. 把解压后目录里的所有文件和文件夹拖进去，包括 `index.html`、`styles.css`、`main.js`、`data/`、`media/`、`publish_report.json` 和 `README.md`。
5. 点击 `Commit changes`。
6. 打开仓库的 `Settings -> Pages`。
7. Source 选择 `Deploy from a branch`。
8. Branch 选择 `main`，目录选择 `/root`。
9. 保存后等待 GitHub Pages 构建完成。
10. 打开 GitHub Pages 给出的访问地址。

## GitHub Pages：Git 命令行方式

适合已经安装 Git 的用户。下面命令假设你已经在 GitHub 新建了一个空仓库。

### 第一次发布

进入解压后的静态站点目录，也就是包含 `index.html` 的目录：

```bash
cd path/to/your/unzipped-snapshot
git init
git branch -M main
git add .
git commit -m "Publish portfolio site"
git remote add origin https://github.com/YOUR_NAME/YOUR_REPO.git
git push -u origin main
```

然后到 GitHub 仓库页面打开 `Settings -> Pages`：

```text
Source: Deploy from a branch
Branch: main
Folder: /root
```

保存后等待部署完成。

### 后续更新

以后每次在 Portfolio Library 里重新生成并下载新的 snapshot 后，可以用新的文件覆盖本地站点目录，再运行：

```bash
cd path/to/your/site-folder
git status
git add .
git commit -m "Update portfolio snapshot"
git push
```

如果 `git commit` 提示没有变化，说明这次导出的内容和线上版本相同，可以不用 push。

### 从 GitHub 拉取仓库后更新

```bash
git clone https://github.com/YOUR_NAME/YOUR_REPO.git
cd YOUR_REPO
```

把新 snapshot 解压后的所有文件复制到这个仓库目录，覆盖旧文件，然后执行：

```bash
git add .
git commit -m "Update portfolio snapshot"
git push
```

## Netlify 部署

1. 登录 Netlify。
2. 选择 `Add new site -> Deploy manually`。
3. 解压本 zip。
4. 把整个解压后的目录拖到 Netlify 的上传区域。
5. 不需要构建命令，发布目录就是当前目录。
6. 发布完成后，Netlify 会给出一个可访问的网址。

## Vercel 部署

1. 登录 Vercel。
2. 新建项目并导入包含本快照目录的仓库。
3. Framework Preset 选择 `Other`。
4. Build Command 留空。
5. Output Directory 使用当前目录。
6. 发布后访问 Vercel 生成的网址。

## 普通静态服务器部署

1. 将整个目录上传到服务器的静态网站根目录。
2. 确认服务器可以直接访问 `index.html`。
3. 确认 `data/` 和 `media/` 没有被服务器规则屏蔽。
4. 如果媒体文件无法显示，优先检查目录结构是否完整上传。

## 导出摘要

- 导出作品数：6
- 导出资产数：11
- 警告数：1
- 错误数：0
