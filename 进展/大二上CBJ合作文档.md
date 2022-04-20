# 大二上CBJ合作文档
我猜大佬们都会markdown写作，五分钟就能学会
## 整体战略构思


### 尽管名字叫平台搭建但是却不仅跟网络平台有关，应该有三个主要任务：
1. 网站搭建实现：（首先还是要明白网站的代码，结构之类的要怎么构建）+搜集题目+放题+做排名表+实名注册（剩下这几个似乎并不是很核心的要素）
2. web题目熟悉和竞赛：docker使用（docker如果不要求自己设计可能直接用框架就差不多，本身似乎也没有要求）+设计题目 （主要可能还是设计题目，设计题目就需要我们会做，因为之后还要打人家的比赛）
3. 漏洞扫描系统实现：看源代码，然后设计;（也不知道要不要装载到那个平台上，或许装载上了可以作为一个  "创新点"  ；具体还看他要求）

#### pdf里的进度也先列出：
1. 调研 
2. 设计 
3. 开发 
4. 配置 *所以这之前就要搞定开发方面的所有工作？*
5. 攻击测试（用设计好的漏扫+web技术搞别人的网站？） 
6. 代码审计（他好像提到了审计编辑器，可以看出代码的漏洞；不过也说了不能全信） 
7. 题目发布和竞赛

**虽然原则上以上步骤不分先后，但是就我个人来想，似乎先把网站和漏扫基本实现之后再专注于做题会比较好，可能可以避免精力的分散；**
也可以看看之后的具体情况来分成不同的做法：大家一块做同一个事的不同模块； 或者大家分别做不同的事；
**而且应该也是临近最后才需要做题，所以把熟练度放到后面会比较好？**
**不过还是要看每次验收时老师的要求之类的，灵活处理。**


#### 报告提交要求：——报告要独立ppt？好像和ppt合并就可以了？
1. 概要/总体设计报告（这次
2. 详细设计报告
后面不分先后的感觉
4. 测试报告 （偏后期
5. 平台结果展示报告 （后期
6. 可编译的代码 （后期
7. 平台运行录像 （后期
8. 每次进展介绍的ppt——这个有机会的话可以做的稍微上点心，以备之后的需要（大创，github等） 



## CTF平台开发
### 平台应具备的基本与进阶要求

- 支持最基本的web,pwn,reserve,misc,杂项五类题型，并从网上收集相关样题（每类不少于3道）布置到CTF网站上
    - 前端：文字的显示+js的按钮效果
    - 后端的代码应该把对应数据库的数据拉出来
    - 即每一个对应的题型，都应该至少有自己的一个数据表来存储（但这个最后的实现是用docker完成的），麻烦之后研究一下数据库和docker的结合
        - 每个题应该有 题目号，题目名，题目类别，题目难度，被做出的次数(与后面的可加分数相关)，目前题目可加分数，一血，二血，三血，hint状态(是否放出hint，默认为"未放出"),hint（短的话就可以放在其中）,题干（题干要不要放）
    - 对应的数据拉出来之后，以前端定义好的模式显示
    - docker：部署题目（xint等）（一次部署五道题？）
- 每道题目需要显示有哪些队伍做出来（其实显示一二三血即可，高级一点的可以显所有做出来的队伍，这个感觉也不难）
- 网站必须显示各个战队的分数，做出来的题目有哪些（最好能显示一二三血），进阶：显示个人分数排行，感觉这个应该不难？
    - **战队号，战队名、总分、排名、web做出次数、pwn做出次数、misc做出次数，reverse做出次数，杂项做出次数....、总题目次数，**

    - 一血题目号，二血题目号，三血题目号，战队号 —---战队可能会有很多个”几血“，而某个题目应该只有一种”一、二、三血“，这里应该保证每个元组中，仅有一种"几血"具有数据，其余置空
    - 一血题目号，二血题目号，三血题目号，学号（用户号） —---如法炮制
    
    - 由于战队和题型之间有重叠，应该单独对这个**关系**做一个表，其中包括**战队号，战队名，题目号，题目名，题目类型，题目第几次被做出(用以搞定从题目上看一血，二血，三血的问题)，这次加了多少分，发布状态（做出题目后是否被推送的状态，默认为“未发布”）** 对个人而言，也应该如法炮制一个 ——**学号（用户号），用户名，题目号，题目名，题目类型，题目第几次被做出(用以搞定从题目上看一血，二血，三血的问题)，这次加了多少分，发布状态（做出题目后是否被推送的状态，默认为“未发布”）**
    
    - 分数应该可以使用每个战队中个人的分来加和得到
    - 战队和个人的排行榜都可以有，每发现有个人（战队）的分数发生变化，就要将数据库的数据取出来进行排序，再放回去，然后排行榜要实时更新，但数据库的更新应该去感知flag的提交——一旦出现正确的flag提交就要开始更改；实时更新可以使用异步处理
