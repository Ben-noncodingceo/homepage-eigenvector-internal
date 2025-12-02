# Cloudflare Pages 部署配置说明

此文件包含 Cloudflare Pages 的构建配置信息。

## 构建配置

如果您在 Cloudflare Dashboard 中手动配置，请使用以下设置：

- **框架预设**: Jekyll
- **构建命令**: `bundle exec jekyll build`
- **构建输出目录**: `_site`
- **根目录**: `/`（留空）
- **环境变量**: 
  - `JEKYLL_ENV`: `production`
  - `RUBY_VERSION`: `3.1`

## Ruby 版本

建议使用 Ruby 3.1 或更高版本。

