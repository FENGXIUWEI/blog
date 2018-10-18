---
title: css3.0总结
date: 2018-06-07 14:11:53
tags:
---
### css3.0
css3.0 在css的基础上新增加了一些属性以及用法
### 属性选择器
E[attr] 只使用属性名，但没有确定任何属性值
E[attr="value"]指定属性名,并指定该属性的属性值
E[attr~="value"]指定属性名，并且具有属性值，此属性值是一个词列表，并且以空格隔开，其中词列表中包含了一个value词，而且等号前面的~不能不写
E[attr^="value"]指定属性名，并且具有属性值，属性值以value开头
E[attr$="value"]指定属性名，并且具有属性值，而且属性值是以value结束的
E[attr\*="value"]指令了属性名,并且有属性值，而且属性值中包含了value值
E[attr|="value"]指定了属性名，并且有属性值是value或者是以‘vaule-’开头的值(zh-cn)
E:nth-child(n) 表示E父元素中的第n个子节点
p:nth-child(odd){background:red} // 匹配奇数行
p:nth-child(even){background:red} // 匹配偶数行
p:nth-child(2n){background:red}
E:nth-last-child(n) 表示E父元素中的第n个字节点，从后向前计算
E:nth-of-type(n) 表示E父元素中的第那个字节点，且类型为E
E:nth-last-of-type(n) 表示E父元素中的第那个字节点，且类型为E，从后向前计算
E:empty表示E元素中没有子节点，注意子节点包含文本节点
E:first-child 表示E元素中的第一个子节点
E:last-child 表示E元素中最后一个子节点
E:first-of-type 表示E元素中的第一个子节点且节点类型是E
E:last-of-type 表示E元素中的最后一个子节点且节点类型为E
E:only-child 表示E元素中只有一个子节点，注意：子节点不包含文本节点
E:only-of-type 表示E的父元素中只有一个子节点，且这个唯一的子节点类型必须为E，注意：子节点不包含文本节点
E:target 表示当前的url片段的元素类型，这个元素必须是E
E:disabled 表示不可点击的表单控件
E:enabled 表示可点击的表单控件
E:checked 表示已选中的checkbox或radio
E:first-line 表示E元素中的第一行
E:first-letter 表示E元素中的第一个字符
E::selection 表示E元素在用户选中文字时
E::before 生成内容在E元素前
E::after 生成内容在E元素后
E:not(s)表示E元素不被匹配
E~F表示E元素毗邻的F元素
content 属性

### 弹性盒模型
任何一个容器都可以指定为Flex布局。
```
.box{
  display: flex;
}
```
行内元素也可以使用Flex布局。
```
.box{
  display: inline-flex;
}
```
同时需要注意，在不用的浏览器中，我们还需要在前面加上对应的浏览器前缀。
```
.box{
  display: -webkit-flex; /* Safari */
  display: flex;
}
```
### 文字特效
text-shadow: h-shadow v-shadow blur color;
h-shadow：水平阴影的位置。允许负值
v-shadow：垂直阴影的位置。允许负值
blur：模糊的距离
color：阴影的颜色

box-shadow: h-shadow v-shadow blur spread color inset;
h-shadow：水平阴影的位置。允许负值
v-shadow：垂直阴影的位置。允许负值。
blur：可选。模糊距离。
spread：可选。阴影的尺寸。
color：可选。阴影的颜色
inset：可选。将外部阴影 (outset) 改为内部阴影。
box-shadow还支持多阴影，例 如：box-shadow: inset 0 0 1px #fff, inset 4px 4px 20px  rgba(255,255,255,0.33), inset -2px -2px 10px rgba(255,255,255,0.25);所表示的 含义是，无偏移1像素模糊白色阴影重叠于左上角4像素偏移20像素模糊透明度0.33的白色内阴影再重叠于右下角偏移2像素，模糊10像素，透明度 0.25的白色内阴影。
text-overflow:
```
div.test
{
	white-space:nowrap;
	width:12em;
	overflow:hidden;
	color:red;
	border:1px solid #000000;
	text-overflow:ellipsis;
	// text-overflow:clip;
	// text-overflow:'--';
}
```
### 过渡和2D变化

