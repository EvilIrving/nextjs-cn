---
title: onDemandEntries
description: 配置 Next.js 在开发中如何处置和保留在内存中创建的页面。
---



Next.js 提供了一些选项，让您可以控制服务器在开发中如何处置或保留在内存中构建的页面。

要更改默认设置，请打开 `next.config.js` 并添加 `onDemandEntries` 配置：

```js filename="next.config.js"
module.exports = {
  onDemandEntries: {
    // 服务器将页面保留在缓冲区中的周期（以毫秒为单位）
    maxInactiveAge: 25 * 1000,
    // 应同时保留而不会被处置的页面数量
    pagesBufferLength: 2,
  },
}
```