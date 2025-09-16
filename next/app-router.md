## Next.js 13+ App路由详解
Next.js 13引入的App Router是基于React Server Components构建的全新路由系统，相比传统的Pages Router提供了更强大的功能和更灵活的架构
## 1. App Router核心概念
App Router位于&zwnj;**app/目录下**&zwnj;，通过文件系统自动映射URL路径，支持动态路由、嵌套路由、路由分组和更灵活的布局管理
其主要特点包括：

- &zwnj;基于文件系统的路由‌&zwnj;：文件夹结构直接映射为URL路径，page.js文件定义页面内容
- &zwnj;服务器优先原则‌&zwnj;：默认使用React Server Components，减少客户端bundle大小
- &zwnj;增强的路由功能‌&zwnj;：支持嵌套布局、并行路由、中间件等高级特性
- &zwnj;改进的数据获取‌&zwnj;：简化了数据获取流程，无需getStaticProps等专用函数

## 2. 基础路由实现
### 1. 静态路由
在app目录下创建文件夹和page.js文件即可定义路由：

```javascript

// app/page.js - 对应根路径 / 
export default function Home() {
  return <h1>欢迎来到首页</h1>;
}

// app/about/page.js - 对应 /about
export default function About() {
  return <h1>关于我们</h1>;
}

```
### 2. 动态路由
使用&zwnj;**[param]**&zwnj;语法定义动态路由参数：

```javascript
// app/blog/[id]/page.js - 对应 /blog/:id
export default function BlogPost({ params }) {
  const { id } = params;
  return <h1>博客文章ID: {id}</h1>;
}
```

## 3. 高级路由功能
### 1. 路由组(Route Groups)
通过将文件夹名用括号包裹(groupName)创建路由组，路由组将路由和项目文件按照逻辑进行分组，但不会影响 URL 路径结构不：

```text
app/
  (marketing)/
    layout.js  # 营销页面专用布局
    about/
      page.js  # /about
  (shop)/
    layout.js  # 商城页面专用布局
    cart/
      page.js  # /cart
```
这样可以在代码层面组织相关路由，同时保持URL简洁

### 2. 嵌套布局
App Router支持自动嵌套布局，通过在文件夹中添加layout.js实现：

```javascript

// app/layout.js - 根布局
export default function RootLayout({ children }) {
  return (
    <html>
      <body>
        <header>全局导航栏</header>
        {children}
      </body>
    </html>
  );
}

// app/dashboard/layout.js - 仪表盘专用布局
export default function DashboardLayout({ children }) {
  return (
    <div>
      <h2>仪表盘侧边栏</h2>
      <div>{children}</div>
    </div>
  );
}
```

布局会自动嵌套，&zwnj;**/dashboard**&zwnj;页面将同时应用两种布局

## 4. 数据获取与路由
在App Router中，可以直接在Server Components中获取数据：

```javascript
// app/products/page.js
async function getProducts() {
  const res = await fetch('https://api.example.com/products');
  return res.json();
}

export default async function ProductsPage() {
  const products = await getProducts();
  
  return (
    <ul>
      {products.map(product => (
        <li key={product.id}>{product.name}</li>
      ))}
    </ul>
  );
}
```
Next.js会自动缓存fetch请求，默认行为等同于getStaticProps

## 5. 完整示例项目
下面是一个简单的博客系统路由结构示例：

```text

app/
  layout.js        # 全局布局
  page.js          # 首页 (/)
  about/
    page.js        # 关于页 (/about)
  blog/
    layout.js      # 博客专用布局
    page.js        # 博客列表 (/blog)
    [slug]/
      page.js      # 博客详情 (/blog/:slug)
  (admin)/
    layout.js      # 管理后台布局
    dashboard/
      page.js      # 管理面板 (/dashboard)
```

每个page.js文件导出React组件作为页面内容，布局会自动嵌套应用

## 6. 总结
Next.js 13+的App Router提供了更现代、更灵活的路由解决方案，特别适合构建复杂的应用程序。通过文件系统路由、嵌套布局和简化的数据获取等特性，开发者可以更高效地组织代码并提升应用性能