# 字体模块

### 字体函数参数

使用方式，请查看 [Google Fonts](/docs/app/building-your-application/optimizing/fonts#google-fonts) 和 [Local Fonts](/docs/app/building-your-application/optimizing/fonts#local-fonts)。

| 键                                           | `font/google`       | `font/local`        | 类型                       | 必需          |
| ------------------------------------------- | ------------------- | ------------------- | -------------------------- | ----------------- |
| [`src`](#src)                               | <Cross size={18} /> | <Check size={18} /> | 字符串或对象数组           | 是               |
| [`weight`](#weight)                         | <Check size={18} /> | <Check size={18} /> | 字符串或数组                | 必需/可选        |
| [`style`](#style)                           | <Check size={18} /> | <Check size={18} /> | 字符串或数组                | -                 |
| [`subsets`](#subsets)                       | <Check size={18} /> | <Cross size={18} /> | 字符串数组                  | -                 |
| [`axes`](#axes)                             | <Check size={18} /> | <Cross size={18} /> | 字符串数组                  | -                 |
| [`display`](#display)                       | <Check size={18} /> | <Check size={18} /> | 字符串                      | -                 |
| [`preload`](#preload)                       | <Check size={18} /> | <Check size={18} /> | 布尔值                      | -                 |
| [`fallback`](#fallback)                     | <Check size={18} /> | <Check size={18} /> | 字符串数组                  | -                 |
| [`adjustFontFallback`](#adjustfontfallback) | <Check size={18} /> | <Check size={18} /> | 布尔值或字符串              | -                 |
| [`variable`](#variable)                     | <Check size={18} /> | <Check size={18} /> | 字符串                      | -                 |
| [`declarations`](#declarations)             | <Cross size={18} /> | <Check size={18} /> | 对象数组                   | -                 |

### `src`

字体文件的路径，可以是字符串或对象数组（类型为 `Array<{path: string, weight?: string, style?: string}>`），相对于调用字体加载器函数的目录。

在 `next/font/local` 中使用

- 必需

示例：

- `src:'./fonts/my-font.woff2'` 其中 `my-font.woff2` 放置在 `app` 目录下的 `fonts` 目录中
- `src:[{path: './inter/Inter-Thin.ttf', weight: '100',},{path: './inter/Inter-Regular.ttf',weight: '400',},{path: './inter/Inter-Bold-Italic.ttf', weight: '700',style: 'italic',},]`
- 如果字体加载器函数在 `app/page.tsx` 中被调用，使用 `src:'../styles/fonts/my-font.ttf'`，则 `my-font.ttf` 放置在项目根目录的 `styles/fonts` 中
### 字体权重 `weight`

字体的[`weight`](https://fonts.google.com/knowledge/glossary/weight)，具有以下可能性：

- 一个字符串，包含特定字体可用的权重值，或者如果是一个[可变字体](https://fonts.google.com/variablefonts)，则为一系列值。
- 如果字体不是[可变谷歌字体](https://fonts.google.com/variablefonts)，则为权重值的数组。它仅适用于`next/font/google`。

在`next/font/google`和`next/font/local`中使用。

- 如果使用的字体**不是**[可变字体](https://fonts.google.com/variablefonts)，则为必需的。

示例：

- `weight: '400'`：一个字符串表示单个权重值 - 对于字体[`Inter`](https://fonts.google.com/specimen/Inter?query=inter)，可能的值为`'100'`，`'200'`，`'300'`，`'400'`，`'500'`，`'600'`，`'700'`，`'800'`，`'900'`或`'variable'`，其中`'variable'`是默认值。
- `weight: '100 900'`：一个字符串表示可变字体的`100`到`900`之间的范围。
- `weight: ['100','400','900']`：一个数组，包含3个非可变字体的可能值。

### 字体样式 `style`

字体的[`style`](https://developer.mozilla.org/docs/Web/CSS/font-style)，具有以下可能性：

- 一个字符串[值](https://developer.mozilla.org/docs/Web/CSS/font-style#values)，默认值为`'normal'`。
- 如果字体不是[可变谷歌字体](https://fonts.google.com/variablefonts)，则为风格值的数组。它仅适用于`next/font/google`。

在`next/font/google`和`next/font/local`中使用。

- 可选

示例：

- `style: 'italic'`：一个字符串 - 对于`next/font/google`，它可以是`normal`或`italic`。
- `style: 'oblique'`：一个字符串 - 对于`next/font/local`，它可以取任何值，但预期来自[标准字体样式](https://developer.mozilla.org/docs/Web/CSS/font-style)。
- `style: ['italic','normal']`：一个数组，包含`next/font/google`的2个值 - 值来自`normal`和`italic`。

### 字体子集 `subsets`

通过一个字符串值数组定义的字体[`subsets`](https://fonts.google.com/knowledge/glossary/subsetting)，包含您希望[预加载](/docs/app/building-your-application/optimizing/fonts#specifying-a-subset)的每个子集的名称。当[`preload`](#preload)选项为true（默认值）时，通过`subsets`指定的字体将在头部注入一个预加载链接标签。

在`next/font/google`中使用。

- 可选

示例：

- `subsets: ['latin']`：一个数组，包含子集`latin`

您可以在谷歌字体页面上找到您的字体的所有子集列表。

### 字体轴 `axes`

一些可变字体包含额外的`axes`。默认情况下，只包含字体权重，以减小文件大小。`axes`的可能值取决于特定字体。

在`next/font/google`中使用。

- 可选

示例：

- `axes: ['slnt']`：一个数组，值为`slnt`，用于`Inter`可变字体，该字体具有如[此处](https://fonts.google.com/variablefonts?vfquery=inter#font-families)所示的额外`axes` `slnt`。您可以通过在[谷歌可变字体页面](https://fonts.google.com/variablefonts#font-families)上使用过滤器并寻找除`wght`之外的轴，来找到您的字体可能的`axes`值。

### 字体显示 `display`

字体的[`display`](https://developer.mozilla.org/docs/Web/CSS/@font-face/font-display)，可能的字符串值为`'auto'`，`'block'`，`'swap'`，`'fallback'`或`'optional'`，默认值为`'swap'`。

在`next/font/google`和`next/font/local`中使用。

- 可选

示例：

- `display: 'optional'`：一个字符串，赋值为`optional`

### 预加载 `preload`

一个布尔值，指定是否应[预加载](/docs/app/building-your-application/optimizing/fonts#preloading)字体。默认值为`true`。


### `fallback`

如果字体无法加载，则使用的备用字体。一个由字符串组成的数组，列出了备用字体，没有默认值。

- 可选

在 `next/font/google` 和 `next/font/local` 中使用

示例：

- `fallback: ['system-ui', 'arial']`: 设置备用字体数组为 `system-ui` 或 `arial`

### `adjustFontFallback`

- 对于 `next/font/google`：一个布尔值，设置是否应使用自动备用字体以减少[累积布局偏移](https://web.dev/cls/)。默认值为 `true`。
- 对于 `next/font/local`：一个字符串或布尔值 `false`，设置是否应使用自动备用字体以减少[累积布局偏移](https://web.dev/cls/)。可能的值为 `'Arial'`, `'Times New Roman'` 或 `false`。默认值为 `'Arial'`。

在 `next/font/google` 和 `next/font/local` 中使用

- 可选

示例：

- `adjustFontFallback: false`: 对于 `next/font/google`
- `adjustFontFallback: 'Times New Roman'`: 对于 `next/font/local`

### `variable`

一个字符串值，用于定义如果使用[CSS变量方法](#css-变量)应用样式时使用的CSS变量名。

在 `next/font/google` 和 `next/font/local` 中使用

- 可选

示例：

- `variable: '--my-font'`: 声明CSS变量 `--my-font`

### `declarations`

一个字体面[描述符](https://developer.mozilla.org/docs/Web/CSS/@font-face#descriptors)键值对数组，用于进一步定义生成的 `@font-face`。

在 `next/font/local` 中使用

- 可选

示例：

- `declarations: [{ prop: 'ascent-override', value: '90%' }]`

## 应用样式

您可以通过以下三种方式应用字体样式：

- [`className`](#classname)
- [`style`](#style-1)
- [CSS变量](#css-变量)

### `className`

返回一个只读的CSS `className`，用于加载的字体，可以传递给HTML元素。

```tsx
<p className={inter.className}>Hello, Next.js!</p>
```

### `style`

返回一个只读的CSS `style` 对象，用于加载的字体，可以传递给HTML元素，包括 `style.fontFamily` 以访问字体族名称和备用字体。

```tsx
<p style={inter.style}>Hello World</p>
```

### CSS变量

如果您希望在外部样式表中设置样式并在那里指定其他选项，请使用CSS变量方法。

除了导入字体外，还导入定义CSS变量的CSS文件，并设置字体加载器对象的变量选项如下：

```tsx filename="app/page.tsx" switcher
import { Inter } from 'next/font/google'
import styles from '../styles/component.module.css'

const inter = Inter({
  variable: '--font-inter',
})
```

```jsx filename="app/page.js" switcher
import { Inter } from 'next/font/google'
import styles from '../styles/component.module.css'

const inter = Inter({
  variable: '--font-inter',
})
```

要使用字体，将文本的父容器的 `className` 设置为字体加载器的 `variable` 值，将文本的 `className` 设置为外部CSS文件中的 `styles` 属性。

```tsx filename="app/page.tsx" switcher
<main className={inter.variable}>
  <p className={styles.text}>Hello World</p>
</main>
```

```jsx filename="app/page.js" switcher
<main className={inter.variable}>
  <p className={styles.text}>Hello World</p>
</main>
```

在 `component.module.css` CSS文件中定义 `text` 选择器类如下：

```css filename="styles/component.module.css"
.text {
  font-family: var(--font-inter);
  font-weight: 200;
  font-style: italic;
}
```

在上面的示例中，文本 `Hello World` 使用 `Inter` 字体和生成的字体备用方案进行样式设置，`font-weight: 200` 和 `font-style: italic`。
## 使用字体定义文件

每次调用 `localFont` 或 Google 字体函数时，该字体将作为您的应用程序中的一个实例被托管。因此，如果您需要在多个地方使用相同的字体，您应该在一个地方加载它，并在需要的地方导入相关的字体对象。这是通过使用字体定义文件来完成的。

例如，在应用程序目录的根目录中创建一个 `styles` 文件夹，并在其中创建一个 `fonts.ts` 文件。

然后，按照以下方式指定您的字体定义：

```ts filename="styles/fonts.ts" switcher
import { Inter, Lora, Source_Sans_3 } from 'next/font/google'
import localFont from 'next/font/local'

// 定义您的变量字体
const inter = Inter()
const lora = Lora()
// 定义非变量字体的 2 种字重
const sourceCodePro400 = Source_Sans_3({ weight: '400' })
const sourceCodePro700 = Source_Sans_3({ weight: '700' })
// 定义自定义本地字体，其中 GreatVibes-Regular.ttf 存储在 styles 文件夹中
const greatVibes = localFont({ src: './GreatVibes-Regular.ttf' })

export { inter, lora, sourceCodePro400, sourceCodePro700, greatVibes }
```

```js filename="styles/fonts.js" switcher
import { Inter, Lora, Source_Sans_3 } from 'next/font/google'
import localFont from 'next/font/local'

// 定义您的变量字体
const inter = Inter()
const lora = Lora()
// 定义非变量字体的 2 种字重
const sourceCodePro400 = Source_Sans_3({ weight: '400' })
const sourceCodePro700 = Source_Sans_3({ weight: '700' })
// 定义自定义本地字体，其中 GreatVibes-Regular.ttf 存储在 styles 文件夹中
const greatVibes = localFont({ src: './GreatVibes-Regular.ttf' })

export { inter, lora, sourceCodePro400, sourceCodePro700, greatVibes }
```

现在，您可以按照以下方式在代码中使用这些定义：

```tsx filename="app/page.tsx" switcher
import { inter, lora, sourceCodePro700, greatVibes } from '../styles/fonts'

export default function Page() {
  return (
    <div>
      <p className={inter.className}>Hello world using Inter font</p>
      <p style={lora.style}>Hello world using Lora font</p>
      <p className={sourceCodePro700.className}>
        Hello world using Source_Sans_3 font with weight 700
      </p>
      <p className={greatVibes.className}>My title in Great Vibes font</p>
    </div>
  )
}
```

```jsx filename="app/page.js" switcher
import { inter, lora, sourceCodePro700, greatVibes } from '../styles/fonts'

export default function Page() {
  return (
    <div>
      <p className={inter.className}>Hello world using Inter font</p>
      <p style={lora.style}>Hello world using Lora font</p>
      <p className={sourceCodePro700.className}>
        Hello world using Source_Sans_3 font with weight 700
      </p>
      <p className={greatVibes.className}>My title in Great Vibes font</p>
    </div>
  )
}
```

为了更方便地在代码中访问字体定义，您可以在 `tsconfig.json` 或 `jsconfig.json` 文件中定义一个路径别名，如下所示：

```json filename="tsconfig.json"
{
  "compilerOptions": {
    "paths": {
      "@/fonts": ["./styles/fonts"]
    }
  }
}
```

现在，您可以按照以下方式导入任何字体定义：

```tsx filename="app/about/page.tsx" switcher
import { greatVibes, sourceCodePro400 } from '@/fonts'
```

```jsx filename="app/about/page.js" switcher
import { greatVibes, sourceCodePro400 } from '@/fonts'
```

## 版本变更

| 版本   | 变更                                                               |
| --------- | --------------------------------------------------------------------- |
| `v13.2.0` | `@next/font` 重命名为 `next/font`。不再需要安装。 |
| `v13.0.0` | 添加了 `@next/font`。                                               |