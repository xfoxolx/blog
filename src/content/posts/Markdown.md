---
title: Blog の Markdown 语法
published: 2024-06-29
description: "Markdown 语法快查"
image: "./cover/light-5.jpg"
tags: [Markdown]
category: Language
draft: false
---

## Blog の Markdown 语法

- GitHub Repository Cards

::github{repo="xfoxolx/xfoxolx"}

```markdown
::github{repo="xfoxolx/xfoxolx"}
```

- Admonitions

:::note
Highlights information that users should take into account, even when skimming.
:::

:::tip
Optional information to help a user be more successful.
:::

```markdown
:::tip
Optional information to help a user be more successful.
:::

:::note[CUSTOM TITLE]
This is a note with a custom title.
:::

`note` `tip` `important` `warning` `caution`
```

- Rendering ANSI escape sequences

```ansi
ANSI colors:
- Regular: [31mRed[0m [32mGreen[0m [33mYellow[0m [34mBlue[0m [35mMagenta[0m [36mCyan[0m
- Bold:    [1;31mRed[0m [1;32mGreen[0m [1;33mYellow[0m [1;34mBlue[0m [1;35mMagenta[0m [1;36mCyan[0m
- Dimmed:  [2;31mRed[0m [2;32mGreen[0m [2;33mYellow[0m [2;34mBlue[0m [2;35mMagenta[0m [2;36mCyan[0m

256 colors (showing colors 160-177):
[38;5;160m160 [38;5;161m161 [38;5;162m162 [38;5;163m163 [38;5;164m164 [38;5;165m165[0m
[38;5;166m166 [38;5;167m167 [38;5;168m168 [38;5;169m169 [38;5;170m170 [38;5;171m171[0m
[38;5;172m172 [38;5;173m173 [38;5;174m174 [38;5;175m175 [38;5;176m176 [38;5;177m177[0m

Full RGB colors:
[38;2;34;139;34mForestGreen - RGB(34, 139, 34)[0m

Text formatting: [1mBold[0m [2mDimmed[0m [3mItalic[0m [4mUnderline[0m
```

- Editor & Terminal Frames

```js title="my-test-file.js"
console.log('Title attribute example')
```

```html
<!-- src/content/index.html -->
<div>File name comment example</div>
```

```bash
echo "This terminal frame has no title"
```

```bash frame="code" title="echo.sh"
echo "This terminal frame has no title"
```

- Marking full lines & line ranges

```js {1, 3, 6-7}
// Line 1 - targeted by line number
// Line 2
// Line 3 - targeted by line number
// Line 4 
// Line 5
// Line 6 - targeted by range "6-7"
// Line 7 - targeted by range "6-7"
```

```js title="line-markers.js" del={2} ins={3-4} {5}
function demo() {
  console.log('this line is marked as deleted')
  // This line and the next one are marked as inserted
  console.log('this is the second inserted line')
  return 'this line uses the neutral default marker type'
}
```

```diff
+this line will be marked as inserted
-this line will be marked as deleted
this is a regular line
```

- Collapsible Sections

```js collapse={1-5, 12-14, 21-24}
// All this boilerplate setup code will be collapsed
import { someBoilerplateEngine } from '@example/some-boilerplate'
import { evenMoreBoilerplate } from '@example/even-more-boilerplate'

const engine = someBoilerplateEngine(evenMoreBoilerplate())

// This part of the code will be visible by default
engine.doSomething(1, 2, 3, calcFn)

function calcFn() {
  // You can have multiple collapsed sections
  const a = 1
  const b = 2
  const c = a + b

  // This will remain visible
  console.log(`Calculation result: ${a} + ${b} = ${c}`)
  return c
}

// All this code until the end of the block will be collapsed again
engine.closeConnection()
engine.freeMemory()
engine.shutdown({ reason: 'End of example boilerplate code' })
```

