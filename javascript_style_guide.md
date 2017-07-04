### javascript  编写规范
由于主体项目采用react+webpack的架构，所以编写javascript时请使用ES6规范;  
推荐ES6教程：[阮一峰ES6教程](http://es6.ruanyifeng.com/)  
项目中用的最多的如：  let 和 箭头函数；  

**==下文示例javascript 版本ES6==**
### 1. 命名规范
命名规范用一句话总结：看到名字就能让人知道是什么，能干什么，所见就所想；  
主要涉及变量、函数、常量、构造函数、类的成员等等的命名规范；  

**驼峰式命名法介绍：**  
驼峰式命名法由小(大)写字母开始，后续每个单词首字母都大写。

按照第一个字母是否大写，分为：

① Pascal Case 大驼峰式命名法：首字母大写。StudentInfo、UserInfo、ProductInfo

② Camel Case 小驼峰式命名法：首字母小写。studentInfo、userInfo、productInfo
- #### 变量

  **`【强制】`命名方法**：小驼峰式命名法。

  **`【强制】`命名规范**：前缀应当是名词。(函数的名字前缀为动词，以此区分变量和函数)
    
  **命名建议**：尽量在变量名字中体现所属类型，如:length、count等表示数字类型；而包含name、title表示为字符串类型。  
**示例**：
  
```
// 好的命名方式
let maxLength = 10
let tableTitle = 'LoginTable'
 
// 不好的命名方式
let setCount = 10
let getTitle = 'LoginTable'
```
- #### 函数
  **`【强制】`命名方法**：小驼峰式命名法。

  **`【强制】`命名规范**：前缀应当为动词。

  **命名建议**：可使用常见动词约定。
  

动词 | 含义 | 返回值
---|---|---
can | 判断是否可执行某个动作(权限) |函数返回一个布尔值。true：可执行；false：不可执行
has | 判断是否含有某个值|函数返回一个布尔值。true：含有此值；false：不含有此值
is  | 判断是否为某个值|函数返回一个布尔值。true：为某个值；false：不为某个值
get | 获取某个值|函数返回一个非布尔值
set | 设置某个值|无返回值、返回是否设置成功或者返回链式对象
load | 加载某些数据|无返回值或者返回是否加载完成的结果
handle | 执行某些操作|无返回值或者返回是操作完成的结果

**示例**： 

```
// 是否可阅读
function canRead() {
    return true
}
 
// 获取名称
function getName() {
    return this.name
}
```
- #### 常量
  **`【强制】`命名方法**：名称全部大写。

  **`【强制】`命名规范**：使用大写字母和下划线来组合命名，下划线用以分割单词。

  **命名建议**：所见即所想。
  
**示例**： 
  
```
const MAX_COUNT = 10;
const URL = 'https://www.baidu.com';
```
- #### 构造函数
  **介绍**：在JS中，构造函数也属于函数的一种，只不过采用new 运算符创建对象。

  **`【强制】`命名方法**：大驼峰式命名法，首字母大写。

  **`【强制】`命名规范**：前缀为名称。

  **命名建议**：一般使用含义明确的名词。
  
**示例**： 

```
function Student(name) {
    this.name = name
}
 
let st = new Student('chenym')
```
- #### 类的成员
  类的成员包含：

  **公共属性和方法**：跟变量和函数的命名一样。

  **私有属性和方法**：前缀为_(下划线)，后面跟公共属性和方法一样的命名方式。  
  
  **示例**： 
  

```
function Student(name) {
    let _name = name; // 私有成员
 
    // 公共方法
    this.getName = ()=> {
        return _name;
    }
 
    // 公共方式
    this.setName = (value)=> {
        _name = value;
    }
}
let  st = new Student('chenym');
st.setName('ymchen');
console.log(st.getName()); // => ymchen：输出_name私有变量的值
```
### 2. 注释规范
   JS支持两种不同类型的注释：单行注释和多行注释。  
   
- #### 单行注释
  **说明**：单行注释以两个斜线开始，以行尾结束。

  **语法**：// 这是单行注释

  **使用方式**：

    单独一行：//(双斜线)与注释文字之间保留一个空格。
    
    在代码后面添加注释：//(双斜线)与代码之间保留一个空格，并且//(双斜线)与注释文字之间保留一个空格。
    
    注释代码：//(双斜线)与代码之间保留一个空格。
    
  **示例**：
  
```
// 调用了一个函数；1)单独在一行
setTitle();
 
let maxCount = 10; // 设置最大量；2)在代码后面注释
 
// setName(); // 3)注释代码
```
- #### 多行注释
  **说明**：以/*开头，*/结尾

  **语法**：/* 注释说明 */

  **使用方法**：

  若开始(/* )和结束( */)都在一行，推荐采用单行注释。

  若至少三行注释时，第一行为 /* ，最后行为  * /，其他行以* 开始，并且注释文字与*保留一个空格。 
  
  **示例**：
  
```
/*
* 代码执行到这里后会调用setTitle()函数
* setTitle()：设置title的值
*/
setTitle();
```
- #### 函数(方法)注释
  **说明**：函数(方法)注释也是多行注释的一种，但是包含了特殊的注释要求，参照 [javadoc(百度百科)](http://baike.baidu.com/item/javadoc)。

  **语法**：
```
/** 
* 函数说明 
* @关键字 
*/
```
使用@key desc格式来书写，常用的关键词有：



关键词|	描述
---|---
@auhor|	作者
@param|	参数
@example|	示例
@link|	链接
@namespace|	命名空间
@requires|	依赖模块
@return|	返回值
@version|	版本号
其中，param关键词的格式为：

```
/**
* @param {String} 参数描述
*/
```


**示例**：

```
/**
* 合并Grid的行
* @param grid {Ext.Grid.Panel} 需要合并的Grid
* @param cols {Array} 需要合并列的Index(序号)数组；从0开始计数，序号也包含。
* @param isAllSome {Boolean} ：是否2个tr的cols必须完成一样才能进行合并。true：完成一样；false(默认)：不完全一样
* @return void
* @author polk6 2015/07/21 
* @example
* _________________                             _________________
* |  年龄 |  姓名 |                             |  年龄 |  姓名 |
* -----------------      mergeCells(grid,[0])   -----------------
* |  18   |  张三 |              =>             |       |  张三 |
* -----------------                             -  18   ---------
* |  18   |  王五 |                             |       |  王五 |
* -----------------                             -----------------
*/
function mergeCells(grid, cols, isAllSome) {
    // Do Something
}
```







  



