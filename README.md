
前言
时隔大半年,终于抽出空来可以更新这个组件了 (边缘化了,大概要被裁员了)


2\.7\.0终于发布了\~


更新内容:


**1\.添加API类任务的超时时间,可以通过全局配置也可以单个任务设置**


**2\.设置定时任务日志查看默认按开始时间倒序**


**3\.添加是否显示控制台日志的全局配置**


目前支持两个参数 `ShowConsoleLog //是否显示控制台日志` ，`DefaultApiTimeOut //默认全局API超时时间`


**代码如下:**




```
builder.Services.AddQuartzUI(quartzMUIOptions: new QuartzMUIOptions() { ShowConsoleLog=false,DefaultApiTimeOut=10});
```


**4\.优化UI显示\-固定操作栏和表头,方便任务较多的情况下操作**


**5\.优化UI显示\-执行记录消息添加支持br关键字进行换行查看**


**6\.修复API类定时任务在没有参数的情况下会报错的问题**


****注意:2\.7如果是数据库存储并从老版本更新的话 请手动添加ApiTimeOut字段****Mysql例子如下:****`ALTER TABLE`tab\_quarz\_task`ADD COLUMN`ApiTimeOut`int NULL;`****


GIT地址(欢迎start和 fork):[l2999019/GZY.Quartz.MUI: 基于Quartz的轻量级,注入化的UI组件 (github.com)](https://github.com)


 


还是介绍一下本项目的特性:


**轻量级,项目仅1\.43 MB(主要有部分UI占用空间,后续还有优化空间)**


**像swaggerUI一样,项目入侵量小,仅需要在Startup中注入的QuartzUI组件**


**可选新开项目(仅需要webapi即可),也可以直接加入到现有项目(支持MVC,razor各种.NET宿主的项目)**


**支持Http定时调用对应service服务.**


**支持通过DLL反射调用本地继承了IJobService的本地方法,并支持动态传参**


![](https://img2023.cnblogs.com/blog/653851/202312/653851-20231214090829374-953037224.gif)


 


更新详细说明
 


## 1\.**添加API类任务的超时时间,可以通过全局配置也可以单个任务设置**


 这个属性是由社区提出的建议,在实际应用中确实有这个必要,所以添加了此功能


现在可以全局匹配默认超时时间,代码如下:




```
builder.Services.AddQuartzUI(quartzMUIOptions: new QuartzMUIOptions() {DefaultApiTimeOut=10});
```


也可以通过创建API类定时任务时进行单个定时任务的配置,如图:


![](https://img2024.cnblogs.com/blog/653851/202409/653851-20240923092511760-1602370243.png)


 


 


 


## **2\.设置定时任务日志查看默认按开始时间倒序**


将定时任务执行日志的排序默认改为按开始时间排序方便查看最新的定时任务信息,如图:


![](https://img2024.cnblogs.com/blog/653851/202409/653851-20240923092800322-1147366838.png)


 


 


 


 


## **3\.添加是否显示控制台日志的全局配置**


这个属性是由社区提出的建议,确实在调试或者特殊情况下,控制台一直在输出内容,很难定位项目异常,所以添加了此功能


现在可以全局匹配默认超时时间,代码如下:




```
builder.Services.AddQuartzUI(quartzMUIOptions: new QuartzMUIOptions() { ShowConsoleLog=false);
```


 


## **4\.优化UI显示\-固定操作栏和表头,方便任务较多的情况下操作**


优化了UI的显示效果,将操作栏和表头进行固定,方便在定时任务较多的情况下进行任务的操作


也是由社区提出的建议


![](https://img2024.cnblogs.com/blog/653851/202409/653851-20240923093225250-1125203774.gif)


 


## **5\.优化UI显示\-执行记录消息添加支持HTML标签进行排版查看**


由社区提出的建议,优化了定时任务的消息记录 可以通过添加关键字(或别的HTML标签)进行排版处理,如图:


![](https://img2024.cnblogs.com/blog/653851/202409/653851-20240923093401851-364755329.png)


 


 


## **6\.修复API类定时任务在没有参数的情况下会报错的问题**


 


 


结束语
 **项目升级内容就介绍到这里拉\~,欢迎各位提出宝贵的意见**


**在这里特别感谢提出宝贵意见的兄弟: [JasonWangJie](https://github.com/l2999019/GZY.Quartz.MUI/issues?q=is%3Aissue+author%3AJasonWangJie "issues opened by JasonWangJie")  [xds135](https://github.com/l2999019/GZY.Quartz.MUI/issues?q=is%3Aissue+author%3Axds135 "issues opened by xds135") [goodluckily](https://github.com/l2999019/GZY.Quartz.MUI/issues?q=is%3Aissue+author%3Agoodluckily "issues opened by goodluckily"):[樱花宇宙官网](https://yzygzn.com)   [ljc1160](https://github.com/l2999019/GZY.Quartz.MUI/issues?q=is%3Aissue+author%3Aljc1160 "issues opened by ljc1160") [smilesxsy](https://github.com/l2999019/GZY.Quartz.MUI/issues?q=is%3Aissue+author%3Asmilesxsy "issues opened by smilesxsy")**


**我的博客即将同步至腾讯云开发者社区，邀请大家一同入驻：https://cloud.tencent.cn/developer/support\-plan?invite\_code\=3c3dzwjbcao00**


