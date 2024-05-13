# Next.js 项目结构

本页面提供了Next.js应用程序的项目结构概览。它涵盖了顶级文件和文件夹、配置文件以及在`app`和`pages`目录内的路由约定。

点击文件和文件夹名称可以了解更多关于每个约定的信息。

## 顶级文件夹

顶级文件夹用于组织您的应用程序代码和静态资源。

<Image
alt="将路由段转换为路径段"
srcLight="/docs/light/top-level-folders.png"
srcDark="/docs/dark/top-level-folders.png"
width="1600"
height="525"
/>

| 文件夹 | 描述 |
| --- | --- |
| [`app`](/docs/app/building-your-application/routing) | 应用路由 |
| [`pages`](/docs/pages/building-your-application/routing) | 页面路由 |
| [`public`](/docs/app/building-your-application/optimizing/static-assets) | 要提供的静态资源 |
| [`src`](/docs/app/building-your-application/configuring/src-directory) | 可选的应用程序源文件夹 |

## 顶级文件

顶级文件用于配置您的应用程序，管理依赖关系，运行中间件，集成监控工具，以及定义环境变量。

| 文件 | 描述 |
| --- | --- |
| **Next.js** |  |
| [`next.config.js`](/docs/app/api-reference/next-config-js) | Next.js的配置文件 |
| [`package.json`](/docs/getting-started/installation#manual-installation) | 项目依赖和脚本 |
| [`instrumentation.ts`](/docs/app/building-your-application/optimizing/instrumentation) | OpenTelemetry和监控文件 |
| [`middleware.ts`](/docs/app/building-your-application/routing/middleware) | Next.js请求中间件 |
| [`.env`](/docs/app/building-your-application/configuring/environment-variables) | 环境变量 |
| [`.env.local`](/docs/app/building-your-application/configuring/environment-variables) | 本地环境变量 |
| [`.env.production`](/docs/app/building-your-application/configuring/environment-variables) | 生产环境变量 |
| [`.env.development`](/docs/app/building-your-application/configuring/environment-variables) | 开发环境变量 |
| [`.eslintrc.json`](/docs/app/building-your-application/configuring/eslint) | ESLint的配置文件 |
| `.gitignore` | Git要忽略的文件和文件夹 |
| `next-env.d.ts` | Next.js的TypeScript声明文件 |
| `tsconfig.json` | TypeScript的配置文件 |
| `jsconfig.json` | JavaScript的配置文件 |

## `app`路由约定

以下是在[`app`路由](/docs/app)中定义路由和处理元数据使用的文件约定。

### 路由文件

| 文件 | 格式 | 描述 |
| --- | --- | --- |
| [`layout`](/docs/app/api-reference/file-conventions/layout) | `.js` `.jsx` `.tsx` | 布局 |
| [`page`](/docs/app/api-reference/file-conventions/page) | `.js` `.jsx` `.tsx` | 页面 |
| [`loading`](/docs/app/api-reference/file-conventions/loading) | `.js` `.jsx` `.tsx` | 加载UI |
| [`not-found`](/docs/app/api-reference/file-conventions/not-found) | `.js` `.jsx` `.tsx` | 未找到UI |
| [`error`](/docs/app/api-reference/file-conventions/error) | `.js` `.jsx` `.tsx` | 错误UI |
| [`global-error`](/docs/app/api-reference/file-conventions/error#global-errorjs) | `.js` `.jsx` `.tsx` | 全局错误UI |
| [`route`](/docs/app/api-reference/file-conventions/route) | `.js` `.ts` | API端点 |
| [`template`](/docs/app/api-reference/file-conventions/template) | `.js` `.jsx` `.tsx` | 重新渲染的布局 |
| [`default`](/docs/app/api-reference/file-conventions/default) | `.js` `.jsx` `.tsx` | 平行路由回退页面 |

### 嵌套路由

| 文件夹 | 描述 |
| --- | --- |
| [`folder`](/docs/app/building-your-application/routing#route-segments) | 路由段 |
| [`folder/folder`](/docs/app/building-your-application/routing#nested-routes) | 嵌套路由段 |

### 动态路由

| 文件夹 | 描述 |
| --- | --- |
| [`[folder]`](/docs/app/building-your-application/routing/dynamic-routes#convention) | 动态路由段 |
| [`[...folder]`](/docs/app/building-your-application/routing/dynamic-routes#catch-all-segments) | 捕获所有路由段 |
| [`[[...folder]]`](/docs/app/building-your-application/routing/dynamic-routes#optional-catch-all-segments) | 可选的捕获所有路由段 |

### 路由组和私有文件夹

| 文件夹 | 描述 |
| --- | --- |
| [`(folder)`](/docs/app/building-your-application/routing/route-groups#convention) | 不影响路由地分组路由 |
| [`_folder`](/docs/app/building-your-application/routing/colocation#private-folders) | 将文件夹及其所有子段排除在路由之外 |

### 平行和拦截路由

| 文件夹 | 描述 |
| --- | --- |
| [`@folder`](/docs/app/building-your-application/routing/parallel-routes#slots) | 命名插槽 |
| [`(.)folder`](/docs/app/building-your-application/routing/intercepting-routes#convention) | 拦截同一级 |
| [`(..)folder`](/docs/app/building-your-application/routing/intercepting-routes#convention) | 拦截上一级 |
| [`(..)(..)folder`](/docs/app/building-your-application/routing/intercepting-routes#convention) | 拦截两级以上 |
| [`(...)folder`](/docs/app/building-your-application/routing/intercepting-routes#convention) | 从根拦截 |

### 元数据文件约定

#### 应用图标

| 文件 | 格式 | 描述 |
| --- | --- | --- |
| [`favicon`](/docs/app/api-reference/file-conventions/metadata/app-icons#favicon) | `.ico` | 网站图标文件 |
| [`icon`](/docs/app/api-reference/file-conventions/metadata/app-icons#icon) | `.ico` `.jpg` `.jpeg` `.png` `.svg` | 应用图标文件 |
| [`icon`](/docs/app/api-reference/file-conventions/metadata/app-icons#generate-icons-using-code-js-ts-tsx) | `.js` `.ts` `.tsx` | 生成的应用图标 |
| [`apple-icon`](/docs/app/api-reference/file-conventions/metadata/app-icons#apple-icon) | `.jpg` `.jpeg`, `.png` | 苹果应用图标文件 |
| [`apple-icon`](/docs/app/api-reference/file-conventions/metadata/app-icons#generate-icons-using-code-js-ts-tsx) | `.js` `.ts` `.tsx` | 生成的苹果应用图标 |

#### Open Graph和Twitter图片

| 文件 | 格式 | 描述 |
| --- | --- | --- |
| [`opengraph-image`](/docs/app/api-reference/file-conventions/metadata/opengraph-image#opengraph-image) | `.jpg` `.jpeg` `.png` `.gif` | Open Graph图片文件 |
| [`opengraph-image`](/docs/app/api-reference/file-conventions/metadata/opengraph-image#generate-images-using-code-js-ts-tsx) | `.js` `.ts` `.tsx` | 生成的Open Graph图片 |
| [`twitter-image`](/docs/app/api-reference/file-conventions/metadata/opengraph-image#twitter-image) | `.jpg` `.jpeg` `.png` `.gif` | Twitter图片文件 |
| [`twitter-image`](/docs/app/api-reference/file-conventions/metadata/opengraph-image#generate-images-using-code-js-ts-tsx) | `.js` `.ts` `.tsx` | 生成的Twitter图片 |

#### SEO

| 文件 | 格式 | 描述 |
| --- | --- | --- |
| [`sitemap`](/docs/app/api-reference/file-conventions/metadata/sitemap#sitemap-files-xml) | `.xml` | 站点地图文件 |
| [`sitemap`](/docs/app/api-reference/file-conventions/metadata/sitemap#generating-a-sitemap-using-code-js-ts) | `.js` `.ts` | 生成的站点地图 |
| [`robots`](/docs/app/api-reference/file-conventions/metadata/robots#static-robotstxt) | `.txt` | Robots文件 |
| [`robots`](/docs/app/api-reference/file-conventions/metadata/robots#generate-a-robots-file) | `.js` `.ts` | 生成的Robots文件 |

## `pages`路由约定

以下是在[`pages`路由](/docs/pages)中定义路由使用的文件约定。

### 特殊文件

| 文件 | 格式 | 描述 |
| --- | --- | --- |
| [`_app`](/docs/pages/building-your-application/routing/custom-app) | `.js` `.jsx` `.tsx` | 自定义应用 |
| [`_document`](/docs/pages/building-your-application/routing/custom-document) | `.js` `.jsx` `.tsx` | 自定义文档 |
| [`_error`](/docs/pages/building-your-application/routing/custom-error#more-advanced-error-page-customizing) | `.js` `.jsx` `.tsx` | 自定义错误页面 |
| [`404`](/docs/pages/building-your-application/routing/custom-error#404-page) | `.js` `.jsx` `.tsx` | 404错误页面 |
| [`500`](/docs/pages/building-your-application/routing/custom-error#500-page) | `.js` `.jsx` `.tsx` | 500错误页面 |

### 路由

| 文件夹约定 | 文件 | 描述 |
| --- | --- | --- |
| [`index`](/docs/pages/building-your-application/routing/pages-and-layouts#index-routes) | `.js` `.jsx` `.tsx` | 首页 |
| [`folder/index`](/docs/pages/building-your-application/routing/pages-and-layouts#index-routes) | `.js` `.jsx` `.tsx` | 嵌套页面 |
| 文件约定 |  |  |
| [`index`](/docs/pages/building-your-application/routing/pages-and-layouts#index-routes) | `.js` `.jsx` `.tsx` | 首页 |
| [`file`](/docs/pages/building-your-application/routing/pages-and-layouts) | `.js` `.jsx` `.tsx` | 嵌套页面 |

### 动态路由

| 文件夹约定 | 文件 | 描述 |
| --- | --- | --- |
| [`[folder]/index`](/docs/pages/building-your-application/routing/dynamic-routes) | `.js` `.jsx` `.tsx` | 动态路由段 |
| [`[...folder]/index`](/docs/pages/building-your-application/routing/dynamic-routes#catch-all-segments) | `.js` `.jsx` `.tsx` | 捕获所有路由段 |
| [`[[...folder]]/index`](/docs/pages/building-your-application/routing/dynamic-routes#optional-catch-all-segments) | `.js` `.jsx` `.tsx` | 可选的捕获所有路由段 |
| 文件约定 |  |  |
| [`[file]`](/docs/pages/building-your-application/routing/dynamic-routes) | `.js` `.jsx` `.tsx` | 动态路由段 |
| [`[...file]`](/docs/pages/building-your-application/routing/dynamic-routes#catch-all-segments) | `.js` `.jsx` `.tsx` | 捕获所有路由段 |
| [`[[...file]]`](/docs/pages/building-your-application/routing/dynamic-routes#optional-catch-all-segments) | `.js` `.jsx` `.tsx` | 可选的捕获所有路由段 |