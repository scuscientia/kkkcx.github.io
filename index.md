## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/kkkcx/kkkcx.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### 第8周周报

一.本周课设要求

分组编写一个满足下列要求的黄金点游戏程序。  
➢ 游戏规则：N个同学（N通常大于10），每人写一个0~100之间的有理数   
(不包括0或100)，交给裁判，裁判算出所有数字的平均值，然后乘以0.618    
(所谓黄金分割常数），得到G值。提交的数字最靠近G（取绝对值）的同   
学得到N分，离G最远的同学得到－2分，其他同学得0分。  
➢ 采用单机方式实现，需要为用户提供便利的输入界面。  
➢ 该游戏每次至少可以运行10轮以上，并能够保留各轮比赛结果。  
➢ 后续在此基础上迭代开发。  

二.本周内完成的任务总结  
搭建博客，结对编程项目组成立，完成立项准备工作，进行需求收集和功能的讨论，以及相关安装环境的搭建

三.学习内容总结

1.结对编程：  
了解结对编程的概念以及如何结对编程：  
在结对编程模式下，一对程序员肩并肩地、平等地、互补地进行开发工作。  
两个程序员并排坐在一台电脑前，面对同一个显示器，使用同一个键盘，同一个鼠标一起工作。  
他们一起分析，一起设计，一起写测试用例，一起编码，一起单元测试，一起集成测试，一起写文档等。

结对编程中有两个角色：  
（a）驾驶员（Driver）是控制键盘输入的人。  
（b）领航员（Navigator）起到领航、提醒的作用。  
这两个角色是可以互换的。和现实生活中的例子类似，一个人负责具体的执行（驾驶，用键盘编辑程序等），另一人负责导航、检查、掩护等。  

为什么要结对编程？  
每人在各自独立设计、实现软件的过程中不免要犯这样那样的错误。  
在结对编程中，因为有随时的复审和交流，程序各方面的质量取决于一对程序员中各方面水平较高的那一位。  
这样，程序中的错误就会少得多，程序的初始质量会高很多，这样会省下很多以后修改、测试的时间。

如何结对编程？  
（1）驾驶员：写设计文档，进行编码和单元测试等XP开发流程。  
（2）领航员：审阅驾驶员的文档、驾驶员对编码等开发流程的执行；考虑单元测试的覆盖程度；是否需要和如何重构；帮助驾驶员解决具体的技术问题。  
（3）驾驶员和领航员不断轮换角色，不宜连续工作超过一小时。领航员要控制时间。  
（4）主动参与。任何一个任务都首先是两个人的责任，也是所有人的责任。没有“我的代码”、“你的代码”或“她的代码”，只有“我们的代码”。  
（5）只有水平上的差距，没有级别上的差异。尽管可能大家的级别资历不同，但不管在分析、设计或编码上，双方都拥有平等的决策权利。  

2.黄金点游戏规则  
N个同学（N通常大于10），每人写一个0~100之间的有理数 (不包括0或100)，交给裁判，裁判算出所有数字的平均值，然后乘以0.618（所谓黄金分割常数），得到G值。  
提交的数字最靠近G（取绝对值）的同学得到N分，离G最远的同学得到－2分，其他同学得0分。  

四.项目状态  
需求收集、项目启动  

五.风险分析及解决办法  
暂无  

### 第9周周报

一.本周课设要求  
继续完善黄金点游戏，添加前端界面  


二.本周内完成的任务总结  

1.实现黄金点游戏逻辑  
   游戏算法（JS实现：）

```javascript
$(function()
{


      var num = 0.0;
      var lun =0;
      var i=1; 
      var j=1;  
      var data= [];
      $('input').keydown(function(event)
	  {
        if(event.keyCode!=8 && (event.keyCode<48 || event.keyCode>57))
		{
           return false; 
        }
      });
      $('#create').click(function(){
        //$('#res').html('');
        num = $('#num').val();
        lun = $('#lun').val();
        if(num == '')
		{
          alert('请填写玩家的数量！');
          return false;
        }
		else if(num>50)
		{
          alert('游戏玩家最多为50人！');
          return false;
        }
        if(lun == '')
		{
          alert('填写游戏轮次！');
          return false;
        }
		else if(lun<2)
		{
          alert('游戏轮次最少为2轮！');
          return false;
        }
        //初始化数组
        for(var a=1;a<=lun;a++)
		{
            data[a] = [];
            for(var b=1;b<=num;b++)
			{
                data[a][b] = 0;
            }
        }
        $('#createGame').css('display','none');//隐藏css中的元素，
        $('#input').css('display','block');
        $('#title').find('.lun').html(lun);
        $('#title').find('.num').html(num);
      });
      $('#test').click(function(){
        
        num = $('#num').val();
        lun = $('#lun').val();
        if(num == '')
		{
          alert('请填写玩家数量！');
          return false;
        }
		else if(num>50)
		{
          alert('玩家最多为50人！');
          return false;
        }
        if(lun == ''){
          alert('请填写游戏轮次！');
          return false;
        }
		else if(lun<2)
		{
          alert('游戏轮次最少为2轮！');
          return false;
        }
        //随机产生数字
        var array = [];
        for(var a=1;a<=lun;a++){
            array[a] = [];
            for(var b=1;b<=num;b++){
                array[a][b] = Math.floor(Math.random()*100);
            }
        }
        count(array,num,lun);
      })
      $('#submit').click(function()
	  {
        var val = $('input[name=val]').val();
        if(val<1 || val>99)
		{
          alert('请输入0~100之间的有理数,不包括0或100');
          return false;
        }
        data[i][j] = val;
        $('input[name=val]').val('');
        j++;
        if(j>num)
		{
          alert('本轮游戏结束，进入下一轮游戏！');
          j=1;
          i++;
          if(i>lun)
		  {
            alert('本次游戏结束！');
            $('#createGame').css('display','block');
            $('#input').css('display','none');
            i = 1;
            j = 1;
           count(data,num,lun);
          }
          $('#now').find('.lun').html(i);
        }
        //重新设置表单内容
        $('#now').find('.num').html(j);
      });
      
    });
```

游戏结果计算及输出：

```javascript
function count(array,num,lun){
        var data = array;
        var s = [];
        //初始化数组
        for(var a=1;a<=lun;a++){
            s[a] = [];
            for(var b=1;b<=num;b++){
                s[a][b] = 0;
            }
        }
        var str = '<tr><td>&nbsp;</td>';
        for(var a=1;a<=num;a++){
          str += "<td>玩家"+a+"</td>";
        }
        str += "<td>总计</td><td>平均</td><td>G</td></tr>";
        
        for(var a=1;a<=lun;a++){
            var sum = 0;
            str += "<tr><td>第"+a+"轮</td>";
            for(var b=1;b<=num;b++){
                sum  += parseInt(data[a][b]);
                //str += "<td>"+data[a][b]+"</td>";
            }
            var avg = sum/num;
            var G = 0.618*avg;
            //获取最大、最小
            var max = Math.abs(data[a][1] - G);  
            var min = Math.abs(data[a][1] - G);
            for(var b=1;b<=num;b++)
			{
              if(Math.abs(data[a][b] - G) >= max)
			  {
                max = Math.abs(data[a][b] - G);
              }
              if(Math.abs(data[a][b] - G) <=min)
			  {
                min = Math.abs(data[a][b] - G);
              }
            }
            for(var b=1;b<=num;b++){
              var score = 0;
              var color = '';
              if(Math.abs(data[a][b]-G) == max){
                score = -2;
                color = 'red';
              }
              if(Math.abs(data[a][b]-G) == min){
                score = num;
                color = 'red';
              }  
             
              /*str += "<td>"+data[a][b]+"("+s+")"+score+","+max_index+","+min_index+"</td>";*/
              s[a][b] = score;
              str += "<td style='color:"+color+"'>"+data[a][b]+"("+score+")</td>";
              
            }
            str += "<td>"+sum+"</td><td>"+avg+"</td><td>"+G+"</td></tr>";
        }
        var res = [];
        str += '<tr><td>计分</td>';
        for(var b=1;b<=num;b++){
          var sum = 0;
          for(var a=1;a<=lun;a++){
            sum  += parseInt(s[a][b]);
          }
          res[b] = sum;
        }
        var max_res = res[1];
        var min_res = res[1];
        for(var c=2;c<=num;c++){
          if(res[c] > max_res){
            max_res = res[c];
          }
          if(res[c] < min_res){
            min_res = res[c];
          }
        }
        var winner = '';
        var loser = '';
        for(var c=1;c<=num;c++){
          var res_color = '';
          if(res[c] == max_res){
            res_color = 'red';
            winner += '玩家'+c+',';
          }
          if(res[c] == min_res){
            res_color = 'red';
            loser += '玩家'+c+',';
          }
          str += "<td style='color:"+res_color+"'>"+res[c]+"</td>";
        }
        winner += '获胜<br>';
        loser += '输了';
 
        str += "<td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>";
        var col = parseInt(num)+3;
        str += "<tr><td>结果</td><td style='color:red' colspan='"+col+"'>"+winner+loser+"</td></tr>";
        $('#res').html(str);
        
    }
```



2.为黄金点游戏设计ui界面  
页面设计




```html
<body>
  <div class="showTime">当前时间：2020年3月17-0时54分14秒</div>
  <script>
    var t = null;
    t = setTimeout(time, 1000); //開始运行
    function time() {
      clearTimeout(t); //清除定时器
      dt = new Date();
      var y = dt.getFullYear();
      var mt = dt.getMonth() + 1;
      var day = dt.getDate();
      var h = dt.getHours(); //获取时
      var m = dt.getMinutes(); //获取分
      var s = dt.getSeconds(); //获取秒
      document.querySelector(".showTime").innerHTML =
        "当前时间：" +
        y +
        "年" +
        mt +
        "月" +
        day +
        "-" +
        h +
        "时" +
        m +
        "分" +
        s +
        "秒";
      t = setTimeout(time, 1000); //设定定时器，循环运行
    }
  </script>
<div id="container">
<h2> 黄金点游戏</h2>
<div id="div1">
	<div id="CreateGame">
    	<table>

        <tr>
        <td>玩家人数:</td>
        <td><input type="text" id="num" class=""></td>
        </tr>
        <tr>
        <td>游戏轮次：</td>
        <td><input type="text" id="lun" class=""></td>
        </tr>        
        </table>
        <table>
        <tr align="center"><td><button id="create">创建游戏</button></td><td><button id="test">模拟游戏</button></td></tr>
        
        </table>
        </div>
</div>
<div id="input">
      <table>
        <tr align="center" id="title">
          <td colspan="3">本次游戏共<span class="lun"></span>轮，玩家人数为<span  class="num"></span>人</td>
        </tr>
        <tr align="center" id="now">
          <td colspan="3">当前轮次：第<span class="lun">1</span>轮，当前玩家为：玩家<span  class="num">1</span></td>
        </tr>
        <tr>
          <td align="right">请输入数字：</td>
          <td><input type="text" name="val" class="val"></td>
          <td><span style="color:red;">(提示！0~100之间的有理数,不包括0或100)</span></td>
        </tr>
        <tr align="center">
          <td colspan="3"><button id="submit">提交</button></td>
        </tr>
      </table>
    </div>
    <table id="res" border='1px' style="margin-bottom:160px"></table>
</div>
<p>四川大学软件工程课程设计</p>
<p>胡斌 康采新</p>
<a href="mailto:1127235750@qq.com">联系我们</a>
</body>
```
3.项目改进：
  + 增加注册页面
  + 优化页面UI设计
  + 设计构建用户数据库
  + 改变提示信息弹出方式
  + 游戏数据可视化
  


三.学习内容总结  
学习使用jsp将黄金点游戏在网页端进行实现  


四.项目状态  
进行项目构建和编码  


五.风险分析及解决办法    

风险分析：  
在实践需求过程中遇到一些之前理解不清的地方，需要落实  

解决办法：  
加强交流沟通，理解需求  




### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
