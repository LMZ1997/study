# 记录工作遇到的一些常用代码

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
  解决移动端a标签点击高亮
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

# ts项目防抖代码
         const debounce = (fn: any, wait: any) => {
	    //用于输入框onchange防抖
	    let timeout: any = null;
	    return function(input: any) {
	      input.persist();
	      if (timeout !== null) clearTimeout(timeout);
	      timeout = setTimeout(fn, wait, input);
	    };
	  };
	  dobounce(fn,300)
