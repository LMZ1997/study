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
