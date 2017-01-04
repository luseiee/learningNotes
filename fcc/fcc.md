Title         : FreeCodeCamp
Author        : Lu, Phil

[TITLE]

# Html & Css
- id只能有一个，多个元素可以是一个class
- padding是元素的大小，margin是元素旁边的边界的大小。  
就好比padding是我人多大，而margin是我占了多大一块地方
- css发生冲突时，self>id > class
```html
  <h1 style="color: green" id="orange-text" class="pink-text blue-text">Hello World!</h1>
```
- 属性后面加上! important可以防止被覆盖  
```html
  .pink-text {
    color: pink !important;
  }
```
- body标签代表整个页面的内容，属于html内，与head并列

# Bootstrap
> Bootstrap将会根据你的屏幕的大小来调整HTML元素的大小 —— 强调 响应式设计的概念。
通过响应式设计，你无需再为你的网站设计一个手机版的。它在任何尺寸的屏幕上看起来都会不错。

- 我们需要把所有的HTML内容放在class为container-fluid的div下。
- 通过使用 span 元素，你可以把几个元素放在一起。你甚至可以用此为一个元素的不同部分指定样式。
```html
  <p>Things cats <span class="text-danger">love</span>:</p>
```
- 把div带上class=row，然后在其中用div class="col-md-*"则可以去适应宽度，一共等分成12份
```
  <div class="row">
    <div class="col-xs-8">
      <h2 class="text-primary text-center">CatPhotoApp</h2>
    </div>
    <div class="col-xs-4">
      <a href="#"><img class="img-responsive thick-green-border" src="/images/relaxing-cat.jpg"></a>
    </div>
  </div>
```

# Font Awesome
> Font Awesome 是一个非常方便的图标库。这些图标都是矢量图形，被保存在 .svg 的文件格式中。这些图标就和字体一样，你可以通过像素单位指定它们的大小，它们将会继承其父HTML元素的字体大小。

- 
```
  <link rel="stylesheet" href="//cdn.bootcss.com/font-awesome/4.2.0/css/font-awesome.min.css"/>
```
- 像这样可以给文字旁边插上矢量小图标
```html
  <button class="btn btn-block btn-danger"><i class="fa fa-trash"></i> Delete</button>
```

# jQuery
> 最流行的JavaScript库jQuery

- 在没有document ready function以前，你的代码会在HTML没有渲染完成就执行，这样会产生bug。
```javascript
<script>
  $(document).ready(function() {
    $("button").addClass("animated bounce");    选择器方式，增加与删除class
    $(".well").addClass("animated shake");
    $("#target3").addClass("animated fadeOut");
    $("button").removeClass("btn-default");
    $("#target1").css("color", "blue");         设置css，css的属性和值用逗号分开
    $("button").prop("disabled", true);         prop用于改变属性，注意属性和css不同，css是在style里的
    $("h3").html("<em>jQuery Playground</em>");   修改标签内的内容，另外还有.text()方法，里面的所有符号会被转义成文本
    $("#target4").remove();                       移除元素
    $("#target2").appendTo("#right-well");      把某个元素移动到另一个div中去
    $("#target2").clone().appendTo("#right-well");   多个方法可以一起用
    $("#target1").parent().css("background-color", "blue");  访问父元素
    $("#right-well").children().css("color", "orange")     访问子元素
    $(".target:nth-child(3)").addClass("animated bounce");   存疑
    $($(".slot")[0]).html(slotOne);     选取第一个class为slot的元素，并将其内容设为slotOne
  });
</script>
```
```javascript
  $(function() {...}); //好像是带document.ready的简写方式？
```
- 我们已经在后台为你引入了jQuery库和Animate.css库
- 注意选择方式和css是差不多滴

