---
title: 百度地图API使用
date: 2018-06-15 10:19:56
tags:
- 百度地图API
categories:
- 百度地图API
---
### 百度地图开发者教程
[百度地图开发者教程](http://lbsyun.baidu.com/)
### 百度地图API密匙申请方法
1.首先打开网址注册一个账号。填好信息好提交。
  申请地址http://lbsyun.baidu.com/apiconsole/key
  ![Alt text](/images/baidu/3.png)
2.点击创建应用弹出如下窗口。
![Alt text](/images/baidu/3.png)
3.按图所示填写自己所需要的菜单功能。
![Alt text](/images/baidu/2.png)
4.提交后，会出现以下图示一连数字那就是地图的API。
![Alt text](/images/baidu/1.png)
### 地图API示例
1.设置覆盖物
![Alt text](/images/baidu/map_2.png)
```
var map = new BMap.Map("allmap",{minZoom:3,maxZoom:5});
// 创建Map实例,minZoom：设置地图允许的最小级别，maxZoom：设置地图允许的最大级别
var point = new BMap.Point(116.473008,39.916605);
// 设置地理坐标点
map.centerAndZoom(point, 4);
// 初始化地图,即可设置中心点和地图缩放级别
map.enableScrollWheelZoom(true);
//启用滚轮放大缩小

//设置marker图标为飞机
var vectorPlane = new BMap.Marker(new BMap.Point(point.lng+0.04,point.lat-0.03), {
  // 初始化小飞机Symbol
  icon: new BMap.Symbol(BMap_Symbol_SHAPE_PLANE, {
    scale: 2,
    // 矢量图标大小
    strokeColor:"#F6C081",
    rotation: 50,
    // 方向
    fillColor:"#F6C081",
    // 填充色
    fillOpacity: 1
    // 透明度
  })
});
map.addOverlay(vectorPlane);
// 向地图中添加单个覆盖物
```
2.设置覆盖物的文字标签
![Alt text](/images/baidu/map_1.png)
```
var point = new BMap.Point(point.lng, point.lat);
// 设置坐标点
var label = new BMap.Label("我是文字标注哦",{offset:new BMap.Size(20,-10)});
// 创建一个文本标注实例,offset:文本标注的位置偏移值
label.setStyle({
width: "20px",
height: "20px",
lineHeight: "15px",
textAlign: "center",
border: '1px solid #000000',
borderRadius: "10px",
});
// 文字标签的样式设置
marker.setLabel(label);
// 为标注添加文本标注
```
3.信息窗口示例
![Alt text](/images/baidu/map_3.png)
```
// 百度地图API功能
var map = new BMap.Map("allmap");
var point = new BMap.Point(116.417854,39.921988);
var marker = new BMap.Marker(point);
 // 创建标注
map.addOverlay(marker);
// 将标注添加到地图中
map.centerAndZoom(point, 15);
var opts = {
  width : 200,     // 信息窗口宽度
  height: 100,     // 信息窗口高度
  title : "海底捞王府井店" , // 信息窗口标题
  enableMessage:true,//设置允许信息窗发送短息
  message:"亲耐滴，晚上一起吃个饭吧？戳下面的链接看下地址喔~"
}
var infoWindow = new BMap.InfoWindow("地址：北京市东城区王府井大街88号乐天银泰百货八层", opts);
// 创建一个信息窗实例，其中content支持HTML内容
marker.addEventListener("mouseover", function(){
  map.openInfoWindow(infoWindow,point);
  //开启信息窗口
});
marker.addEventListener("mouseout", function(){
  map.closeInfoWindow(infoWindow,point);
  //关闭信息窗口
});
```
4.绘制折线
![Alt text](/images/baidu/map_4.png)
```
var map = new BMap.Map("allmap");
map.centerAndZoom(new BMap.Point(116.404, 39.915), 15);
map.enableScrollWheelZoom();

var Symbol = new BMap.Symbol(BMap_Symbol_SHAPE_PLANE, {
scale: 2,
strokeColor:"#24B76E",
rotation: 270,
fillColor: "#24B76E",
fillOpacity: 1
})
//设置飞机矢量图
 var iconSequence = new BMap.IconSequence(Symbol, '10%', '100%', false);
//创建线上的符号类。 fixedRotation 图标的旋转角度是否与线走向一致
var polyline = new BMap.Polyline([
		new BMap.Point(116.399, 39.910),
		new BMap.Point(116.405, 39.920),
		new BMap.Point(116.423493, 39.907445)
		// 点的集合
	], {strokeColor:"blue",
	 strokeWeight:2,
	 // 折线样式设置
	 strokeOpacity:0.5,
	 icons:[iconSequence]
	 // 配置贴合折线的图标
	 });
	map.addOverlay(polyline);   //增加折线

```