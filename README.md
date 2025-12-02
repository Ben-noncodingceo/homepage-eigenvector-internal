# 个人网站搭建指南

> **重要说明**：此网站为**即未科技/质心教育**（Center of Mass Education Tech.）内部培训、测试、分享使用。

### 展示您的软件开发技能

本仓库提供了搭建个人网站所需的代码，用于展示您作为软件开发者的工作成果。当您在 GitHub 仓库中管理代码时，网站会自动渲染仓库所有者的个人资料信息，包括照片、简介和仓库列表。

您的个人网站等待个性化定制。它包含空间来突出您在软件开发中的特定兴趣领域，如编程语言或行业。同时，它也准备好发布您的下一篇精彩博客文章。

这一切都通过 [Jekyll](https://jekyllrb.com/docs/)（用于构建网站）、[GitHub Pages](https://pages.github.com/)（用于托管网站）和 [GitHub API](https://developer.github.com/v3/)（用于自动填充网站内容）的组合来实现。

![](https://user-images.githubusercontent.com/221550/110506678-51906280-80cd-11eb-803a-c41984bd9312.png)

## 安装

### Fork `github/personal-website` 仓库

您需要创建"个人网站启动器"仓库的副本，以便拥有自己的项目进行定制。"Fork"就是仓库的副本。请在 [the `github/personal-website` repository](https://github.com/github/personal-website) 页面顶部选择"Fork"。

一旦您为 fork 的仓库找到了位置，它就是您的了。您是所有者，如果愿意，可以随时发布。

### 在本地开发环境中安装

如果您想在本地 Web 开发环境中管理网站，需要使用 [Ruby](https://jekyllrb.com/docs/installation/)。

一旦您为 fork 的仓库找到了位置，**[克隆它](https://help.github.com/articles/cloning-a-repository/)**。

#### 安装 Jekyll

Jekyll 是一个可以在大多数系统上安装的 [Ruby Gem](https://jekyllrb.com/docs/ruby-101/#gems)。

1. 安装完整的 [Ruby 开发环境](https://jekyllrb.com/docs/installation/)
2. 安装 Jekyll 和 [bundler](https://jekyllrb.com/docs/ruby-101/#bundler) [gems](https://jekyllrb.com/docs/ruby-101/#gems)
```
gem install jekyll bundler
```
3. 切换到新目录
```
cd personal-website
```
4. 安装缺失的 gems
```
bundle install
```
5. 构建网站并在本地服务器上运行
```
bundle exec jekyll serve
```

您应该看到类似以下的内容：

```
Configuration file: /octocat/personal-website/_config.yml
            Source: /octocat/personal-website
       Destination: /octocat/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
                    done in 14.729 seconds.
 Auto-regeneration: enabled for '/octocat/personal-website'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

不用担心"No GitHub API authentication could be found"消息。[API 认证仅在](https://github.com/jekyll/github-metadata/blob/master/docs/authentication.md)您想要显示更详细的元数据（如分支名称）时才需要。

6. 现在访问 [http://localhost:4000](http://localhost:4000)

### 发布

当您在 GitHub 上托管个人网站代码时，可以通过 GitHub Pages 获得免费托管支持。

**最快的方法**是将您的仓库重命名为 `username.github.io`，其中 `username` 是您的 GitHub 用户名（或组织名称）。然后，下次您将任何更改推送到仓库的 `master` 分支时，它们将在您的 `username.github.io` 地址上通过网络访问。

**如果您想使用自定义域名**，需要将其添加到 github.com 上仓库的"Custom domain"设置中。然后注册和/或[使用 DNS 提供商配置您的域名](https://help.github.com/articles/quick-start-setting-up-a-custom-domain/)。

## 自定义

这是您的网站，您控制源代码。因此，如果您愿意，可以自定义所有内容。但我们提供了一些快速自定义选项，供您在启动网站时考虑。

### 快速配置更改

大多数自定义可以通过修改仓库的 `_config.yml` 文件在几秒钟内完成。只需记住每次保存新更改后重新启动本地服务器，以便您的 Jekyll 网站正确重建：

1. 通过键盘命令 <kbd>CTRL</kbd>+<kbd>c</kbd> 关闭服务器
2. 重新启动服务器：`bundle exec jekyll serve`

#### 布局

您的网站在较大屏幕设备上默认显示为两列布局，照片、姓名和基本信息显示在左对齐的"侧边栏"中。您可以通过将 `_config.yml` 文件中读取 `layout: sidebar` 的行更改为 `layout: stacked` 来快速切换到"堆叠"单列布局。

#### 样式

您的网站默认显示为"浅色"白色和灰色背景，带有深色文本。您可以通过将 `_config.yml` 文件中读取 `style: light` 的行更改为 `style: dark` 来快速切换到带有白色文本的"深色"背景。

#### 项目

您网站的"我的项目"部分默认使用您最近"推送"的九个仓库生成。默认情况下，它还会排除您 fork 的仓库。但这些参数中的每一个都可以在仓库的 `_config.yml` 文件中的 `projects` 字典行下快速自定义。

参数包括：

- `sort_by`：仓库排序的方法。选项包括 `pushed` 和 `stars`。
- `limit`：将在您网站的"我的项目"部分显示的仓库的最大数量。开箱即用，此数字设置为 `9`。
- `exclude`：
   - `forks`：当为 `true` 时，您 fork 的仓库将从列表中排除。
   - `projects`：您要从列表中排除的仓库名称列表。

#### 主题

您的网站预配置了三个主题（例如"Web design"和"Sass"），它们出现在标题为"我的兴趣"的部分中。这些也存储在仓库的 `_config.yml` 文件中，您可以在其中定义每个主题的名称和其他两个可选详细信息：

- `web_url`：您希望主题链接到的网址（例如 `https://github.com/topics/sass`）。
- `image_url`：您希望与主题一起显示的图像的网址（最好是正方形）。

#### 社交媒体

您的网站支持链接和分享到您使用的社交媒体服务，包括 Behance、Dribbble、Facebook、LinkedIn、Medium、Stack Overflow、Twitter 和 YouTube。要识别您使用的服务：

1. 编辑仓库的 `_config.yml` 文件。
2. 编辑 `social_media` 字典行，并以简单的 `key: value` 形式表示您喜欢的服务：

```
social_media:
  behance: your_username
  dribbble: your_username  
  facebook: your_username
  hackerrank: your_username
  instagram: your_username
  keybase: your_username
  linkedin: your_username
  medium: your_username
  stackoverflow: your_user_id
  telegram: your_username
  twitter: your_username
  unsplash: your_username
  vk: your_username
  website: http://your_website_url
  youtube: your_username
```

您定义的每个服务的个人资料链接将出现在网站的 `<header>` 中，附加到您的简介。如果这些服务支持分享，您发布的任何博客文章都将包含使用每个社交媒体服务分享该文章的链接。

**注意**：此功能由仓库中的两个文件支持：

- `/_data/social_media.yml`：定义每个支持的服务，包括变量名、显示名称、URL 路径和 SVG 图标。
- `/_includes/social_media_share_url.html`：输出支持分享 URL 的任何支持的社交媒体服务所需的分享 URL。

如果您有兴趣添加此仓库中尚未支持的社交媒体服务，可以编辑这两个文件来构建该支持。

## 添加页面

要在您的网站上**添加页面**（例如详细简历）：

1. 在仓库根目录创建一个新的 `.html` 或 `.md` 文件。
2. 给它一个您希望在页面 URL 中使用的文件名（例如 `http://yoursite.dev/filename`）。
3. 在文件开头，包含以下 [front matter](https://jekyllrb.com/docs/front-matter/)：

```
---
layout: default
---
```

## 添加博客文章

要在您的网站上**添加博客文章**：

1. 在仓库的 `/_posts/` 目录中创建一个新的 `.md` 文件。
2. 使用以下格式为其命名：

```
YEAR-MONTH-DAY-title.MARKUP
```

3. 在文件开头，包含以下 [front matter](https://jekyllrb.com/docs/front-matter/)：

```
---
title: "我的博客文章标题"
---
```

您的网站附带一个占位符博客文章，您可以参考。值得注意的是，它的 [front matter](https://jekyllrb.com/docs/front-matter/) 将 `published` 声明为 `false`，因此它不会出现在您的网站上。

虽然您可以在 front matter 中定义 `layout`，但您的网站预配置为将 `post` 布局分配给 `/_posts/` 目录中的所有文章。因此，您不必在文章中声明它。

Jekyll 编写和管理博客文章的约定非常灵活。您可以在 [Jekyll 的"Posts"文档中了解更多信息](https://jekyllrb.com/docs/posts/)。

## 内容和模板

为了为您提供一个良好的基础来启动个人网站，您的仓库包含一些"includes"——在整个网站中重复使用的动态 `.html` 文件。它们都存储在 `/_includes/` 目录中。

有常见的文件，如 `header.html` 和 `footer.html`。但还有几个值得指出：

- `interests.html`：标题和"我的兴趣"的动态列表，由您在 `_config.yml` 中列出的[主题](#主题)填充。
- `masthead.html`：您的头像、姓名、简介和其他元数据的集合，在所有网页上突出显示，以帮助识别网站的内容。
- `post-card.html`：博客文章的紧凑、摘要展示，重复使用以显示您最新博客文章的列表。
- `projects.html`：标题和"我的项目"的动态列表，由您最新的 GitHub 仓库列表填充。
- `repo-card.html`：仓库的紧凑、摘要展示，重复使用以显示您的 GitHub 仓库列表。
- `thoughts.html`：标题和"我的想法"的动态列表，由您最新博客文章的列表填充。
- `topic-card.html`：主题的紧凑、摘要展示（在 `_config.yml` 中定义），重复使用以显示您的兴趣列表。

### 布局

您的仓库附带三个布局：

- **default**：任何内置页面或文章都不使用，但对您创建的任何新页面很有用。
- **home**：由您的 `index.html` 主页使用，以显示您的项目、兴趣和（可选）博客文章的列表。
- **post**：默认由 `/_posts/` 目录中的文章使用。

Jekyll 定义布局的约定非常灵活。您可以在 [Jekyll "Layouts" 文档中了解更多关于自定义布局的信息](https://jekyllrb.com/docs/layouts/)。

## 样式

您的网站预配置为使用 [GitHub 非常灵活的 CSS 框架"Primer"](https://styleguide.github.com/primer/)。它目前在您的 `styles.scss` 文件中引用，使用 CSS import 规则：

```
@import url('https://unpkg.com/primer/build/build.css');
```

当然，欢迎您删除它或将其替换为另一个框架。只需记住，您的网站预打包的 HTML 引用了多个 Primer"实用类"来定义列宽、边距和背景颜色等内容。

您还可以通过向 `/assets/styles.scss` Sass 样式表添加自定义 CSS 来添加和扩展 Primer 的样式。通过编辑此文件，您可以自定义网站的颜色方案、排版等。

## 多语言支持

本网站支持三种语言的切换：
- 英语（English）
- 简体中文（简体中文）
- 繁体中文（繁體中文）

用户可以通过页面右上角的语言选择器切换语言，选择会自动保存并在下次访问时应用。

## 许可证

该主题在 [MIT License](https://opensource.org/licenses/MIT) 条款下作为开源提供。