# JavaScript
- var a 来定义变量
- 未初始化的变量，程序内部会给它一个值undefined
```JavaScript
  var a;     
  var c;
 a = a + 1;        
 c = c + " String!";
 Output:
 a = NaN, b = NaN, c = 'undefined String!'
```
- 变量命名请用驼峰命名法
- 字符串中请使用 \\ 来进行转义
- 字符串a, a.length获取长度, a\[0\]获取第0位字符
- String Immutability字符串不可变性
```JavaScript
  var myStr = "Jello World";
  myStr[0] = "H"; //这行会报错
  myStr = "Hello World";
```
- 数组
```JavaScript
  var array = ["John", 23];
```
- array.push(n), 把n放到数组最末端
- array.pop(),把最后一个数组元素取出来
- array.shift(),取出第一个元素
- 3 == '3' is true
- 3 === '3' is false
- 同理 != !==
- && ||
- 函数
- 对象,感觉好像字典
```JavaScript
  var ourDog = {
    "name": "Camper",
    "legs": 4,
    "tails": 1,
    "friends": ["everything!"]
  };
  ourDog.name;    //访问属性
  ourDog["name"];  //the same
  ourDog.sex = "male"; //添加属性
  delete ourDog.tails; //删除属性
```
> JavaScript Object Notation 简称 JSON，它使用JavaScript对象的格式来存储数据。JSON是灵活的，因为它允许 数据结构 是 字符串，数字，布尔值，字符串，和 对象 的任意组合。

- 嵌套的JSON对象
 
```JavaScript
  var myStorage = {
    "car": {
      "inside": {
        "glove box": "maps",
        "passenger seat": "crumbs"
      },
      "outside": {
        "trunk": "jack"
      }
    }
  };
  // 这是一个嵌套的JSON对象 
  var gloveBoxContents = myStorage.car.inside["glove box"]; // Change this line
  myStorage.hasOwnProperty;  //
  
```
- for循环
```JavaScript
  for (var i = 0; i < 10; i += 2) {
    ourArray.push(i);
  }
```

# Object Oriented and Functional Coding

- 这种写法很类似于python的类了，称为js的面向对向和函数编程

```javaScript
  var Bike = function() {
    this.wheels = 1; //这种就可以用myBike.wheels来访问
    var gear = 4; //把属性设为var则无法通过外界访问，比如myBike.gear
    
    this.getGear = function() {  //这两种就是熟悉的类的方法啦
      return this.gear;
    };
    this.setGear = function(g) {
      this.gear = g;
    };
  };
  myBike = new Bike(); //这种方式创建对象
```

- 数组有一个map方法，接收一个函数，可以对数组中的每一个元素进行操作

```javaScript
  var timesFour = oldArray.map(function(val){
    return val * 4;
  });
```

- 数组还有一个reduce方法，每次对下一个值进行操作，reduce接受一个函数和一个可选的第二个值作为初始值

```javaScript
  var singleVal = array.reduce(function(previousVal, currentVal) {
    return previousVal - currentVal;
  }, 0);
```

- 数组的filter方法，留下返回为true的值

```javaScript
  var newArray = oldArray.filter(function(val) {
    return val<6;});
```

- 数组的sort方法，函数的返回值大的判为大

```javascript
  var array = [1, 12, 21, 2];
  array.sort(function(a, b) {
    return a - b;
  });
```
> Attention,array.sort()是按字符串排序的，不是按数字大小哦

- Array.reverse() 反转数组

- Array.concat(anotherArray) 连接数组

- string = Array.join(" ")

- string的一些函数
```javascript
  str.replace(re_or_substr, new_str) //替换,支持正则表达式，这个是不会改变原来的str的
  str.toLowerCase()
  str.replace("a") //用a来分割字符串并返回一个数组
  str.slice(start [,end]) //字符串切片, 同样的，array也有这种语法
```

- 如何判断NaN, NaN == NaN返回值是false！！

