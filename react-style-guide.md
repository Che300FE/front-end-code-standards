# React编码规范

## 基本规则
* 每个文件只包含一个 React 组件
* 使用 `JSX` 语法
* 除非是从一个非 `JSX` 文件中初始化 app，否则不要使用 `React.createElement`

## 命名
* **扩展名:** 使用 `jsx` 作为 React 组件的扩展名
* **文件名:** 文件命名采用帕斯卡命名法，如：`ReservationCard.jsx`
* **引用名:**  组件引用采用帕斯卡命名法，其实例采用驼峰式命名法。

## 对齐
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

## 引号

* 对于 `JSX` 使用双引号，对其它所有 JS 属性使用单引号

```

     // bad
      <Foo bar='bar' />
      // good
      <Foo bar="bar" />
      // bad
      <Foo style={{ left: "20px" }} />
      // good
      <Foo style={{ left: '20px' }} />
```

## 空格

* 在自闭和标签之前留一个空格

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

## 属性

* 属性名采用驼峰式命名法

```

    // bad
    <Foo
      UserName="hello"
      phone_number={12345678}
    />
    // good
    <Foo
      userName="hello"
      phoneNumber={12345678}
    />

```


## 括号
* 当组件跨行时，要用括号包裹 JSX 标签。

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

## 标签

* 没有子组件的父组件使用自闭和标签。

```

    // bad
      <Foo className="stuff"></Foo>
      // good
      <Foo className="stuff" />
```
* 如果组件有多行属性，闭合标签应写在新的一行上。


```

    // bad
      <Foo
        bar="bar"
        baz="baz" />
      // good
      <Foo
        bar="bar"
        baz="baz"
      />
```

## 方法

* 不要对 React 组件的内置方法使用 `underscore` 前缀


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
