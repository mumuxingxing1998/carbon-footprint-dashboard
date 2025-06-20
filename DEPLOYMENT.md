# 部署指南 - GitHub Pages

本指南将帮助你将这个碳足迹分析看板部署到GitHub Pages上。

## 🚀 快速部署步骤

### 1. 创建GitHub仓库

1. 登录GitHub账户
2. 点击右上角的 "+" 号，选择 "New repository"
3. 输入仓库名称，例如：`carbon-emission-dashboard`
4. 选择 "Public" 或 "Private"
5. 不要勾选 "Add a README file"（我们已经有了）
6. 点击 "Create repository"

### 2. 上传文件到GitHub

#### 方法一：使用Git命令行

```bash
# 克隆仓库到本地
git clone https://github.com/你的用户名/carbon-emission-dashboard.git
cd carbon-emission-dashboard

# 复制项目文件到仓库目录
# 确保以下文件在仓库根目录：
# - index.html
# - README.md
# - .gitignore
# - .github/workflows/deploy.yml

# 添加文件到Git
git add .

# 提交更改
git commit -m "Initial commit: Carbon emission dashboard"

# 推送到GitHub
git push origin main
```

#### 方法二：使用GitHub Web界面

1. 在GitHub仓库页面，点击 "uploading an existing file"
2. 拖拽或选择以下文件：
   - `index.html`
   - `README.md`
   - `.gitignore`
   - `.github/workflows/deploy.yml`
3. 添加提交信息：`Initial commit: Carbon emission dashboard`
4. 点击 "Commit changes"

### 3. 启用GitHub Pages

#### 自动部署（推荐）

1. 文件上传后，GitHub Actions会自动运行
2. 等待几分钟，Actions会创建 `gh-pages` 分支
3. 进入仓库设置：Settings → Pages
4. 在 "Source" 部分选择 "Deploy from a branch"
5. 选择 "gh-pages" 分支和 "/ (root)" 文件夹
6. 点击 "Save"

#### 手动部署

如果自动部署不工作：

1. 进入仓库设置：Settings → Pages
2. 在 "Source" 部分选择 "Deploy from a branch"
3. 选择 "main" 分支和 "/ (root)" 文件夹
4. 点击 "Save"

### 4. 访问你的网站

部署完成后，你的网站将在以下地址可用：
```
https://你的用户名.github.io/carbon-emission-dashboard/
```

## 🔧 故障排除

### 常见问题

1. **页面显示空白**
   - 检查浏览器控制台是否有JavaScript错误
   - 确保所有CDN链接都能正常访问
   - 检查 `index.html` 文件是否在仓库根目录

2. **图表不显示**
   - 确认Recharts和React库已正确加载
   - 检查网络连接，确保CDN资源可访问

3. **GitHub Actions失败**
   - 检查 `.github/workflows/deploy.yml` 文件是否正确
   - 确保仓库有适当的权限设置

### 调试步骤

1. **本地测试**
   ```bash
   # 在本地启动简单的HTTP服务器
   python -m http.server 8000
   # 或使用Node.js
   npx serve .
   ```

2. **检查文件结构**
   ```
   carbon-emission-dashboard/
   ├── index.html
   ├── README.md
   ├── .gitignore
   └── .github/
       └── workflows/
           └── deploy.yml
   ```

## 📝 自定义配置

### 修改网站标题和描述

编辑 `index.html` 文件中的 `<title>` 标签和页面内容。

### 更新数据

在 `index.html` 文件中找到 `rawData` 数组，修改或添加项目数据。

### 更改样式

使用Tailwind CSS类名或添加自定义CSS来修改页面样式。

## 🌐 域名设置（可选）

如果你想使用自定义域名：

1. 在仓库设置中：Settings → Pages
2. 在 "Custom domain" 部分输入你的域名
3. 保存设置
4. 在你的域名提供商处设置DNS记录

## 📊 性能优化

- 所有依赖都使用CDN，确保快速加载
- 图片和图标使用优化的格式
- 代码已压缩和优化

## 🔒 安全考虑

- 项目使用公开的CDN资源
- 没有敏感数据或API密钥
- 适合公开分享和展示

---

部署完成后，你的碳足迹分析看板就可以在互联网上访问了！🎉 