- 算法题里有一道题不知道怎么传入额外传入的参数
```javascript
  function destroyer(arr) {
    // Remove all the values
    var args = Array.prototype.slice.call(arguments); //这两行很重要！！
    a = args.splice(1);   //取出第二项开始的内容
    var ret = arr.filter(function(val) {
      for (var i = 0; i < a.length; i++) {
        if (val == a[i])
          return false
      }
      return true
    })
    return ret;
  }
  
  destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

# JSON APIs and Ajax

```javascript
  <script>
  $(document).ready(function() {
      $("#getMessage").on("click", function() {
        $.getJSON("/json/cats.json", function(json) {  
          var html = "";
          json = json.filter(function(val) {
            return (val.id !== 1);
          });
          json.forEach(function(val) {
            html += "<div class = 'cat'>"
            html += "<img src = '" + val.imageLink + "'>"
            html += "</div>"
          });
          $(".message").html(html);
        });
      });
    });
  </script>
  <div class="container-fluid">
    <div class = "row text-center">
      <h2>Cat Photo Finder</h2>
    </div>
    <div class = "row text-center">
      <div class = "col-xs-12 well message">
        The message will go here
      </div>
    </div>
    <div class = "row text-center">
      <div class = "col-xs-12">
        <button id = "getMessage" class = "btn btn-primary">
          Get Message
        </button>
      </div>
    </div>
  </div>
```
- 这段代码干了这么一件事情，从#getMessage button事件被触发，获取json文件，然后处理json对象，并应json的
一些函数去做处理，并返回html代码动态加入原代码中。

> 当你需要根据服务器返回的数据来动态改变页面的时候，应用程序接口(API)就派上用场了。  
记住，API——应用程序接口(Application Programming Interface)是计算机之间相互交流沟通的工具。  
许多网站的应用程序接口(API)都是通过一种称为JSON格式的数据来传输的，JSON 是 JavaScript Object Notation的简写。

- 目前的理解，JSON API就是从其他url获取数据的接口

- Ajax则是一种技术，比如onclick了之后去部分改变代码

> AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。  
AJAX 不是新的编程语言，而是一种使用现有标准的新方法。  
AJAX 是与服务器交换数据并更新部分网页的艺术，在不重新加载整个页面的情况下。












---

---

# Codes
## 小猫app
```html
<link href="//fonts.gdgdocs.org/css?family=Lobster" rel="stylesheet" type="text/css">
<style>
  h2 {
    font-family: Lobster, Monospace;
  }

  .thick-green-border {
    border-color: green;
    border-width: 10px;
    border-style: solid;
    border-radius: 50%;
  }

</style>

<div class="container-fluid">
  <div class="row">
    <div class="col-xs-8">
      <h2 class="text-primary text-center">CatPhotoApp</h2>
    </div>
    <div class="col-xs-4">
      <a href="#"><img class="img-responsive thick-green-border" src="/images/relaxing-cat.jpg"></a>
    </div>
  </div>
  <img src="/images/running-cat.jpg" class="img-responsive">
  <div class="row">
    <div class="col-xs-4">
      <button class="btn btn-block btn-primary"><i class="fa fa-thumbs-up"></i> Like</button>
    </div>
    <div class="col-xs-4">
      <button class="btn btn-block btn-info"><i class="fa fa-info-circle"></i> Info</button>
    </div>
    <div class="col-xs-4">
      <button class="btn btn-block btn-danger"><i class="fa fa-trash"></i> Delete</button>
    </div>
  </div>
  <p>Things cats <span class="text-danger">love:</span></p>
  <ul>
    <li>cat nip</li>
    <li>laser pointers</li>
    <li>lasagna</li>
  </ul>
  <p>Top 3 things cats hate:</p>
  <ol>
    <li>flea treatment</li>
    <li>thunder</li>
    <li>other cats</li>
  </ol>
  <form action="/submit-cat-photo">
    <div class="row">
      <div class="col-xs-6">
        <label><input type="radio" name="indoor-outdoor"> Indoor</label>
      </div>
      <div class="col-xs-6">
        <label><input type="radio" name="indoor-outdoor"> Outdoor</label>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-4">
        <label><input type="checkbox" name="personality"> Love</label>
      </div>
      <div class="col-xs-4">
        <label><input type="checkbox" name="personality"> Lazy</label>
      </div>
      <div class="col-xs-4">
        <label><input type="checkbox" name="personality"> Crazy</label>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-7">
    <input type="text" class="form-control" placeholder="cat photo URL" required>
      </div>
      <div class="col-xs-5">
    <button type="submit" class="btn btn-primary"><i class="fa fa-paper-plane"></i> Submit</button>
      </div>
    </div>
  </form>
