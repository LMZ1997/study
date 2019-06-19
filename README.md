# '<div><img  ... /></div>'
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
