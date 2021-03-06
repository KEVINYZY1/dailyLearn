### 实习总结

---

### 1）我的收获



**技术方面**  


+ grunt/gulp 打包工具

+ Express Node的框架  
至少要了解如何初始化一个Node项目、如何搭建一台Express服务器、以及如何使用request模块转发请求。

+ Kissy 前端脚本库  
kissy是公司内部使用的前端框架，对业务更有亲和力。kissy提供庞大的组件和插件，易用性很强，但有一定学习门槛。

+ git，熟练建立分支、合并分支、回滚。

+ 仔细阅读规范  
 
虽然阅读规范是一项艰辛的任务，但一旦出现浏览器对某个页面的渲染不同的情况，这一任务就是不可避免的了。

> 最近我遇到这样一个例子，与可伸缩（flex）元素的默认最小尺寸有关。根据规范所说，可伸缩元素的min-width与min-height的初始值是auto，而不是0，这就意味着在默认情况下，这些元素不可能收缩到比其中的内容尺寸还小。而在过去8个月中，Firefox是唯一一个正确地实现了这一特性的浏览器。
> 


**工具方面**

+ adb，命令行工具，PC和安卓设备建立交互，方便hybird app调试（[温习](http://www.cnblogs.com/xiaoxuetu/p/3411214.html)）
+ ihosts，管理本地hosts
+ emment，sublime便捷开发插件，提高开发效率


----
### 2）我参与的项目和任务

**项目**

#### a ) 猎户一期   

目标：方便运营操作和提高运营工作效率。



#### b ) 扫描卡片2.0版本

**遇到的问题**

修复“头部跟随效果，用fixed实现，故而滚动条会滑动到头部”问题。需要考虑其他方案，模拟native效果。  
问题产生原因 ：设定body overflow:scroll属性而头部  position:fixed，并不会产生这种比较原生的样式。body容器全部可滚动，滚动条将跨越整个屏幕可见区域。这是因为用户滑动的是整个页面，而不是某个容器的内容。  
>滚动在许多app中决定用户体验的最重要因素之一。 
 
最终采用iscrolljs需要，修改原本的html结构，添加额外的标签属性，实现顺畅、连续拖动会加速滑动效果。

html5页面上依照native app的固定头部设计，降低不同终端在用户体验上的差异性。实践了鬼道叔叔《跨终端Web》中提到的思想：
>跨终端希望从移动优先理念出发，从设计、产品、开发都能够先做出移动版本再层层累加，这是概念上的“跨”；另一方面，对于用户而言，看到的页面地址永远都只有一个，不同终端间的差异对那个该对用户透明，这就是现实中的“跨”。


**基本工作流程：**

html是由后端管理。前端将html/css/JavaScript开发好后，将html模板交给后端同学，同时将静态资源(css/javascript/img)发布到测试环境或线上。img直接上传，但是css和js需要在本地打包后，push到仓库，同时使用团队cdn工具att完成cdn部署。一般前端的改工在两分钟之内就能在线上见效，一天发布十几个版本毫无压力。

**但是也会遇到问题：**  

页面开发简单，联调麻烦。  
服务端在vm只注入json， 渲染前端用ejs模板引擎渲染。  
vm模板的缺陷是前后端不能完全分离，前端修改线上模板需要依赖后端同学。前端js渲染模板的缺陷在于前端需运行js同时json数据注入后才会渲染出页面。后端传送的数据格式和字段未知，一旦模板尝试访问不存在字段会造成，前端模板引擎出错，页面渲染失败。
后续解决方法：PC连接已经安装apk的手机，在git管理员命令处理程序中查看日志（例如输出后端数据）。但是需要注意，客户端访问还没上线只上传到测试环境资源，需要修改hosts。



**埋点**

一款Android商业应用上线后，最关心的莫过于用户使用哪个模块比较频繁，哪个模块使用人群较少，产品可以根据这些数据来修正app以后的发展方向，使产生最大的商业价值。
通过埋点监控，我们可以深入业务的每一个细节，产生的用户行为可以通过所埋的点累计次数并将这些数据发送到数据中心，通过数据分析师就能给产品提出宝贵的意见，指导产品的演化方向。

+ 参与yunos权益中心后台管理系统改版：

两天时间搭建后台系统前端页面，完成所有基本功能，批量操作（发布，下架），查询筛选，分页等等功能。权益两种领取方式（优惠码和html5）逻辑处理上稍微有所区别。权益表表格/权益信息列表修改页面，在 本地 前端开发时使用nodejs环境结合grunt工具，实现输出本地模拟数据等，为和后台交接做好准备。一周时间和服务端同学完成管理后台变量修改权重、状态、标签的接口对接。对于已经新添加权限页面，html5批量上传文件，获取文件名。后台返回上传状态信息和存储后台的文件名，提供能浏览和下载功能等等。 



**任务**

+ 在糖蜜和文泰指导下，修复bbs.yunos.com反射型XSS。
+ 在糖蜜指导下，修复【生活服务】YunOS版块热帖中出现Ctrl+C的链接复制方式

-----
###  3）我参加的讲座


+ 7月27日下午参加“蚂蚁金服前端团队 Ant UED 主办的技术分享会”。

>百度平侠分享百度FEX架构变迁，对前端开发的思考，以及对目前创业热潮的观察。  
百度对人才选拔要求高，[要求成员能力 = 全栈 + 产品意识 + 自驱]。前端工程师拥抱变化，打造技术专长，并且有对技术探索的热情。  
怎么样的前端最抢手？前端（全栈）+ 务实，务实是很多企业所看重的。
（展示交互逻辑 + 数据 + 终端设备）-> 应用 -> 用户  
支付宝体验技术部玉伯陈述体验技术部未来的的方向和架构。  
研发模式3.0 ->（chair1.0 + Arale7.0 + 体验学院 + 工程平台）
第一代工程师高效不专业 -> （前端/服务端/客户端/数据分析等工程师）分工更细，品质提升，专业但不高效 -> 第三代工程师演变为产品工程师和平台工程师，高效而又专业。  
团队核心品质[专业]开放、简单、极致，[有爱]相信、给予  
团队每一个人应该有野心，有事情主动争取机会。但是野性有别于狼性。


+  7月29日下午参加UED新人特训营  

小马《阿里UED发展史》  
>数据可视化产品，营销性产品，企业级服务产品，终端产品  
无障碍沟通，更多关注有障碍人群。  
mobile first  
对业务的足够熟悉，才能找到切合点。具备这个能力，表达自己的意愿，主动争取另一方向的工作  

态哥《在阿里的365天》  
>工作战斗力=基础分+项目数+项目质量+纵横向能力。
预留时间，总结和充电，培养纵向能力。一些不敢做，无法做的东西，在每天一点一滴地积累中提升，身边人也能看得到你的努力。
明确需求，项目背景。更多接触业务需求，逐渐熟悉工作流程。得心应手。并且开始积累和视觉相关的交互和前端方向的知识。项目级任务，会议总结(沟通组织能力)。


  
-----
### 4）我的思考


**造轮子**

造轮子在商业角度看是非常糟糕的，但是从学习角度来看，非常好。库和小工具都能从npm里拿下来，但也可以想象自己独立建造能够学到多少东西。
虽然哪一第三方代码，具有多年的测试用例积累和已知问题积累，使用它们绝对是非常明智选择。从优秀到卓越，不把自己的手弄脏是几乎不可能逃到金子的。

**多项目同时进行如何做好进度管理**  

1）明确且达成共识的项目目标  
2）精细化的任务分解。要点是每个子任务时间不要超过一周，明确的子任务目标、时间、交付物。  
3）有时间保障且有能力执行的资源分配。有些项目虽然分配了资源，但是不能保障资源的有效投入，这个是项目不能推进的非常重要的原因。  
4）每日检查、每周检查项目进展和提交物  


**快速反应，快速学习**

阿里强调拥抱变化，要拥抱好变化，快是必不可少的。在将近两个月的实习期里，我对任务、对项目的反应速度越来越快，将自身的惰性磨灭的越来越少。同时，在阿里这样一个快节奏的互联网公司，工作上的很多内容都需要自己主动去了解，所以我的学习能力在这里得到了极大的锻炼，理解了一项新事物，马上就能运用到实际工作中去。

在阿里的实习是充满挑战也充满机遇。生活服务系统内，一开始视觉设计，交互设计到前端开发都被交由我负责，这样下能够发掘我们在设计方面的天赋；开发平台充当一回用户体验师，第0批开放者，用开放平台开发demo，体验整个流程，改善开放平台用户体验。

很多知识是需要花费大量的时间学习的，比如 backbone, JQuery源码分析, MVVM, 设计模式, HTTP协议, 响应式, 异步编程, 模块化, websocket, DOM监控, 本地储存, 浏览器渲染原理等等，平时学习的时候可以把这些关键字枚举下，然后针对每个关键字延伸学习。

延伸学习的方式很简单，google 一个关键词你能看到十几篇优秀的博文，再这些博文中寻找新的关键字，直到整个大知识点得到突破。我一直都是这么学习的。

周瑾：我认为工程师可以分为两种：**一种喜欢钻细一个东西，然后以此为生；还有一种喜欢不断折腾，需要去满足自己了解未知的欲望**。拿我自己来说，我属于后者。我有创业经历，也做过大公司的螺丝钉。螺丝钉其实满足不了我对技术的兴趣，所以在工作过程中我在不断寻找自己的技术边界，并试图打破它。就这样，技术开始变得一点点全面起来。

>周瑾：我其实不怎么觉得全栈有优势，我只能说能看到这种人身上的一点点共性。视野，思维和学习能力确实有点优势，但我认为共性是性格上的。我接触到的在互联网行业跨领域性的人，其实都比较单纯，或者说编程对于这类人来说不是一种谋生途径而是一种个人兴趣。

我觉得全栈更多的是自己对纯技术的渴求，深入任何一个技术领域都是很细致的一件事，全栈与否更多的是一种经验上量变到质变的过程。

**把所学到的东西都记录下来**

把学到的东西记录下来，最终要的原因是强迫你更好地理解这件事。如果没法讲清楚他的工作原来，那么在记录的整个过程中，它会推动你把并不真正理解的东西弄清楚。很多情况下自己根本意识不到自己还不理解他们——直到自己动手写的时候。

>将你所学到的东西用文字记录下来：“按我的经验来看，写作、演讲以及开发demo，这些方法能够迫使我对知识点进行充分的挖掘，并做到从内到外的完全理解。哪怕你写的东西完全没人看，但写作的过程本身就已经值得你付出的努力了。”

**学会阅读别人的代码**

从阅读他人的代码中可以学到很多知识，它可以拓宽你的思路，了解“新的工作方法”，同时也有助于你在团队中的工作。实际上，这一点确实相当必要，因为“作为一位工程师来说，你的时间大部分都是在一个现有的代码库中添加或修改代码”，而不是从头开始编写全新的代码。

**密切沟通且沟通有道**

对于任何一项工作来说，与团队中其他同学的沟通都是一项很重要的内容。团队运作上出了问题，很有可能是沟通不畅。因此我在工作中特别注意和团队成员在信息沟通上保持一致，但要保持一致，仅仅多发邮件是不够的。要根据不同的工作场景，不同小二的工作习惯，制定相应的沟通策略，以实现精确而高效的沟通。

-----
### 5）我的改进


在实习过程中，我还是暴露出了很多的不足。如果我有幸转正成功，我计划利用最后一年的校园时光来磨练工作技巧，改进工作。  

**多学习，多看书**

听起来很稀松平常，也很虚的一点。但确实在工作中我切切实实的感受到了知识的重要性。
 
除了学习专业课的知识，其他学科的知识也是之后学习的目标。因为每学习一门学科，都意味着打开了一扇新世界的大门，都意味着掌握了一种新的思维方式。反映到工作中来，就是能够用更多的角度来创造性的工作，如果没有相当的知识储备，是无论如何都难以做到这一点的。比如学习了心理学的知识，就能够更好地洞察消费者的内心，从而有针对性的制定相关方案。

**培养细节意识**


细节决定成败，今后对于细节我会特别注重，因为工作中很多东西涉及到数字，需要特别细致认真的工作态度。但如何培养细节意识，是一个很模糊的概念，但我会在工作中努力去摸索适合自己的培养模式的。
