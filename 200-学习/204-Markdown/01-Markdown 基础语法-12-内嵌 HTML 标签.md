# 内嵌 HTML 标签

Markdown 支持 HTML 的行级內联标签和区块标签

**要点**：

- HTML 的块级元素请在其前后使用空行与其它内容进行分隔
- Markdown 语法在 HTML 区块标签中将不会被进行处理
- 尽量不要使用制表符或空格（spaces）对 HTML 标签做缩进

**注意**：并非所有 Markdown 应用程序都支持在 Markdown 文档中添加 HTML

## 折叠内容

```html
<details>
  <summary>折叠内容的标题</summary>
  折叠内容
</details>
```

演示：

<details>
  <summary>折叠内容的标题</summary>
  这是折叠的内容
</details>