多样式设置：transition：1s width，2s 1s height，3s 2s background
transition-property:要运动的样式  （all || [attr] || none）
transition-duration:运动时间
transition-delay:延迟时间
transition-timing-function:运动形式(
ease：（逐渐变慢）默认值
linear：（匀速）
ease-in：(加速)
ease-out：（减速）
ease-in-out：（先加速后减速）
cubic-bezier 贝塞尔曲线（ x1, y1, x2, y2 ） http://matthewlein.com/ceaser/
)
过渡完成事件 :
Webkit内核：obj.addEventListener('webkitTransitionEnd',function(){},false);
firefox:obj.addEventListener('transitionend',function(){},false);
2D变换transform
rotate()： 旋转函数 取值度数
transform-origin：原点，默认原点位于元素的X轴和Y轴的50%处
```
// 表盘效果
<!DOCTYPE HTML>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <script src="jquery-1.10.2.min.js" type="text/javascript"></script>
    <title>无标题文档</title>
    <style id="css">
        #wrap{
            width:200px;
            height:200px;
            -webkit-border-radius: 50%;
            -moz-border-radius: 50%;
            border-radius: 50%;
            border:2px solid #000;
            margin: 100px auto;
            position:relative;
        }
        #wrap ul{
            margin:0px;
            padding:0px;
            height:200px;
            list-style:none;
            position:relative;
        }
        #wrap ul li{
            width:2px;
            height:5px;
            background:#000;
            position:absolute;
            left:99px;
            top:0px;
            -webkit-transform-origin: center 100px;
        }
        #wrap ul li:nth-child(1){
            -webkit-transform: rotate(0deg);
        }
        #wrap ul li:nth-child(5n+1){
            height:10px;
            background:red;
        }
        #hour{
            width:6px;
            height: 45px;
            background:#000;
            position:absolute;
            left:97px;
            bottom:100px;
            -webkit-transform-origin:bottom;
        }
        #min{
            width:4px;
            height: 65px;
            background:green;
            position:absolute;
            left:98px;
            bottom:100px;
            -webkit-transform-origin:bottom;
        }
        #sec{
            width:2px;
            height: 85px;
            background:red;
            position:absolute;
            left:99px;
            bottom:100px;
            -webkit-transform-origin:bottom;
        }
        #centre{
            height:12px;
            width:12px;
            border-radius:50%;
            background:#000;
            position:absolute;
            left: 94px;
            bottom:94px;
        }
    </style>
</head>
<body>
<div id="wrap">
    <ul id="list">
    </ul>
    <div id="hour"></div>
    <div id="min"></div>
    <div id="sec"></div>
    <div id="ico"></div>
    <div id="centre"></div>
</div>
<script>
$(function(){
    var ulHtml='';
    var sCss='';
    for(var i=0;i<60;i++){
        sCss+=' #wrap ul li:nth-child('+(i+1)+'){-webkit-transform: rotate('+i*6+'deg);}'
        ulHtml +='<li></li>'
    }
    $("#list").html(ulHtml);
    $("#css").append(sCss)
    var oHour=$("#hour");
    var oMin=$("#min");
    var oSec=$("#sec");
    toTime(oHour,oMin,oSec)
    setInterval(function(){
        toTime(oHour,oMin,oSec);
    },1000)
    function toTime(oHour,oMin,oSec){
        var oDate=new Date();
        var iSec=oDate.getSeconds();
        var iMin=oDate.getMinutes()+iSec/60;
        var iHour=(oDate.getHours()%12)+iMin/60
        oSec.css("-webkit-transform","rotate("+(iSec*360/60)+"deg)");
        oMin.css("-webkit-transform","rotate("+(iMin*360/60)+"deg)");
        oHour.css("-webkit-transform","rotate("+(iHour*360/12)+"deg)");
    }
})
</script>
</body>
</html>
```
skew() ：倾斜函数 取值度数
scale()：缩放函数 取值 正数、负数和小数
translate()：位移函数
transform-origin：right bottom 变换的基点值
```
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <script src="jquery-1.10.2.min.js" type="text/javascript"></script>
    <style>
     html{
         height:100%;
         overflow:hidden;
     }
     body{
       background:#f9f9f9;
     }
     #menu{
         width:50px;
         height:50px;
         position:fixed;
         right:20px;
         bottom:20px;
     }
     #menu_list{
         height:42px;
         width:42px;
         position:relative;
         margin:4px;
     }
     #menu_list img{
         border-radius:21px;
         position:absolute;
         left:0;
         top:0;
         border-radius:21px;
     }
     #home{
         width:50px;
         height:50px;
         background:url(home.png) no-repeat;
         border-radius:25px;
         position:absolute;
         left:0;
         top:0;
         -webkit-transition:1s;
         -moz-transition: 1s;
         -ms-transition: 1s;
         -o-transition: 1s;
         transition: 1s;
     }
    </style>
    <script>
        $(function(){
            var oBtn=$("#home");
            var aMenus=$("#menu_list img");
           var off=true;
            var iR=-150;
            oBtn.click(function(){
                // 逆时针旋转360度
                if(off){
                    oBtn.css("-webkit-transform","rotate(-360deg)");
                    //设置每一个导航的位置
                    for(var i=0;i<aMenus.length;i++){
                        var iDeg=(90/4)*i;
                        var isLeftTop=toLT(iDeg,iR);
                        var left=isLeftTop.i-21;
                        var top=isLeftTop.t+21;
                        aMenus.eq(i).css({"transition":"0.5s "+i*100+"ms","left":left+"px","top":top+"px","-webkit-transform":"rotate(-720deg)"})
                    }

                }else{
                // 顺时针旋转
                    oBtn.css("-webkit-transform","rotate(360deg)");
                    for(var i=0;i<aMenus.length;i++){
                        aMenus.eq(i).css({"transition":"0.5s "+(aMenus.length-1-i)*50+"ms","left":"0px","top":"0px","-webkit-transform":"rotate(0deg)"})
                    }
                }
                off=!off
            })
            for(var i=0;i<aMenus.length;i++){
                aMenus.eq(i).click(function(){
                    $(this).css({"transition":"0.5s","-webkit-transform":"scale(2)","opacity":"0.5"});
                    // 完成过渡效果后的修改
                    $(this).bind("transitionend", end);
                })
            }
            // 计算图标的位置
            function toLT(iDeg,iR){
                var isLeft=Math.round(Math.sin(iDeg/180*Math.PI)*iR)
                var isTop=Math.round(Math.cos(iDeg/180*Math.PI)*iR)
                return {i:isLeft,t:isTop}
            }
            // 完成过渡效果后的样式调整
            function end(){
                $(this).css({"transition":"0.1s","-webkit-transform":"scale(1)","opacity":"1"});
            }
        })
    </script>
</head>
<body>
<div id="menu">
    <div id="menu_list">
        <img src="prev.png" alt=""/>
        <img src="open.png" alt="" />
        <img src="clos.png" alt="" />
        <img src="full.png" alt="" />
        <img src="refresh.png" alt="" />
    </div>
    <div id="home"></div>
</div>
</body>
</html>
```
matrix：矩阵
matrix（a,b,c,d,e,f)
位移：
x轴的位移：e+disX
Y轴的位移：f+disY
### 动画
关键帧的写法
```
@keyframes  miaov_test
{
	from { background:red; }
	to { background:green; }
}
```
折纸效果
```
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <style>
        @-webkit-keyframes open{
            0%
            {
                -webkit-transform:rotateX(-120deg);
            }
            25%
            {
                -webkit-transform:rotateX(30deg);
            }
            50%
            {
                -webkit-transform:rotateX(-15deg);
            }
            75%
            {
                -webkit-transform:rotateX(8deg);
                box-shadow:inset 0 0 0 0 #ccc;
            }
            100%
            {
                -webkit-transform:rotateX(0deg);
            }
        }
        @-webkit-keyframes hide{
            0%
            {
                -webkit-transform:rotateX(0deg);
            }
            100%
            {
                -webkit-transform:rotateX(-120deg);
            }
        }
        *{
            padding:0px;
            margin:0px;
        }
        .wrap{
            width:240px;
            margin:0 auto;
            position:relative;
            /* 设置3D效果 */
            -webkit-perspective:800px;
        }
        .wrap h3{
            width:240px;
            height:40px;
            background:#f60;
            color:#fff;
            line-height:40px;
            text-align:center;
            position:relative;
            z-index:10;
        }
        .wrap div{
            position:absolute;
            top:30px;
            left:0;
            -webkit-transform-style:preserve-3d;
            width:100%;
            -webkit-transform-origin:top;
            -webkit-transform:rotateX(-120deg);
            z-index:1;
        }
        .wrap>div:nth-of-type(1){
            top:40px;
        }
        .wrap span{
            width:240px;
            display:block;
            height:28px;
            background:#CF3;
            color:#fff;
            font:14px/28px "宋体";
            text-indent:20px;
            box-shadow:inset 0 0 100px 20px rgba(0,0,0,0.2);
        }
        .wrap .open{
            -webkit-transform:rotateX(0deg);
            -webkit-animation:1.5s open ease;
        }
        .wrap .open>span{
            box-shadow:inset 0 0 100px 20px rgba(0,0,0,0);
        }

        .wrap .close{
            -webkit-transform:rotateX(-120deg);
            -webkit-animation:0.5s hide ease;
        }
        .wrap .close>span{
            box-shadow:inset 0 0 100px 20px rgba(0,0,0,0.5);
        }
        #btn{
            position:absolute;
            left:0;
            top:0;
            width:100px;
            height:30px;
            transition:1s;
        }
    </style>
    <script>
        window.onload=function()
        {
            var oBtn=document.getElementById("btn");
            var oWrap=document.getElementById("wrap");
            var aDiv=oWrap.getElementsByTagName("div");
            var i=0;
            var oTimer=null;
            var iDelay=200;
            var Boff=true;
            oBtn.onclick=function(){
                oBtn.style.left="-300px";
                if(Boff){
                    // 开启计时器
                    i=0;
                    oTimer=setInterval(function(){
                        aDiv[i].className="open";
                        if(i==aDiv.length-1)
                        {
                            // 关闭计时器
                            clearInterval(oTimer);
                            oBtn.style.left="0px";
                            oBtn.value="关闭";
                        }
                        i++;
                    },iDelay)

                }else{
                    // 收起此效果
                    i=aDiv.length-1;
                    oTimer=setInterval(function(){
                        aDiv[i].className="close";
                        if(i==0)
                        {
                            // 关闭计时器
                            clearInterval(oTimer);
                            oBtn.style.left="0px";
                            oBtn.value="展开";
                        }
                        i--;
                    },iDelay)
                }
                Boff=!Boff;
            }
        }
    </script>
</head>
<body>
    <input type="button" value="展开" id="btn" />
    <div id="wrap" class="wrap">
        <h3>这是标题</h3>
        <div>
            <span>
               选项1
            </span>
            <div>
                <span>
                    选项2
                </span>
                <div>
                    <span>
                        选项3
                    </span>
                    <div>
                        <span>
                            选项4
                        </span>
                        <div>
                            <span>
                                 选项5
                            </span>
                            <div>
                                <span>
                                    选项6
                                </span>
                                <div>
                                     <span>
                                        选项7
                                     </span>
                                    <div>
                                        <span>
                                            选项7
                                        </span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```