</div>
```

## 老虎机
![app2]

[app2]: images/app2.png "app2" { width:auto; max-width:90% }

```html
<script>
  function runSlots() {
    var slotOne;
    var slotTwo;
    var slotThree;
    
    var images = ["//i.imgur.com/9H17QFk.png", "//i.imgur.com/9RmpXTy.png", "//i.imgur.com/VJnmtt5.png"];
    
    slotOne = Math.floor(Math.random() * (3 - 1 + 1)) + 1;
    slotTwo = Math.floor(Math.random() * (3 - 1 + 1)) + 1;
    slotThree = Math.floor(Math.random() * (3 - 1 + 1)) + 1;
    
    
    // Only change code below this line.
    $($('.slot')[0]).html('<img src = "' + images[slotOne-1] + '">');
    $($('.slot')[1]).html('<img src = "' + images[slotTwo-1] + '">');
    $($('.slot')[2]).html('<img src = "' + images[slotThree-1] + '">');
    
    
    // Only change code above this line.
    
    if (slotOne === slotTwo && slotTwo === slotThree) {
      $('.logger').html("It's A Win");
      return null;
    }
    
    if (slotOne !== undefined && slotTwo !== undefined && slotThree !== undefined){
      $(".logger").html(slotOne + " " + slotTwo + " " + slotThree);
    }
    
    $('.logger').append(" Not A Win");
    
    return [slotOne, slotTwo, slotThree];
  }

  $(document).ready(function() {
     $('.go').click(function() {
       runSlots();
     });
   });
</script>
 
<div>
 <div class = 'container inset'>
   <div class = 'header inset'>
     <img src='/images/freecodecamp_logo.svg' alt='learn to code JavaScript at Free Code Camp logo' class='img-responsive nav-logo'>
     <h2>FCC Slot Machine</h2>
   </div>
   <div class = 'slots inset'>
     <div class = 'slot inset'>
       
     </div>
     <div class = 'slot inset'>
       
     </div>
     <div class = 'slot inset'>
       
     </div>
   </div>
   <br/>
   <div class = 'outset'>
     <button class = 'go inset'>
       Go
     </button>
   </div>
   <br/>
   <div class = 'foot inset'>
     <span class = 'logger'></span>
   </div>
 </div>
</div>

<style>
 .slot > img {
  margin: 0!important;
  height: 71px;
  width: 50px;
 }
 .container {
   background-color: #4a2b0f;
   height: 400px;
   width: 260px;
   margin: 50px auto;
   border-radius: 4px;
 }
 .header {
   border: 2px solid #fff;
   border-radius: 4px;
   height: 55px;
   margin: 14px auto;
   background-color: #457f86
 }
 .header h2 {
   height: 30px;
   margin: auto;
 }
 .header h2 {
   font-size: 14px;
   margin: 0 0;
   padding: 0;
   color: #fff;
   text-align: center;
 }
 .slots{
   display: flex;
   background-color: #457f86;
   border-radius: 6px;
   border: 2px solid #fff;
 }
 .slot{
   flex: 1 0 auto;
   background: white;
   height: 75px;
   width: 50px;
   margin: 8px;
   border: 2px solid #215f1e;
   border-radius: 4px;
   text-align: center;
 }
 .go {
   width: 100%;
   color: #fff;
   background-color: #457f86;
   border: 2px solid #fff;
   border-radius: 2px;
   box-sizing: none;
   outline: none!important;
 }
 .foot {
   height: 150px;
   background-color: 457f86;
   border: 2px solid #fff;
 }
 
 .logger {
   color: white;
   margin: 10px;
 }
 
 .outset {
   -webkit-box-shadow: 0px 0px 15px -2px rgba(0,0,0,0.75);
   -moz-box-shadow: 0px 0px 15px -2px rgba(0,0,0,0.75);
     box-shadow: 0px 0px 15px -2px rgba(0,0,0,0.75);
 }
 
 .inset {
   -webkit-box-shadow: inset 0px 0px 15px -2px rgba(0,0,0,0.75);
   -moz-box-shadow: inset 0px 0px 15px -2px rgba(0,0,0,0.75);
   box-shadow: inset 0px 0px 15px -2px rgba(0,0,0,0.75);
 }
</style>
```
