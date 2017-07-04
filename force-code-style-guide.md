### `[@@] JavaScript强制要求 [@@]`

#### 变量

**`【强制】`命名方法**：小驼峰式命名法。

**`【强制】`命名规范**：前缀应当是名词。(函数的名字前缀为动词，以此区分变量和函数)


#### 函数
**`【强制】`命名方法**：小驼峰式命名法。

**`【强制】`命名规范**：前缀应当为动词。


#### 常量
**`【强制】`命名方法**：名称全部大写。

**`【强制】`命名规范**：使用大写字母和下划线来组合命名，下划线用以分割单词。

#### 构造函数

**`【强制】`命名方法**：大驼峰式命名法，首字母大写。

**`【强制】`命名规范**：前缀为名称。

---
### `[@@] CSS强制要求 [@@]`


#### `【强制】` 使用 `4` 个空格长度的Tab做为一个缩进层级，不允许使用 `2` 个空格字符。[注] sublime等编辑器可以支持。

示例：

```css
.selector {
	margin: 0;
	padding: 0;
}
```

#### `【强制】` `>`、`+`、`~` 选择器的两边各保留一个空格。

示例：

```css
/* good */
main > nav {
	padding: 10px;
}

label + input {
	margin-left: 5px;
}

input:checked ~ button {
	background-color: #69C;
}

/* bad */
main>nav {
	padding: 10px;
}

label+input {
	margin-left: 5px;
}

input:checked~button {
	background-color: #69C;
}
```
#### `【强制】` 属性选择器中的值必须用双引号包围。

解释：

不允许使用单引号，不允许不使用引号。


示例：

```css
/* good */
article[character="juliet"] {
	voice-family: "Vivien Leigh", victoria, female;
}

/* bad */
article[character='juliet'] {
	voice-family: "Vivien Leigh", victoria, female;
}
```

#### `【强制】` 属性定义必须另起一行。


示例：

```css
/* good */
.selector {
	margin: 0;
	padding: 0;
}

/* bad */
.selector { margin: 0; padding: 0; }
```


#### `【强制】` 属性定义后必须以分号结尾。

示例：

```css
/* good */
.selector {
	margin: 0;
}

/* bad */
.selector {
	margin: 0
}
```


#### `【强制】` 如无必要，不得为 `id`、`class` 选择器添加类型选择器进行限定。

解释：

在性能和维护性上，都有一定的影响。


示例：


```css
/* good */
#error,
.danger-message {
	font-color: #c00;
}

/* bad */
dialog#error,
p.danger-message {
	font-color: #c00;
}
```

#### `【强制】` 文本内容必须用双引号包围。

解释：

文本类型的内容可能在选择器、属性值等内容中。

示例：

```css
/* good */
html[lang|="zh"] q:before {
	font-family: "Microsoft YaHei", sans-serif;
	content: "“";
}

/* bad */
html[lang|=zh] q:before {
	font-family: 'Microsoft YaHei', sans-serif;
	content: '“';
}
 
```

#### `【强制】` 当数值为 0 - 1 之间的小数时，省略整数部分的 `0`。

示例：

```css
/* good */
panel {
	opacity: .8;
}

/* bad */
panel {
	opacity: 0.8;
}
```

#### `【强制】` `url()` 函数中的路径不加引号。

示例：

```css
body {
	background: url(bg.png);
}
```


#### `【强制】` 长度为 `0` 时须省略单位。 (也只有长度单位可省)

示例：

```css
/* good */
body {
	padding: 0 5px;
}

/* bad */
body {
	padding: 0px 5px;
}
```

#### `【强制】` RGB颜色值必须使用十六进制记号形式 `#rrggbb`。不允许使用 `rgb()`。 

解释：

带有alpha的颜色信息可以使用 `rgba()`。使用 `rgba()` 时每个逗号后必须保留一个空格。

示例：

```css
/* good */
.success {
	box-shadow: 0 0 2px rgba(0, 128, 0, .3);
	border-color: #008000;
}

/* bad */
.success {
	box-shadow: 0 0 2px rgba(0,128,0,.3);
	border-color: rgb(0, 128, 0);
}
```

#### `【强制】` 颜色值可以缩写时，必须使用缩写形式。

示例：

```css
/* good */
.success {
	background-color: #aca;
}

/* bad */
.success {
	background-color: #aaccaa;
}
```

#### `【强制】` 颜色值不允许使用命名色值。

示例：

```css
/* good */
.success {
	color: #90ee90;
}

/* bad */
.success {
	color: lightgreen;
}
```

#### `【强制】` 需要在 Windows 平台显示的中文内容，其字号应不小于 `12px`。

解释：

由于 Windows 的字体渲染机制，小于 `12px` 的文字显示效果极差、难以辨认。

---

### `[@@] LESS强制要求 [@@]`

**`【强制】`嵌套**：嵌套的声明块前必须（MUST）增加一次缩进，嵌套层级不要过深，理论上不超过3层。 

---

### `[@@] React强制要求 [@@]`

#### 【强制】对齐，参考下面的格式 

```
// bad
<Foo superLongParam="bar"
	anotherSuperLongParam="baz" />

// good
<Foo
	superLongParam="bar"
	anotherSuperLongParam="baz"
/>

// if props fit in one line then keep it on the same line
<Foo bar="bar" />

// children get indented normally
<Foo
	superLongParam="bar"
	anotherSuperLongParam="baz"
>
	<Spazz />
</Foo>
```

#### 【强制】空格，在自闭和标签之前留一个空格

```
// bad
<Foo/>
// very bad
<Foo                 />
// bad
<Foo
 />
// good
<Foo />
```

#### 【强制】括号，当组件跨行时，要用括号包裹 JSX 标签。

```
/// bad
render() {
	return <MyComponent className="long body" foo="bar">
	<MyChild />
	</MyComponent>;
}

// good
render() {
	return (
		<MyComponent className="long body" foo="bar">
			<MyChild />
		</MyComponent>
	);
}

// good, when single line
render() {
	const body = <div>hello</div>;
	return <MyComponent>{body}</MyComponent>;
}
```

#### 【强制】方法，不要对 React 组件的内置方法使用 `underscore` 前缀

```
// bad
React.createClass({
    _onClickSubmit() {
        // do stuff
    }
    // other stuff
});
// good
class extends React.Component {
    onClickSubmit() {
        // do stuff
    }
    // other stuff
});
```