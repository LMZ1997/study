# ‘< div><img  ... /></ div>‘
想要这里的div根据图片的高度自适应，可以给img加上浮动样式，然后再在div里插入标签<span style="clear:both"></span>

# vue中在css里引入背景图片background-image:url(),url里的路径可以使用绝对路径 /static/imgs/logo.png
# 获取微信用户昵称头像
	var my_nickname = decodeURIComponent(localStorage.getItem("nickname")); //当前访问者的用户名
	var my_photo = decodeURIComponent(localStorage.getItem('photo'));	//当前访问者的头像
# html根目录font-size动态设置
	html {
	  font-size: 16px;
	}
	@media screen and (min-width: 375px) {
	  html {
	    /* iPhone6的375px尺寸作为16px基准，414px正好18px大小, 600 20px */
	    font-size: calc(100% + 2 * (100vw - 375px) / 139);
	    font-size: calc(16px + 2 * (100vw - 375px) / 139);
	  }
	}
	@media screen and (min-width: 414px) {
	  html {
	    /* 414px-1000px每100像素宽字体增加1px(18px-22px) */
	    font-size: calc(112.5% + 4 * (100vw - 414px) / 586);
	    font-size: calc(18px + 4 * (100vw - 414px) / 586);
	  }
	}
	@media screen and (min-width: 600px) {
	  html {
	    /* 600px-1000px每100像素宽字体增加1px(20px-24px) */
	    font-size: calc(125% + 4 * (100vw - 600px) / 400);
	    font-size: calc(20px + 4 * (100vw - 600px) / 400);
	  }
	}
	@media screen and (min-width: 1000px) {
	  html {
	    /* 1000px往后是每100像素0.5px增加 */
	    font-size: calc(137.5% + 6 * (100vw - 1000px) / 1000);
	    font-size: calc(22px + 6 * (100vw - 1000px) / 1000);
	  }
	}

# 解决html5 audio标签在苹果ios不能自动播放的问题
	function audioAutoPlay(id){
		var audio = document.getElementById(id),
		    play = function(){
			audio.play();
			document.removeEventListener("touchstart",play, false);
		    };
		audio.play();
		document.addEventListener("WeixinJSBridgeReady", function () {
		    play();
		}, false);
		document.addEventListener('YixinJSBridgeReady', function() {
		    play();
		}, false);
		document.addEventListener("touchstart",play, false);
	    }
    audioAutoPlay('BGSound');
    
# 解决ElementUi里的轮播图默认高度300px的影响
	方法一（不全面）：setSize: function() {
		var width = window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
		this.screenWidth = width;
		//图片                高 / 宽  700 / 1920
		this.bannerHeight = 360 / 720 * this.screenWidth
		document.getElementById('el-carousel').style.height = this.bannerHeight + 'px';

	      }
	方法二：.el-carousel{
		height: 11.75rem!important;
	    }
# async函数的使用方式，直接在普通函数前面加上async，表示这是一个异步函数，在要异步执行的语句前面加上await，表示后面的表达式需要等待
# github拉取git仓库下的某个文件夹
    如： https://github.com/LMZ1997/stu/tree/master/weChat    将 tree/master 更改为 trunk ,然后用svn下载
# 解决移动端a标签点击高亮
	  a {
		width: 100px;
		height: 100px;
		display: block;
		-webkit-tap-highlight-color: transparent;
	      }
# 多行文本溢出显示省略号
	 display: -webkit-box;
	 /*! autoprefixer: off */
	  -webkit-box-orient: vertical;
	/*! autoprefixer: on */
	-webkit-line-clamp: 3;
	overflow: hidden;
# 微信h5页面兼容性之
	h5页面点击inout框弹出输入法框后，将输入法框关闭，会导致当前页面显示之前100%高度减去输入框高度的bug，解决：添加input的blur事件,执行document.body.scrollTop=0操作
# h5页面input框的输入法回车事件，可能越过当前input的限制问题，比如设置input必填；解决办法：检测input keydown事件，如果输入回车，则return false

# 判断对象最准确的用法 
	function isObject(x) {
	    return Object.prototype.toString.call(x) === '[object Object]';
	}
# ES6方法set实现数组去重
	const fn = arr => [...new Set(arr)];

	fn([1,2,3,2,3,5])  // 1,2,3,5
# 强制项目只能在微信浏览器里打开
	  var useragent = navigator.userAgent;
	    if (useragent.match(/MicroMessenger/i) != 'MicroMessenger') {
		// 这里警告框会阻塞当前页面继续加载
		alert('已禁止本次访问：您必须使用微信内置浏览器访问本页面！');
		// 以下代码是用javascript强行关闭当前页面
		window.location.href = "http://www.eol.cn";
	    }
# h5兼容性之input框回车限制
    $(".z_input").keydown(function(e) {
      //避免输入框回车问题
      if (e.keyCode == 13 && $(this).text() == "") {
        return false;
        alert("请完善相关信息");
      }
    });
# h5兼容性之键盘抬起影响布局（多发于安卓）
	 window.onload = function() {
	      //安卓机键盘抬起会使背景图上移问题
	      document.getElementsByTagName("body")[0].style.height =
		window.innerHeight + "px";
	    };