- 实名制**登录认证注册系统**（用学号登陆认证即可，不需要用身份证真的实名认证）
    
    - **战队也必须有一个类似注册的系统来进行组建**
    
    - 收到请求并添加数据库，学号(用户号)、用户名、总分、排行、所属战队号、所属战队名，、web做出次数、pwn做出次数、misc做出次数，reverse做出次数，杂项做出次数....、总题目次数——同样仿照战队
    - 学号应该就是“主码”
- 题目最好能实现动态分值，动态分值就是原本毎题都是1000point，做出来的队伍越多，题目的分值越少，至于最后的算法貌似可以调，就是我们可以控制每多一个队伍作出来降多少分，这个我不知道实现难不难
    - 总之先弄个简单的二分分数，直到某个值之后进行固定
    - 那可能需要动态对数据库的数值进行修改，除了要对显示的这个东西修改以外
- 题目可以放hint，这个应该也不难
- 必须有一个公告栏，就是放一些信息，比如：有哪一个队伍做出了哪一题，哪一题又放了hint，哪个队伍作弊??被逮到了。。。等等消息，还可以放一些比赛的规则之类的东西，这个应该实现也不难。。。。
    - 
- 需要有top10队伍的趋势图。
    - 可能需要前端的绘图库——把单独战队的排名表放在一个里面，可以通过点击选项？依次切换排名
    - 排名问题大概可以利用前面的全排名得到
- 每个用户和队伍可以显示队伍做出题目的具体情况和方向分布，排行等等；每个用户也应该有自己的个人排名。
 
    
    
    - 总题目数量，每种题目所占的百分比，柱形图（左边显示数量，右边显示百分比？，底下显示题目类型）
    - 在个人里可以看到自己的”x血“和战队的“x血”；同理，在题目里也应该能看见哪个战队进行的“x血”

**总的来说，一个平台我们登录进去以后，应该会有五个大板块，分别为：公告，排行，赛题，趋势，战队。**
1. 排行应该有——大列表列出来
    1. 战队排行
    2. 用户排行

2. 公告：公告人工来维护是不是就行了
    1. hint发布情况（一旦发布，用户就可以永久进行查看了，因此可以预先把hint填入，然后设置若hint状态显示未发布时，用户就不能访问到）
    2. 什么队伍又新作出了题（发布之后，并将发布状态改为已发布后，再对队伍的做题数进行改变）;同理，谁又做出了新题也可以这样来做
    
    
    4. 比赛规则（基本不用改）

3. 赛题（docker）

4. 趋势 
    1. 个人趋势
    2. 战队趋势
        - 我发现凡是能对个人进行的排行等操作，也可以同样对战队进行同样的操作
    ----
    4. 赛题趋势
        1. 被做出了几次
        2. 目前值多少分
        3. hint是否发布

5. 可能到时候也需要模式与外模式的切换吧
    1. 目前能做完模式就差不多了
    2. 外模式到时候看需要再说吧
    
<font color = red>每个学生做5个题，要求必须做其他组的题，这应该是所有工作都做完之后要干的了，算是另一个部分</font>



### 好的想法与思路:

**主要元素：
1. Os:*ubuntu* 
    - 没有发现太多的问题
    
3. 服务器：*nginx+反向代理* 反向代理可以防御一些攻击之类的，可能会对之后的平台竞赛有益吧
    - web服务器是软件工具
    - 用于提供http/https访问服务
    - 只用配置即可
    - 布上服务器之后，才可以让自己的网站被其他人所访问
    - 
    
