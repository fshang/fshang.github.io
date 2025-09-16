# Docsify 部署指南

> 一个简单且轻量级的文档网站生成器。

## 快速开始

### 1. 安装

全局安装 docsify-cli 工具：

```bash
npm i docsify-cli -g
```
### windows系统需要将docsify增加到系统环境变量中

### 2. 初始化项目

```bash
# 初始化项目
docsify init ./docsify

# 本地预览
docsify serve docsify
```

### 3. 项目结构

初始化后，您的项目将包含以下文件：

```
.
└── docsify
    ├── README.md
    ├── index.html
    └── .nojekyll
```

### 4. 配置文件

修改 `index.html` 配置文件：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/themes/vue.css" />
 
    <!-- 文件夹样式 -->
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/sidebar-folder.min.css" />
    <!-- 箭头样式 -->
    <!-- <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/sidebar.min.css" /> -->
  </head>
  <body>
    <div id="app"></div>
    <script>  
      window.$docsify = {
        name: "Blog",
        // 侧边栏文档目录
        loadSidebar: true,
 
        subMaxLevel: 2,
        alias: {
          "/.*/_sidebar.md": "/_sidebar.md",
        },
        // 跳转后自动到顶部
        auto2top: true,
 
        coverpage: true,
        // PLUGINS
        // ----------------------------------------------------------------
        // 页面右侧toc
        toc: {
          tocMaxLevel: 2,
          target: "h2, h3, h4, h5, h6",
        },
 
        // 全文搜索
        search: {
          depth: 6,
          noData: "没有搜到!",
          placeholder: "搜索...",
          // 避免搜索索引冲突,同一域下的多个网站之间
          namespace: "website-1",
        },
        // 底部导航
        pagination: {
          previousText: "上一页",
          nextText: "下一页",
          crossChapter: true,
          crossChapterText: true,
        },
        // 字数统计
        count: {
          countable: true,
          position: "top",
          margin: "10px",
          float: "right",
          fontsize: "0.9em",
          color: "red",
          language: "chinese",
          localization: {
            words: "",
            minute: "",
          },
          isExpected: true,
        },
      };
    </script>
    <!-- docsify -->
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/docsify.min.js"></script>  
 
    <!-- 代码高亮  https://cdn.jsdelivr.net/npm/prismjs@1/components/ -->
	
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>	
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-cmake.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-java.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-csharp.min.js"></script>     
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-docker.min.js"></script>  
	<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-powershell.min.js"></script>  
 
 
    <!-- 多tab支持 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-tabs@1/dist/docsify-tabs.min.js"></script>
 
    <!-- 代码复制 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-copy-code@2/dist/docsify-copy-code.min.js"></script>
 
    <!-- 底部 上一页下一页 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-pagination@2/dist/docsify-pagination.min.js"></script>
 
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/external-script.min.js"></script>
 
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/ga.min.js"></script>
 
    <!-- 全文搜索 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/search.js"></script>
 
    <!-- 图片放大缩小 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/zoom-image.min.js"></script>
 
    <!-- 字数统计 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-count@latest/dist/countable.min.js"></script>
 
    <!-- 侧边栏目录折叠 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
 
    <!-- 页面右侧 TOC -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-plugin-toc@1.1.0/dist/docsify-plugin-toc.min.js"></script>
 
      <!-- emoji -->
      <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
  </body>
</html>
```

### 5. 部署

#### GitHub Pages 部署

1. 将文档推送到 GitHub 仓库
2. 在仓库设置中启用 GitHub Pages
3. 选择部署分支和目录

#### Netlify 部署

1. 在 Netlify 中连接 GitHub 仓库
2. 设置构建命令（通常不需要）
3. 设置发布目录为 `docs`

### 6. 侧边栏配置

- 添加侧边栏：创建 `_sidebar.md` 文件
- 添加导航栏：创建 `_navbar.md` 文件
- 添加封面：创建 `_coverpage.md` 文件
- 支持 Emoji：引入 emoji 插件
- 支持复制代码：引入 copy-code 插件

## 相关链接

- [Docsify 官方文档](https://docsify.js.org/#/zh-cn/)
- [Docsify GitHub](https://github.com/docsifyjs/docsify/)
```