# input框设置为number类型，不容易对其进行字符限制，设置类型为text + 正则限制数字输入
# input 原生验证条件required,在每一项都通过验证时，会触发form标签上绑定的submit函数
# 当页面的地址包含‘#’时，widnow.location.search的返回值为空，因为search只取“？”后面和“#”之前的内容，如果“#”之前没有“？”search取值为空。
# "button type=\"reset\"></button>==="<button type="+'reset'+"></button>"
# 点击按钮下载文件不能用点击事件触发ajax请求接口
# 点击按钮复制Dom内的内容
	copyUrl = id => {
	    var e = document.getElementById(id);
	    e.select(); // 选择对象
	    document.execCommand("Copy"); // 执行浏览器复制命令
	    message.success("复制成功");
	  };
# echarts在react中使用需要import相关组件 如图例 import "echarts/lib/component/legend"; 如果没有引入，初次进入页面可能显示没问题，但是点击刷新后，图表显示会有问题 
# 如果父元素的font-size也是采用em表示,那么子元素的font-size怎么计算；
	如果父元素设置为2rem;真是font-size为32px;
	子元素也设置为2rem;那么子元素的font-size为64px;
# 下面通过代码阐述instanceof的内部机制,假设现在有 x instanceof y 一条语句
	while(x.__proto__!==null) {
	    if(x.__proto__===y.prototype) {
		return true;
	    }
	    x.__proto__ = x.__proto__.proto__;
	}
	if(x.__proto__==null) {return false;}
	
	x会一直沿着隐式原型链__proto__向上查找直到x.__proto__.__proto__......===y.prototype为止，如果找到则返回true，也就是x为y的一个实例。否则返回false，x不是y的实例。
#  react-router 和  react-router-dom 
	不同之处就是后者比前者多出了 <Link> <BrowserRouter> 这样的 DOM 类组件。
	因此我们只需引用 react-router-dom 这个包就行了
#  刷新页面，js 请求一般会有哪些地方有缓存处理？
	DNS缓存：短时间内多次访问某个网站，在限定时间内，不用多次访问DNS服务器。
	CDN缓存：内容分发网络（人们可以在就近的代售点取火车票了，不用非得到火车站去排队）
	浏览器缓存：浏览器在用户磁盘上，对最新请求过的文档进行了存储。
	服务器缓存：将需要频繁访问的Web页面和对象保存在离用户更近的系统中，当再次访问这些对象的时候加快了速度。
# 可以通过哪些方法优化css3 animation渲染
	尽可能多的利用硬件能力，如使用3D变形来开启GPU加速：
	尽可能少的使用box-shadows与gradients
	在CSS动画中使用webkit-transform: translateX(3em)的方案代替使用left: 3em，因为left会额外触发layout与pain
#  CSS Hack (用一些奇怪的手段达到兼容的方式！）
	<!–-[if IE 7]>
		<link rel="stylesheet" href="ie7.css" type="text/css" />
	<![endif]–->
# （值1，值2）等于啥
	var d = a = 3, b = 4
   	console.log(d)  //3
	
	var d = (a = 3, b = 4)
    	console.log(d)  //4
#  !!隐式转换
	var x = !!"Hello" + (!"world", !!"from here!!");    console.log(x)   //2
   	var x2 = 1 + (0,1);                                 console.log(x2)  //2
   	var x3= true + (false,true);                        console.log(x3)  //2
# a+++b运算过程
    var a=1;
    console.log( a+++3 ); //4      分为2部分运算，第一个首先a要先加上3，即1+3得出4，然后a++;即a此时==2；
    console.log( a+++1 );//3       分为2部分运算，第一个首先a要先加上1，即2+1得出3，然后a++;即a此时==3；
    console.log( a+++8 );//11      分为2部分运算，第一个首先a要先加上8，即3+8得出11，然后a++;即a此时==4；
# 判断值的类型
	typeof可以用来判断除null以外的其他原始类型的数据，typeof null == object;
	instanceof 用来判断除function以外的其他复杂类型的数据， typeof 函数fn == function。
# 函数传参中，参数为原始类型的，函数内不管如何改变参数的值，对函数外部的真实值不产生影响.若参数为复杂类型即对象时，函数内若更改参数，那么函数外部的值也将由影响
# js的常用内置对象？（new + 对象）
	Arguments 函数参数集合
	Array 数组
	Boolean 布尔对象
	Date 日期时间
	Error 异常对象
	Function 函数构造器
	Math 数学对象
	Number 数值对象
	Object 基础对象
	RegExp 正则表达式对象
	String 字符串对象
# 谈谈垃圾回收机制的方式及内存管理
      方式：
      	    1.标记清除（首先标记所有变量，还有引用价值的变量去掉标记，剩下有标记的就全部被垃圾回收机制清除）
	    2.引用计数（跟踪每个变量，该变量被引用一次计数就加1，该变量的值变成另一个计数就减1，当该变量计数为0时就被垃圾回收清除）
# [1,2,3].map(parseInt)
      设计到两方面知识
      1.map函数的参数arguments
      2.二进制转换规则
      首先，map函数接收一个function,这个function默认传参为（item,index),也就是说parseInt(item,index);
	parseInt(‘1’, 0); // radix为0时，使用默认的10进制，返回1。
	parseInt(‘2’, 1); // radix值在2-36，无法解析，返回NaN。
	parseInt(‘3’, 2); // 基数为2，2进制数表示的数中，最大值小于3，无法解析，返回NaN。
# ES5和ES6如何取数组的最大值：
	// ES5 的写法
	Math.max.apply(null, [14, 3, 77, 30]);

	// ES6 的写法
	Math.max(...[14, 3, 77, 30]);
# eval()的作用？
	把字符串参数解析成JS代码并运行，并返回执行的结果；
	
	例如：
	eval("2+3");//执行加运算，并返回运算值。
	eval("var age=10");//声明一个age变量
	
	eval的作用域取决于调用它的this的作用域