4. DBMS：*Mysql* ——直接从关系型数据库入手，学了这个也相当于为数据库这门课减负了
    - 我大概查了一下，mysql基本一些语言方面没有特别多的兼容性问题；不用担心
    - [mongoDB与mySQL](https://juejin.im/entry/5a18b88951882554b8373e20)
    - 数据库管理工具：~~navicat~~/workbench——解释：navicat要花钱，不干。workbench免费
    - 下方已经附上了装workbench的一些方法
        - [linux安装workbench](https://blog.csdn.net/b2569449528/article/details/78183319)
        - [workbench的开启与使用，比较有用](https://www.linuxidc.com/Linux/2015-06/118366.htm)
    - [Ubuntu18.04 安装MySQL](https://blog.csdn.net/weixx3/article/details/80782479)
   
 
        


   
6. 语言：python 
    - 目前流行度很高，而且学了这个对其他也有帮助
<!--    - PHP 要注意一些版本的选择
    
    - node.js 似乎也不错的样子，基于javascript的后端开发语言 
-->

6. 前端框架：*bootstrp*，好像还有其他的（animate.css） ——bootstrp 好像用得最多呢

    - 前端语言
        - html负责数据组织，使用标签形式
        - css（层叠样式表）负责样式表达，达到表达形式的不同。——采用键值对，对html的某一类内容定义风格
        - 同一个html和不同的css组合，可以产生同样信息的不同风格表达；同样的css可以使不同的html产生不同的风格
        - css可以单独成为文件也可以写在html中
        - css三种写法
            - html的一行内
            - html的页面内
            - 单独成一个文件并在html文件中添加css的链接
        - 所谓的前端框架可能就是一种开源库罢了；

        - javascript 一种轻量级的脚本型编程语言，为web增加了交互，动态效果和行为功能；由浏览器执行并在访问时下载到本地；可以单独成文件.js；
        - 好消息，很多的功能都能由js的第三方库来显示；直接搬来用就可以了；


        - http——各种针对url资源的命令，get、post、put、patch...；http无状态，浏览器不关心服务器，只关心url；
        


    - jQuery之类的；不过这玩意似乎可以算到前端语言
        - jQuery是一个快速，简洁的JavaScript库，由John Resig创建于2006年，有一个很好的座右铭：少写，多做。
        - jQuery 简化了 HTML 文档遍历，事件处理，动画和Ajax交互快速Web开发的。
        - [jQuery教程](https://www.yiibai.com/jquery/jquery-overview.html)


8. 后端框架：简化web开发，框架就是一个web应用的半成品
    - Python：后端语言，业务逻辑的实现

    python知识：
            1. __name__ 相当于“__main__”;——在本文件中是这样；但是在其他文件中__name__的值是那个定义了该变量的文件名







 - flask
        - [官网](https://palletsprojects.com/p/flask/)
        - [如何把flask的web应用部署到linux](https://www.cnblogs.com/AcodingDg/p/10335674.html)
        - [jinja2](https://baike.baidu.com/item/jinja2/8911090?fr=aladdin)
        - [模板引擎](https://baike.baidu.com/item/%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E/907667?fr=aladdin)
        - [Flask+nginx+Gunicorn部署](https://blog.csdn.net/xudailong_blog/article/details/80490137)
        - [基于flask+gunicorn&&nginx来部署web App](https://www.cnblogs.com/luzeming/p/10597878.html)
        - [使用Flask+uwsgi+Nginx部署Flask正式环境](https://www.missshi.cn/api/view/blog/5b1511a213d85b1251000000)
        - [Python3 基于 Nginx 部署 Flask 项目](https://blog.csdn.net/yilovexing/article/details/82969298)
        - 下面两个差不多
            - [python连接mysql---利用mysql-connector](https://www.runoob.com/python3/python-mysql-connector.html)
            - [Python3 MySQL 数据库连接 - PyMySQL 驱动](https://www.runoob.com/python3/python3-mysql.html)
            - [flask-mysql,直接就和模板连接的连接器](https://flask-mysql.readthedocs.io/en/latest/)
            - 从外部连接mysql时，还需要在/etc/mysql/mysql.conf.d路径下使用 sudo vim mysqld.cnf，并将bind- address=127.0.0.1 注释掉


 <!--   
        - 这属于小型项目，我们使用全栈框架的话，反而可能会出现编码不自由，过度受限的情况。
        - [python框架的描述](https://hackernoon.com/top-10-python-web-frameworks-to-learn-in-2018-b2ebab969d1a)
                   - The main idea behind Flask is to help build **a solid web application foundation.** From there, you can use any extensions you might need.
          - 如果您要开发的是一个包含功能和要求的大型系统，那么全栈框架可能是正确的选择。如果您的应用程序位于更小更简单的一侧，您应该考虑使用微框架。但是，框架也可以阻碍发展。在选择全栈框架时，您经常会遇到限制。当然，您可以找到解决这些问题的方法，但要注意不要在为获得无框架python语言上应有的自由时花费过多时间。-->
     
        



<!--       - Django——似乎有即开即用的代码框架-->
<!--
         
        - tornado
      - PHP：[有个推荐网站](https://medium.com/wetprogrammer/2019-php%E6%A1%86%E6%9E%B6%E6%8C%87%E5%8D%97-83d94d403a5b)
    - 如果希望快速打造一個產品原型：Laravel——基于框架 lumen——laravel的微框架,提供现成轮子
        - 優點：良好的設計模式與規範、簡明的開發文件、龐大的社群
        - 缺點：過度封裝與部份功能使其效率較低、社群有些高傲（個人感覺）
    - 如果希望打造穩定的產品：Symfony 全家餐或許會很適合，但全家餐好像挺大的
        - 優點：支援性全面的元件、詳盡到會迷路的開發文件、良好的社群與公司支援
        - 缺點：開發難度稍高、全家餐體積龐大
    - 如果希望效率足夠高而且穩定：phalcon ——快
        - 優點：壓倒性的效能（除了 Swoole 或原生寫法）
        - 缺點：需要額外 extension 支援，造成開發時的難度比一般 PHP 要高
    - 如果希望試試新東西：感觉swoole不错的(要不要试试呢...，搜索了资料感觉还行的样子)——提供轮子框架 ——最快
        - [swoole,laravel,nginx](https://www.jianshu.com/p/1012a6d79177) 
        - Swoole 作為非 HTTP 服務（如 WebSocket）；**异步高并发扩展非阻塞**
        - 用 Zephir 為效能瓶頸寫幾個 extension
        - [zephir01](https://segmentfault.com/a/1190000018270834?utm_source=tag-newest)
        - [zephir官网](https://zephir-lang.com/en)
        - [如何使用zephir](https://www.cnblogs.com/fuland/p/4280456.html)
        - [swoole官网](https://www.swoole.co.uk/)
        - [swoole应该绕过的坑](https://blog.csdn.net/mama476984957/article/details/93174336)
        - [swoole github01](https://github.com/swoole/swoole-src)  
    - node.js：——这样前端使用js好像就能搞定 **也是异步开发**
        - express，最大众的使用，缺点是太过简单，很多东西需要从0搞起，不过似乎也只是对大项目有一些困难，咱们这种小的问题大概不大？
        - koa2，刚开始应用不久, 担心有扩展不足和不兼容问题
        - sails.js，开箱即用的全功能Express增强框架, 内置支持websocket；缺点:(据说)ORM性能不好；这几个看不懂
        - nodejs就是让JavaScript(js)可以实现服务器上的开发。如果会js的话还行；JavaScript(前端语言)+nodejs(JavaScript的运行环境)=实现服务器上的开发(后端技术)，也就是说js+nodejs实现了后端开发的技术
-->
<!--
9. 字体脚本：*font awesome; cufon*如果能美观的话是最好的了

11. 估计用不着了，ftp：pureftpd ??? 但是不用这个服务似乎就可以不下（某b站教程-->

12. 连接池：属于优化用具；
    - Python数据库连接池——DBUtils
    - [连接池](https://www.cnblogs.com/wangkun122/articles/8992637.html)
    - [官方mysql-proxy](https://baike.baidu.com/item/MySQL%20Proxy/2509887)
    - [mysql与atlas与mysql-proxy](https://www.cnblogs.com/yyhh/p/5084844.html)
        <!--    - 可是mongoDB扩展性，灵活性比较强； -->
<!--    [基于php](https://learnku.com/articles/20793)
    [SMProxy](https://github.com/louislivi/SMProxy)
    [现有代码](https://www.jb51.net/article/133709.htm)-->
    
13. 杂项
    - webpack打包工具---将前端代码打包，js，css打包，便于缓存和管理；并且保证版本更新性
    - 
**次要元素
1. 流量分析：<font color = grey> 可能不太用得着呢  </font> *google analytic* 这个份额最大了
2. 内容分发平台CDN：<font color = grey> 有的网站有这个，不知道用处咋样  </font> *cloudFlare*

**扩展性问题**


### 资料:
这里放在网上找到的一些好的资料
[Web-自学](https://www.w3school.com.cn/)
[Web-速查字典](https://man.ilovefishc.com/)
[一些参考价值一般的网站教程01](https://yihui.name/cn/2009/06/how-to-build-a-website-as-a-dummy/)
[一些参考价值一般的网站教程02](https://www.webhostingsecretrevealed.net/zh-CN/blog/web-hosting-guides/make-a-website/)
[Litch大佬的开发记录](https://buptchk.github.io/2019/02/27/LitCTF.html)

[关于.gitignore](https://www.jianshu.com/p/699ed86028c2)
[visual studio + github](https://www.cnblogs.com/sorex/archive/2011/08/11/2134642.html)
[在github上加入本地文件](https://www.cnblogs.com/zhixi/p/9584624.html)
[github关于pull，push与commit](https://blog.csdn.net/zl1zl2zl3/article/details/79922959)
[github项目团队协作开发流程](https://blog.csdn.net/weixin_42052836/article/details/80464923)
[visual studio 与 github的交互](https://github.com/github/VisualStudio/blob/master/docs/using/index.md)
[mysql 学习](https://www.runoob.com/mysql/mysql-tutorial.html)
[flask教程](https://flask.palletsprojects.com/en/1.1.x/tutorial/#tutorial)
[flask快速入门](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart)
[flask项目布局](https://flask.palletsprojects.com/en/1.1.x/)


可以进行实践的一些东西：注意在实践中打开网页的时候要关掉代理。
[visual studio(code)上的一些flask参参考知识——环境设置01](https://docs.microsoft.com/zh-cn/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#use-virtual-environments)
[visual studio(code)上的一些flask参参考知识——环境设置02](https://docs.microsoft.com/zh-cn/visualstudio/ide/quickstart-python?view=vs-2019&toc=https%3A%2F%2Fdocs.microsoft.com%2Fzh-cn%2Fvisualstudio%2Fpython%2Ftoc.json%3Fview%3Dvs-2019&bc=https%3A%2F%2Fdocs.microsoft.com%2Fzh-cn%2Fvisualstudio%2F_breadcrumb%2Ftoc.json%3Fview%3Dvs-2019)
[visual studio(code)中创建和管理python环境](https://docs.microsoft.com/zh-cn/visualstudio/python/managing-python-environments-in-visual-studio?view=vs-2019#selecting-and-installing-python-interpreters)

[visualstudio(code)中使用python](https://docs.microsoft.com/zh-cn/visualstudio/python/tutorial-working-with-python-in-visual-studio-step-01-create-project?view=vs-2019)

### web平台的快速部署
1. 脚本直接在本机上就可以测试，不用非要在ubuntu里写，因为ubuntu容易死机，至少我这里是这样的。
    - 单元测试：测试自己的单个函数的功能
    - 综合测试：把网站开开，在里面输一输，点一点
    - 测试的时候只用在本机上测试，然后完成**数据库的远程连接，数据库直接由协议可以直接利用框架中定义的语句通过ip地址跨机链接**，**服务器配环境，然后本地远程连接对方的数据库** **数据库可视化管理系统（workbench）也可以远程连接，但是和后端这个并不是同一个连接**。这样就已经可以测试>
    - 相对路径基本是跟文件传输有关系的（可能用不着）
    - 数据库服务器不需要外网，只在内网为WEB服务器提供数据查询服务即可。
2. 实际上web平台核心的部件只有两个： 数据库和代码模块（具体来说是后端的代码模块）。后端完成，业务逻辑就完成；数据库结构完成，数据的组织和存储就完成了。**所以，这是我们目前的重点任务，是我们下次课之前的核心任务**
    - 首先是设计数据库的组织形式，这大概是由网站的结构所决定的
    - 其次是对数据的链接和利用，这是后端代码的任务

3. 前端和后端
    - 之所以需要对接，是因为前端页面只负责提供视图没有内容，而后端只提供内容，两者所谓的对接，就是把后端的内容放在前端页面预留出来的位置上。（虽然说是前端后端，但这一对接实际发生在服务器端）。
    - 所以服务器端进行的活动如下：
        - 接收用户请求——》找到负责处理的程序——》处理程序找到要传输给用户的前端页面——》该前端页面留出位置——》后端到数据库取数据——》后端把数据放在前端留出来的位置上——》结合成真正用户看到的html文件——》传输给用户。

4. 但是我们不能忽视前端的简单建设，因为**一定的前端构建，可以让我们的测试更加简单**

5. 大家要尽量熟悉一些github的应用，以便之后好干活。


6. 结构
    - 浏览器<--HTTP--->WSGI（web服务器接口）<--URLS-->web框架

    - web框架<-路由模式-->发送相应的url到对应函数中(系统对处理函数做了相关定位)<---->web框架最终作用于前端与数据库，将前端文件与数据库相分离，分离的同时由利用业务逻辑将其关联

    - 目标：
        - 工程——应用集合
        - 应用——具体应用载体（框架，配置与应用的分离）


1. 定制路由（url与处理函数的关联过程）——path(URL,函数)
2. 定制前端的展示文件
3. 定制数据库的格式
4. 将他们关联




## 设计web安全类题目并部署
### 要求
每人设计2道web安全类题目 *这似乎也比较往后，首先要会做，才会设计，总之还得学习web题目的打法，总之网站要弄好，才能搜集那些题*
*可以尝试把网站都处理好之后再去综合学题目的做法*

<font color = red>基于docker虚拟环境部署题目</font>*所以这个似乎并不是发布在网站上？*

[关于docker](http://m.elecfans.com/article/648468.html)
[关于docker以及docker的部署](https://www.cnblogs.com/aspirant/p/8808809.html)
难易题目各1个

### 好想法与思路


## WEB漏洞安全扫描系统
### 要求
至少支持对SQL注入漏洞、XSS漏洞、上传漏洞和弱口令的扫描（sqlmap似乎也没有支持那么多种，后面还是要看一些其他漏洞扫描模块的实现）
——不过先从sqlmap搞起吧

扫描结果自动形成扫描报告，支持HTML和word输出格式 将扫描结果形成漏洞扫描报告提交 *sqlmap有类似源代码*

每组对其他所有组的CTF网站进行扫描（之后的事，扫就完事了）


### 好的想法与思路:
233
- sqlmap使用python写的，到时候也用python去搞吧;还有一些开源漏扫软件，但是不如集中一点于sqlmap。
- 建完网站之后漏洞不着急填补，可以之后搞出自己的漏洞扫描系统之后和sqlmap得到的东西进行比对，之后再用sqlmap进行审查，清空自己的漏洞

### 资料:
这里放在网上找到的一些好的资料
[sql源码阅读](https://www.cnblogs.com/darkpig/p/6661437.html)
[sql源码分析](https://www.cnblogs.com/natian-ws/p/7806331.html)
sql优化，但据说优化了和没优化差不多...：
[sql优化01](https://blog.51cto.com/13770310/2128197)
[sql优化02](https://blog.51cto.com/13770310/2130522)
[WEB漏洞扫描的开源工具](https://www.22vd.com/40513.html)

## 课后资料与思路

### new文字资料
1. 一般来说应该进行的流程：
web开发->web安全->web安全扫描 循序渐进

2. web设计:尽量美观比较好。

3. 版本控制服务器
    - 为了防止版本中间出现混乱，并且可以做还原一类的东西；
    - 老师说，github也可以有相似的效果
4. 人员进行分工：
    - 老师建议规定制度：每一个人工作占比；在报告里体现占比；督促机制；
    - 一个想法：可以一起放到github中然后每个人写完代码之后署上自己的名字；
    

5. 关于题目的想法:
    - 做题者自行上传题目的设想（似乎难以实现；
    - 请参考图片里的一些资源，可以的话之后会把图片的文字放过来

6. webpack打包工具---将前端代码打包，所有的js，css均会打包成一个文件，便于缓存和管理；并且保证版本更新性；

7. 框架的目的：避免让我们接触原生问题；

8. json：应用数据传输格式
   接口采用RESTful？
   Ajax 即“Asynchronous Javascript And XML”(异步 JavaScript 和 XML),是指一种创建交互式网页应用的网页开发技术。——对于动态变化的页面，只需要从后台获取中间变化的代码而不需要刷新整个页面。web2.0
   HTML5+CSS3，web自适应和普世应用，自适应系统以及屏幕 web3.0（似乎还并没有到来）
   
   

9. **一些工具 第四步的东西**
    - **command-line= 后端版本？处理**
    - docker container/image management=分发和管理

10. 开源协议：appache等一系列协议（到时候需要查一查）

11. 从老师那里收集到的一些资料
    - 关于报告
        - 之后的报告+进度作为评分标准
        - 这次不用报告，之后的每次要写报告+ppt，学委**电子版**收齐即可。
        - **之后的每次应该有报告，虽然据说没有也可以，但是考虑到最后会让做一个大报告作为整体成绩，所以老师建议我们每次还是写，以便为期末考试减负.**
        - **另外，报告格式好的话会有加分。报告应该有目录，通过目录展示自己清晰的逻辑会留下好印象。**
        
        - 但是后期可能用不到ppt了，需要自己把电脑拿上来用电脑展示网站界面以及一些动态的东西
        
        - 经验：调研最好写出统计结果是何时归纳的（如果没有就没办法了）
        
    - 关于进度问题
        - pdf中的报告的内容框架**只是一个梳理**，实际上进度还是按照自己的来，在力所能及的范围下，越快越好

    - 一些大致的进展情况
        - 除了最后两次集中，之后的课会**大约2-3周**上一次
        
        - **前期**：
            1. web要把前后端，数据库，等东西大致连起来，弄出雏形；最好再放上一些题目
        
        - **中期**
             1. 部署题目（在这之前要熟悉）

             2. 测试网站具体功能和服务正常运行的情况
        - **后期**
    
            1. 互相做题与攻防——防御的主要目的是为了测试“编码安全性”，因为如果编码没有问题，就扫不出漏洞；当然老师也并不排斥我们使用**现成的"WAF"**——web应用防火墙，或者去找**开源防火墙代码**;**最后能否被攻破应该也是一个考核标准**
            
            2. 看最后自己的时间情况，做出自己的渗透扫描工具——**也就是说这个应该是最后的模块，而且也没有特别重要；当然，如果大家有时间还是尽量把它做好，也达到一个学习的效果**
            3. 关于渗透扫描工具，我们
                - 可以直接在开源代码上换个模样
                
                - 或在开源上自己添加代码(推荐)
                
                - 或自己编写（肯定编不过sqlmap，但是根据学习能力和成果会给分）
                - 以上三个从上到下分数会依次变高




### 图片资料
![01.jpg](https://i.loli.net/2019/09/19/9HRsajfty7Yiv58.jpg)

![02.jpg](https://i.loli.net/2019/09/19/UmBEVvJ1dHoXA6Z.jpg)

![05.jpg](https://i.loli.net/2019/09/19/lanJ1Yz5EhjpHmM.jpg)

![09.jpg](https://i.loli.net/2019/09/19/TsqYJP8HGSkFi7c.jpg)

![08.jpg](https://i.loli.net/2019/09/19/Xuk7foELrSnt4RG.jpg)

![04.jpg](https://i.loli.net/2019/09/19/Bby7f6lUIahpe4m.jpg)

![10.jpg](https://i.loli.net/2019/09/19/IjEgWsZ3UHOlqtB.jpg)

![03.jpg](https://i.loli.net/2019/09/19/LyOaRjucd9h8TKM.jpg)

![06.jpg](https://i.loli.net/2019/09/19/cS8usZbY7lidWhE.jpg)

![07.jpg](https://i.loli.net/2019/09/19/RKZWVLkXyow6B4N.jpg)

![11.jpg](https://i.loli.net/2019/09/19/xwJvmHI9lhkKbYd.jpg)

![12.jpg](https://i.loli.net/2019/09/19/yNEDfSHX8dJRtM1.jpg)

![13.jpg](https://i.loli.net/2019/09/19/65YkjilhJEdtcB3.jpg)

![15.jpg](https://i.loli.net/2019/09/19/q4ea3UtKY9sXymE.jpg)

![14.jpg](https://i.loli.net/2019/09/19/yGBUjwFxbfOMahL.jpg)

![16.jpg](https://i.loli.net/2019/09/19/y4jtveJsoYwiabQ.jpg)