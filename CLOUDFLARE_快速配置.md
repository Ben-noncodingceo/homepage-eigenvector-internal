# Cloudflare Pages 快速配置指南

> **重要说明**：此网站为**即未科技/质心教育**（Center of Mass Education Tech.）内部培训、测试、分享使用。

## ✅ 项目已创建

您的 Cloudflare Pages 项目已经创建，项目名称：`homepage-eigenvector-internal`

## 🚀 配置步骤（两种方式任选其一）

---

## 方式一：使用 Cloudflare Dashboard 自动部署（推荐，最简单）

如果您已经在 Cloudflare Dashboard 中创建了项目并连接了 GitHub，只需要确保构建设置正确即可。

### 检查构建设置

1. 登录 Cloudflare Dashboard：https://dash.cloudflare.com/
2. 进入 **Workers & Pages** → 找到项目 `homepage-eigenvector-internal`
3. 点击项目进入详情页
4. 点击 **Settings**（设置）标签
5. 点击 **Builds & deployments**（构建和部署）

### 确认以下设置

确保以下设置正确：

- **Framework preset**: `Jekyll`
- **Build command**: `bundle exec jekyll build`
- **Build output directory**: `_site`
- **Root directory**: 留空（使用 `/`）

### 环境变量（可选但推荐）

在 **Environment variables**（环境变量）部分，添加：

1. **Variable name**: `JEKYLL_ENV`
   **Value**: `production`

2. **Variable name**: `RUBY_VERSION`
   **Value**: `3.1`

### 保存设置

点击 **Save**（保存）按钮。

### 触发首次部署

1. 返回项目主页
2. 点击 **Deployments**（部署）标签
3. 点击 **Retry deployment**（重新部署）或等待自动触发

**完成！** 现在每次您推送代码到 GitHub，Cloudflare 会自动部署。

---

## 方式二：使用 GitHub Actions（高级，可选）

如果您想使用 GitHub Actions 进行更精细的控制，需要配置以下 Secrets。

### 步骤 1：获取 Cloudflare API Token

1. 登录 Cloudflare Dashboard
2. 点击右上角用户图标 → **My Profile**
3. 点击 **API Tokens** 标签
4. 点击 **Create Token**
5. 使用 **Edit Cloudflare Workers** 模板
6. 设置权限：
   - **Account** → **Cloudflare Pages** → **Edit**
7. 点击 **Continue to summary** → **Create Token**
8. **重要**：复制 Token（只显示一次）

### 步骤 2：获取 Account ID

1. 在 Cloudflare Dashboard 右侧边栏找到 **Account ID**
2. 复制这个 ID

### 步骤 3：在 GitHub 仓库中添加 Secrets

1. 打开 GitHub 仓库：https://github.com/Ben-noncodingceo/homepage-eigenvector-internal
2. 点击 **Settings**（设置）
3. 左侧菜单：**Secrets and variables** → **Actions**
4. 点击 **New repository secret** 添加：

**Secret 1:**
- **Name**: `CLOUDFLARE_API_TOKEN`
- **Value**: 粘贴步骤 1 中复制的 Token

**Secret 2:**
- **Name**: `CLOUDFLARE_ACCOUNT_ID`
- **Value**: 粘贴步骤 2 中复制的 Account ID

### 步骤 4：验证部署

1. 推送任何更改到 `master` 分支
2. 在 GitHub 仓库中，点击 **Actions** 标签
3. 查看工作流运行状态
4. 部署成功后，在 Cloudflare Dashboard 中查看部署

---

## 📍 您的网站地址

部署成功后，您的网站地址应该是：
- `https://homepage-eigenvector-internal.pages.dev`

您可以在 Cloudflare Dashboard 的项目页面找到这个地址。

---

## ✅ 验证部署

### 检查部署状态

1. 在 Cloudflare Dashboard 中，进入项目 `homepage-eigenvector-internal`
2. 点击 **Deployments** 标签
3. 绿色 ✅ 表示成功，红色 ❌ 表示失败

### 测试网站

1. 访问：https://homepage-eigenvector-internal.pages.dev
2. 检查网站是否正常显示
3. 测试右上角的语言切换功能

---

## 🔄 自动部署说明

配置完成后，以下操作会自动触发部署：

- ✅ 推送到 `master` 或 `main` 分支
- ✅ 创建 Pull Request（会创建预览部署）
- ✅ 合并 Pull Request

**您不需要手动操作，一切自动完成！** ✨

---

## ❓ 常见问题

### Q: 部署失败了怎么办？
**A**: 
1. 在 Cloudflare Dashboard 中点击失败的部署
2. 查看构建日志（Build logs）
3. 检查构建设置是否正确
4. 确保 `Gemfile` 文件存在

### Q: 网站没有更新？
**A**: 
1. 确认代码已推送到 GitHub
2. 在 Cloudflare Dashboard 中检查是否有新的部署
3. 等待 1-2 分钟让部署完成
4. 清除浏览器缓存后刷新页面

### Q: 如何查看部署日志？
**A**: 
1. Cloudflare Dashboard → 项目 → **Deployments**
2. 点击任意部署查看详细日志

---

## 🎉 完成！

现在您的网站已经配置好自动部署了。每次您推送代码到 GitHub，Cloudflare 会自动构建并部署您的网站。

**祝您使用愉快！** 🚀

