# Markdown 入门指南
## 导语
> Markdown 是一种轻量级的「标记语言」
常用的标记符号也不超过十个，这种相对于更为复杂的 HTML 标记语言来说，Markdown 可谓是十分轻量的，学习成本也不需要太多。

## Markdown 官方文档
> [创始人 John Gruber 的 Markdown 语法说明](http://daringfireball.net/projects/markdown/syntax)

>[Markdown 中文版语法说明](http://www.appinn.com/markdown/) 

##编辑工具
**mac os X**：你可以使用强无敌的[Mou](http://25.io/mou/) : 实时预览，偏好设置（Preference），主题设置（Themes），样式（CSS）
> 如果对自带主题样式不满意，可以在github上搜索其它爱好者为 Mou 编写的更多主题样式，导入的方式可以在偏好设置的 Themes 或 CSS 选项中 选择 reload。

**window**:你可以使用[Markpad](http://code52.org/DownmarkerWPF/) :好不好我不知道，反正我用的是它~支持实时预览。

**web端**：你可以使用[简书](http://www.jianshu.com/)，只需要注册登陆，就可以开始你的创作
> 登陆后，可以在用户设置里面将**常用编辑器**设置为Markdown

##Markdown 语法规则
###标题
只需要在文字前面加 # 号就可以定义标题 
>  \#  一级标题

>   \##  二级标题

>   \###  三级标题

###列表
有序/无序列表:无序列表只需要在文字前面加 * 号或者 - 号；有序列表直接1.，2.，3.加文字，注意：符号要和文字之间加上一个字符的**空格**
> *p1

> *p2

> *p3

###引用
只需要在文字前面加 > 号（大括号）即可
 
 > eg： > test 注意符号和文字之间是有一个字符**空格**的

###粗体和斜体
 > 粗体：需要用一对俩个 * 号，将想要实现粗体效果的文本**包裹**起来 

 >  斜体：用一对单个 * 号，将想要实现斜体效果的文本**包裹**起来

###代码框
只需要用一对单个（`） ，将代码片段包裹起来：
> eg ：\` printf() ` 

###图片和链接
插入链接与插入图片的语法很像，区别在一个 !号

链接为：`[]()`

图片为：`![]()`

> 插入百度链接：`[baidi](http://baidu.com)`

> 插入百度图片 `![baidu](https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png)`

###反斜杠
Markdown 可以利用反斜杠来帮助插入普通的符号，只需要在想插入的普通符号前面加 \ 即可。

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
> \`   反引号

> \*   星号

> \_   底线

> \{}  花括号

> \[]  方括号

> \()  括弧

> \#   井字号

> \+   加号

> \-   减号

> \.   英文句点

> \!   惊叹号

###分隔符
- - -    
你可以用三个以上的 * 号或者 - 号 来实现分隔符，注意行内不能有其他东西，除了空格
> * \---
> 
> * \***
> 
> * \* \* \*
> 
> * \- - -

###表格
表格比较累人，例子如下(去掉 * 号)
***
\| Tables        | Are           | Cool  |  

\| ------------- |:-------------:| -----:|

\| col 3 is      | right-aligned | $1600 | 

\| col 2 is      | centered      |   $12 |

\| zebra stripes | are neat      |    $1 | 
***

效果如下：

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
***
###全文完
<img src="http://i1.buimg.com/569521/95e0482dea622035.jpg"alt='pinterest' height=500 >