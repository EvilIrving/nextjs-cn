---
title: 日志记录
description: 配置在开发模式下运行 Next.js 时如何将数据抓取记录到控制台。
---



您可以配置在开发模式下运行 Next.js 时日志记录的级别以及是否将完整 URL 记录到控制台。

目前，`logging` 仅适用于使用 `fetch` API 的数据抓取。它尚未适用于 Next.js 内部的其他日志。

```js filename="next.config.js"
module.exports = {
  logging: {
    fetches: {
      fullUrl: true,
    },
  },
}
```