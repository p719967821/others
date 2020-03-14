##做qq小程序的一些经验记录
***
**1. html中class，style，id的区别**
class：就相当于一个类，在body中引用后要在其他地方定义
id：相当于一个替代品
style：相当于.html中的css，可以直接inline也可以用作一个标签单独定义
**2. 对路径的了解（已完全了解）**
比如同文件夹下的practice中的practice.md是D:/qq_html/practice/practice.md要向其中插入图片有两种方法 
- 绝对路径
    - 网图   直接看其路径复制下来就行，稳定
    - 本地绝对路径 从根目录开始写，windows根目录就是c盘，d盘，比如上面这个路径就是绝对路径
- 相对路径
    以practice文件夹为基准
    前提：d盘下有qq_html和picture文件夹，picture中有1.npg，qq_html中有practice文件夹和2.png文件，practice下有practice.html和3.png和abc文件夹，abc文件夹下有4.png
    - 则要用1.png 相对路径: ../../picture/1.png(或直接用一个/代表从根目录开始，即/practice/1.png，就不用从当前位置往上一级推)
    - 则要用2.png 相对路径: ../2.png（同上，也可用/qq_html/2.png表示）
    - 则要用3.png 相对路径: 3.png 或./3.png(./代表当前的位置，前面的路径用一个.表示)
    - 则要用4.png 相对路径: abc/4.png

**3. 一边模仿一边记录**
css    
    padding-top/bottom/left/right：5px  边距 
    opacity：透明度，在0到1之间，0是完全透明，1是不透明
    display：用flex盒子分布
    flex-dirction raw 横向排列
    border： 1px soild #eee 边框的设置，第一个是大小，第二个是边框的形状（dotted，soild，double，dashed），第三个是边框的颜色
    position：位置，relative相对位置，fixed、absolute
    margin:设置 p 元素的 4 个外边距，可以是
            margin：2cm，3cm，4cm，5cm（上右下左）
            margin：auto
html


bindtap：事件是视图层到逻辑层的通讯方式，可以将用户的行为反馈到逻辑层进行处理。在组件中绑定一个事件处理函数，如bindtap，详见微信小程序开发框架-事件[(点这里)](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/event.html)


this.setData():[点这里](https://blog.csdn.net/qq_38595560/article/details/81565925)


data-idx="{{index}}"：只有这种形式，才能把wxml中的东西用到js中（在wxml中可以直接用index和item），存储一些数据供home.js里调用，这里data-xxx，xxx就是你给home.js里提供的数据关键词，home.js通过获取xxx关键词来获取xxx里面的数据，而开发文档中的wx:for-index="idx",好像就只是重命名的作用，而且只能在wxml中用，不能到js中使用。


{{ss}}：是在js中定义ss的值，而在html中用ss来代替值的大小，相当于一个变量

console.log()是指在显示台中展现相应的数据

 wx.XXX是要放在一个函数内使用的，不能单独作为一个函数。
**4. 图片的css调节**
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 5px;
**5. css中px，em，rem等的认识**
    [如链接](https://blog.csdn.net/jyy_12/article/details/42557241)
**6. 什么是api，以及它的作用**
 [通俗易懂的解释](https://blog.csdn.net/cumtdeyurenjie/article/details/80211896)
 api相当于是这种方法，是一个整体,在开发实际中相当于那个wx.login之类的一些调用函数
 接口（interface）相当于是中间的那个区域
 协议和格式见文章
**7. var that=this是什么意思**
    因为this代指此时的数据对象，在数据运行的过程中，对象会发生变化，所以要把this的对象赋给that，以免此时的对象丢失。
**8.转跳界面制作**
    html：将需要点击的位置用view框起来，然后用bindtap属性定义一个函数a
    js：在a函数中调用wx.navigator函数，在url中确定转跳的位置即可
**9.点击后出现成功提示**
    html：将需要点击的位置用catchtap属性定义一个函数a
    js：在a函数中调用wx.showToast函数，
**10. 微信小程序的alert**
    目前来说，微信小程序中没有window.alert（），不过有一个功能相同的wx.showToast函数来实现相同的功能
**11. bindtap**
    这是一个点击事件，在html中定义一个函数abc，当点击cde部分是就会调用js中的abc函数的内容
    html：在 《view bindtap="abc"》cde《/view》<font color="red">（<>显示不出来，用《》代替）</font>
    js:&nbsp;  abc:function(){}
**12. 如何使用全局变量**
    [如何使用全局变量](https://blog.csdn.net/michael_ouyang/article/details/54923784)
    在app.js中定义globalData后，在其他的js中，只要在最开始用var xxx=getApp（）就可以在后面的函数中使用xxx.globalData.
**12. js中的数据**
    对于在js中的一些具体的数据，就统一写在最前面，data：{}
    如果只有一个就不用{}，直接data：1如果有多个，就
    data：{
        option：1，
        assign：2，
        appointed：3
        }
**13. 模块化**
我们可以将一些公共的代码抽离成为一个单独的 js 文件，作为一个模块。模块只有通过 module.exports 或者 exports 才能对外暴露接口。
a.js
>function:sayhello(name)
{
    console.log('hello ${name}!')
}
>    module.exports={sayhello:sayhello}

b.js
>var common=require('a.js')
Page({
    geta:function(){
        common.sayhello('Jill')
    }
>})

**14. 注释**
js中用（斜杠斜杠）或（斜杠星fsfdd斜杠星）
json中不能加注释
wxml中用（小括号叹号杠杠dddf杠杠小括号）
wxss中用（斜杠星星ads星星斜杠）
**参考资料（十分感谢）**
[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/event.html)
[个人中心版面](https://blog.csdn.net/qq_38194393/article/details/88572380)
[链接二](https://www.jianshu.com/u/b4a296d6ebee)
[转跳方式](https://www.php.cn/xiaochengxu-408480.html)
[商家评价主](https://blog.csdn.net/qq_35086913/article/details/85265938)    ([商家评价辅](https://blog.csdn.net/qq_38194393/article/details/88844121))
[微信小程序的一个很全的教程](https://blog.csdn.net/michael_ouyang/article/details/54923052)
[微信小程序登录原理](https://blog.csdn.net/michael_ouyang/article/details/72635263)
[wxss大全](https://www.cnblogs.com/yang-shuai/p/6899430.html)
***