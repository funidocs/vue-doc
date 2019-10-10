# 快速开始

> 1.  在`docs/`下新建 markdown 文件.
> 2.  在`_sidebar.md`添加配置

# Vue 的基本用法

```vue
<div>hello {{ msg }}</div>

<script>
new Vue({
	el: '#main',
	data: { msg: 'Vue' }
});
</script>
```
