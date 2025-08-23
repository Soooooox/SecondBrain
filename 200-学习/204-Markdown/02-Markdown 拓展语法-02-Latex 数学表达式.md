# Latex 数学表达式

## 基础语法结构

- 命令：以反斜杠 `\` 开头 `\命令`，如 `\alpha`、`\sum`
- 参数：用花括号 `{}` 包围必需参数，如 `\frac{a}{b}`
- 分组：用花括号 `{}` 将多个字符组合，定义操作范围，如 `x_{i+1}`

## 小写希腊字母

| 小写希腊字母 | LaTeX 代码   | 小写希腊字母 | LaTeX 代码   |
|-------------|-------------|-------------|-------------|
| $\alpha$    | `\alpha`    | $\beta$     | `\beta`     |
| $\gamma$    | `\gamma`    | $\delta$    | `\delta`    |
| $\epsilon$  | `\epsilon`  | $\zeta$     | `\zeta`     |
| $\eta$      | `\eta`      | $\theta$    | `\theta`    |
| $\iota$     | `\iota`     | $\kappa$    | `\kappa`    |
| $\lambda$   | `\lambda`   | $\mu$       | `\mu`       |
| $\nu$       | `\nu`       | $\xi$       | `\xi`       |
| $\pi$       | `\pi`       | $\rho$      | `\rho`      |
| $\sigma$    | `\sigma`    | $\tau$      | `\tau`      |
| $\upsilon$  | `\upsilon`  | $\phi$      | `\phi`      |
| $\chi$      | `\chi`      | $\psi$      | `\psi`      |
| $\omega$    | `\omega`    |             |             |

## 大写希腊字母

小写希腊字母的 LaTeX 代码首字母大写对应大写希腊字母

| 大写希腊字母 | LaTeX 代码   | 大写希腊字母 | LaTeX 代码   |
|-------------|-------------|-------------|-------------|
| $\Gamma$    | `\Gamma`    | $\Delta$    | `\Delta`    |
| $\Theta$    | `\Theta`    | $\Lambda$   | `\Lambda`   |
| $\Xi$       | `\Xi`       | $\Pi$       | `\Pi`       |
| $\Sigma$    | `\Sigma`    | $\Upsilon$  | `\Upsilon`  |
| $\Phi$      | `\Phi`      | $\Psi$      | `\Psi`      |
| $\Omega$    | `\Omega`    |             |             |

## 常用数学符号

### 基本运算符号

- 加减乘除：
    - 加 $+$：`+`
    - 减 $-$：`-`
    - 乘 $\times$：`\times`
    - 除 $\div$：`\div`
- 分数 $\frac{a}{b}$：`\frac{分子}{分母}`
- 根号：
    - 平方根 $\sqrt{a}$：`\sqrt{根内式子}`
    - n 次根 $\sqrt[n]{a}$：`\sqrt[n]{根内式子}`

### 指数和下标

- 指数 $a^b$：用 `^` 后加相应的字符来实现
- 下标 $a_b$：用 `_` 后加相应的字符来实现

### 比较符号

- 等于：
    - 等于 $=$：`=`
    - 不等于 $\neq$：`\neq`
    - 恒等于 $\equiv$：`\equiv`
- 大小：
    - 小于 $<$：`<`
    - 大于 $>$：`>`
    - 小于等于 $\leq$：`\leq`
    - 大于等于 $\geq$：`\geq`
- 约等于：
    - 约等于 $\approx$：`\approx`
    - 相似于 $\sim$：`\sim`

### 集合符号

- 属于：
    - 属于 $\in$：`\in`
    - 不属于 $\notin$：`\notin`
- 包含：
    - 子集 $\subset$：`\subset`
    - 超集 $\supset$：`\supset`
- 交并：
    - 交集 $\cap$：`\cap`
    - 并集 $\cup$：`\cup`
- 空集 $\emptyset$：`\emptyset`

## 特殊函数和符号

- 三角函数：
    - 正弦 $\sin$：`\sin`
    - 余弦 $\cos$：`\cos`
    - 正切 $\tan$：`\tan`
- 对数：
    - 对数函数 $\log$：`\log`
    - 自然对数 $\ln$：`\ln`
- 极限 $\lim_{x \to 0}$：`\lim_{变量 \to 极限值}`
- 求和 $\sum_{i=1}^{n}$：`\sum_{下界=起始数}^{上届}`
- 积分 $\int_{a}^{b}$：`\int_{上届}^{下界}`
- 无穷 $\infty$：`\infty`

## 括号

- 小括号 $()$：`()`
- 方括号 $[]$：`[]`
- 大括号 $\lbrace \rbrace$：左 `\lbrace`、右 `\rbrace`
- 尖括号 $\langle \rangle$：左 `\langle`、右 `\rangle`

## 多行对齐公式

**行内公式**：

```latex
\begin{align} 多行公式内容 \end{align}
```

**块级公式**：

```latex
\begin{align}
多行公式内容
\end{align}
```

- 多行公式内容：换行用 `\\`

## 矩阵

**行内公式**：

```latex
\begin{括号类型} 矩阵内容 \end{括号类型}
```

**块级公式**：

```latex
\begin{括号类型}
矩阵内容
\end{括号类型}
```

- 矩阵内容：
    - 元素分隔：用 `&`
    - 换行：用 `\\`
- 括号类型：
    - 圆括号：`pmatrix`
    - 方括号：`bmatrix`
    - 行列式：`vmatrix`

例如: $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$ 对应 `\begin{pmatrix} a & b \\ c & d \end{pmatrix}`

## 参考

- 整体：[菜鸟教程 Markdown 数学公式](https://www.runoob.com/markdown/md-math.html)
- `括号`：[Github Markdown 中的公式书写](https://arthur-delacroix.github.io/2021/03/13/Github/Github%20Markdown%20%E4%B8%AD%E7%9A%84%E5%85%AC%E5%BC%8F%E4%B9%A6%E5%86%99/)
