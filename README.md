# Joint_Angle
单片机430采集电容极板的电容值，并通过蓝牙传输到安卓端，安卓端负责接收蓝牙数据及可视化显示（OpenGL ES)

*前身基于蔡的MagNavi*

###2015.06.25

没有下雨

由于之前的程序是基于平板，直接应用到手机上会有问题，修改界面，加部分蓝牙通信代码

###2015.06.26

下面是修改的一些步骤。
![](http://i.imgur.com/1YYmEJx.jpg)
这是刚改好蔡神的apk后的界面显示，数据好像一直不对，关节角度居然总是超值，和下位机液晶屏上的数字完全不相关，遂一遍一遍修改如下：

- 有个timertask在timer.schedule下200ms循环收一次数据，有挺多数据重复，大概是300ms一次
- 正常数据是三围，但是蓝牙的getinputstream在非本地这样的数据流情况下读取的都是1位+2位

![](http://i.imgur.com/Vl6qTOl.jpg)
![](http://i.imgur.com/Ucii5rA.jpg)


修改后根据时间判断，1+2之间的时间间隔较短，俩个数据包间隔长，修改好后数据基本可以是如下这样。
![](http://i.imgur.com/GhjNRFw.jpg)

###2015.06.29

雨季，下个不停

string转double会抛出异常，需要catch否则出错不能成功


图片突然无法上传


###2015.07.01

刚把雨伞放下，遮阳伞就要拿起来了

绘图表为什么会发生这样的情况？
![](http://i.imgur.com/GUznxPM.jpg)

而且好像不能清屏，似乎是重叠画起来的，不知为何

###2015.07.02

使用了MPChartlib，绘制图形成功

但是刷屏方法是0-50，,0-50，不是连续前移
![](http://i.imgur.com/gGBG6p3.jpg)





