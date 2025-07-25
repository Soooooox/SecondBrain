# 数学表达式

## 行内数学表达式

使用 `$` 美元符号将表达式括起来

```latex
$数学表达式$

$`数学表达式`$
```

**注意**：中文符号与其后面 `$$` 之间需要有空格，因此最好行内数学表达式前面使用英文符号与空格的组合

## 块级数学表达式

使用 `$$` 将表达式括起来

```latex
$$数学表达式$$
```

使用代码块表示，语言选择 `math` (推荐)

```latex
    ```math
    数学表达式
    ```
```

**注意**：块级数学表达式前后要空一行

## Github 的 latex 表达式使用方法

### 1. 数学表达式标号

```latex
数学表达式 \quad (序号)
```

### 2. 花括号的显示{ }

行内：

```latex
$`\{ 数学表达式 \}`$
```

块级：使用代码块

```latex
\{ 数学表达式 \}
```
