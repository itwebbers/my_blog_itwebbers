---
title: vue之scoped css
categories:
  - Vuejs
date: 2018-12-25
type: 'tags'
tags:
  - css
  - vue
---

# Scoped CSS 详解

> 当`<style>`标签有`scoped`属性时，它的 CSS 只作用于当前组件中的元素，这类似与 Shadow DOM 中的样式封装。他有一些注意事项，但不许任何 polyfill。它通过 PostCSS 来实现以下转换

```vue
<style scoped>
.example {
  color: red;
}
</style>

<template>
  <div class="example">hi</div>
</template>
```

## 子组件的根元素

> 使用`scoped`后，父组件的样式将不会渗透到子组件中。不过一个子组件的根节点会同时受其父组件的 scoped CSS 和子组件 scoped CSS 的影响。这样涉及是为了让父组件可以从布局的角度出发，调整其子组件根元素的样式。

## 深度作用选择器

> 如果你希望`scoped`样式中的一个选择器能够作用得更深，例如影响子组件，你可以使用 `>>>` 操作符：

```css
<style scoped>
  .a >>> .b { /* ... */ }
</style>
```

> 上述的代码会被编译成：

```css
.a[data-v-f3f3eg9] .b {
  /* ... */
}
```

> <font color=red>有些像 Sass 之类的预处理器无法正确解析 `>>>`。这种情况下你可以使用`/deep/` 操作符取而代之这个`>>>`的别名，同样可以正常工作</font>

## 动态生成的内容

> 通过`v-html`创建的 DOM 内容不受 Scoped 样式影响，但是你仍然可以通过深度作用选择器来为他们设置样式。
