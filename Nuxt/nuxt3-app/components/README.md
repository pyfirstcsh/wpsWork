# components/ 目录

components/ 目录是存放可导入到你的页面中的 Vue 组件或其他组件。
Nuxt 会自动导入 components/ 目录下任何组件。

## 组件命名

如你的嵌套目录中有一个组件，例如：

```bash
| components/
--| base/
----| foo/
------| Button.vue
```

... 然后组件的名称将基于自己的路径和文件名，并删除重复的段 (比如： an/an/Button.vue 注册名将会是 AnButton)。因此组件名会是：

```vue
<BaseFooButton />
```

::: info 提示：
为清楚起见，建议组件的文件名与其名称匹配。 (所以，在上面的例子中, 你可以将 `Button.vue` 重命名为 `BaseFooButton.vue`.)
:::

## 动态导入

要动态导入一个组件 (也称为懒加载一个组件) 只需要在原组件名前加上 `Lazy` 前缀.

```vue
<template>
  <div>
    <TheHeader />
    <slot />
    <LazyTheFooter />
  </div>
</template>
```

当该组件不是总被需要，这一点特别重要。通过使用 `Lazy` 前缀，你可以在合适的时机，延迟加载组件代码，这有助于优化你的 JavaScript 包大小。

```vue
<template>
  <div>
    <h1>Mountains</h1>
    <LazyMountainsList v-if="show" />
    <button v-if="!show" @click="show = true">Show List</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false
    }
  }
}
</script>
```
