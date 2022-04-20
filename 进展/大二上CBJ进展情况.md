# 大二上CBJ进展情况
### 资料

[可用于xss攻击测试的网站 类型：>.xss.<](http://testphp.vulnweb.com/search.php?test=query)

[xpath基本情况1](https://zhuanlan.zhihu.com/p/29436838)
[xpath 轴用法](https://www.jianshu.com/p/1575db75670f)
[etree中的element](https://www.cnblogs.com/ifantastic/archive/2013/04/12/3017110.html)

[colab](https://www.jianshu.com/p/ce2e63d1c10c)
https://zhuanlan.zhihu.com/p/43746516
https://juejin.im/post/5b345a49f265da599c561b25
[tensorflow库](https://docs.google.com/spreadsheets/d/1FLFJLzg7WNP6JHODX5q8BDgptKafq_slHpnHVbJIteQ/edit#gid=0)
[NVIDA计算库](https://www.joe0.com/2019/10/19/how-resolve-tensorflow-2-0-error-could-not-load-dynamic-library-cudart64_100-dll-dlerror-cudart64_100-dll-not-found/)
-[有用的flask文章](https://www.cnblogs.com/franknihao/category/1059940.html)
[opencv1](https://www.jianshu.com/p/5cdf22d657c6)
[opencv2](https://www.jianshu.com/p/0287bcd24f78)

[知乎 验证码登录型](https://zhuanlan.zhihu.com/p/26102000)
from requests import get,post,Session
[github反反爬虫](https://github.com/luyishisi/Anti-Anti-Spider)

REQ_HEADERS = {
    "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.110 Safari/537.36",
    "Referer": "http://www.ichunqiu.com/login"
}
#下面换成你的账号信息
REQ_PAYLOAD = {
    "username": "18888888888",
    "password": "99999999",
    "yzm": None,
    "rem": 0
}


S = Session()


R_1 = S.get("http://www.ichunqiu.com/login",headers=REQ_HEADERS)

R_2 = S.post("http://www.ichunqiu.com/loginCtl/dialog_login",headers=REQ_HEADERS,data=REQ_PAYLOAD)

R_3 = S.get("http://www.ichunqiu.com/personal/selleft",headers=REQ_HEADERS)

R_3.encoding = "UTF-8"
print R_3.text
pwnable.tw

[python concurrent 多线程，写的还不错](https://blog.louie.lu/2017/08/01/%E4%BD%A0%E6%89%80%E4%B8%8D%E7%9F%A5%E9%81%93%E7%9A%84-python-%E6%A8%99%E6%BA%96%E5%87%BD%E5%BC%8F%E5%BA%AB%E7%94%A8%E6%B3%95-06-concurrent-futures/)

[zip，多个可迭代对象，每次选取其中的每一个，总体成为一个元组，最终打包成一个大元组列表](https://www.runoob.com/python/python-func-zip.html)

[python使用requests POST提交一个键多个值](https://blog.csdn.net/win_turn/article/details/54849734)

[知乎headers添加教学](https://zhuanlan.zhihu.com/p/35643481)

别人配置好的SQLilabs：http://43.247.91.228:84/


[我们的网站地址（我记不住）](http://49.233.168.44/)
xiaoxiaorenwu xqh000521
ws 123456

[xpath+requests](https://blog.csdn.net/jeikerxiao/article/details/73530529)

[beautifulsoup+regular expression](https://www.jianshu.com/p/ceb99aed4b2e)

[urlparse](https://docs.python.org/3/library/urllib.parse.html)

[在线正则](https://tool.oschina.net/regex/)
resp.text返回的是Unicode型的数据。

resp.content返回的是bytes型也就是二进制的数据。

也就是说，如果你想取文本，可以通过r.text。

如果想取图片，文件，则可以通过r.content。

（resp.json()返回的是json格式数据）

举个栗子
例如下载并保存一张图片

import requests

jpg_url = 'http://img2.niutuku.com/1312/0804/0804-niutuku.com-27840.jpg'

content = requests.get(jpg_url).content

with open('demo.jpg', 'wb') as fp:
    fp.write(content)

 "text/html" !=
 
 s = requests.Session()
s.auth = ('user', 'pass')
s.headers.update({'x-test': 'true'})

# both 'x-test' and 'x-test2' are sent
s.get('http://httpbin.org/headers', headers={'x-test2': 'true'})

s = requests.Session()

r = s.get('http://httpbin.org/cookies', cookies={'from-my': 'browser'})
print(r.text)
# '{"cookies": {"from-my": "browser"}}'

r = s.get('http://httpbin.org/cookies')
print(r.text)
# '{"cookies": {}}'
 
 
 
 
[001xpath--可以定位文档中元素的位置,或许有替代正则的可能](https://zhuanlan.zhihu.com/p/29436838)
[002反爬,proxy,cookie（带验证码的cookie？！！！！！）；反盗链，ajax！！！](https://www.zhihu.com/question/35461941)

[003快速上手](https://2.python-requests.org//zh_CN/latest/user/quickstart.html)
??(http://www.voidcn.com/article/p-ojkkorrn-mr.html)
[004高级用法](https://2.python-requests.org//zh_CN/latest/user/advanced.html)

[常见的post方式，有时间的话可以看看吧，作为表格的一些过滤的东西](https://www.jianshu.com/p/ba40da728806)

[requests](https://2.python-requests.org//zh_CN/latest/user/quickstart.html)
[cookie增删改查](https://blog.csdn.net/titiyufeng/article/details/53182951)
[requests.session保持cookie1](https://blog.csdn.net/u013061183/article/details/78455013)
[requests.session保持cookie2](http://irootlee.com/python_cookie/)
[](https://www.ituring.com.cn/article/200288)
## 可用项目
- 伪造登录
- 多线程
- 扫？
- 爬虫

1. sql
    - 先去扫目录
    - sql----drone
    - \ 反斜杠 '\username ='$post
    - ||或
    - 限定list的范围
    - flask框架的debug模式
    - debug pin码---固定参数进行构造
        - 任意文件读
        - pin码读
        - 对docker进行了优化，从其他地方读取
        - owaspzap

2. xss----
    - xsser
    - 扫描目录
    

3. pwd common crack（根据post信息得到
    - ip随机化
    - 大字典
    - 递归/迭代

4. 文件上传：burpsuite和 firebug
    - docx jinja2 生成统一报告
    - 插件化系统----蓝图



5. 靶机
- DVWA
- SQLI-LABS
- PIKACHU
- UPLOAD-LABS


6. 见图



7. 可用网站
 - 御行车网




### 
[csrf01](https://www.cnblogs.com/phpstudy2015-6/p/6771239.html)
[csrf02 全](https://www.ibm.com/developerworks/cn/web/1102_niugang_csrf/index.html)
[xss](https://portswigger.net/web-security/cross-site-scripting)

### 学习
[yield 生成元函数](https://www.ibm.com/developerworks/cn/opensource/os-cn-python-yield/index.html)
[join()](https://www.runoob.com/python/att-string-join.html)

[正则表达式：命名捕获组](https://blog.csdn.net/lxcnn/article/details/4146148)

[mechanize browser](https://blog.csdn.net/zhaodedong/article/details/46432921)
[request.session 高级](https://2.python-requests.org//zh_CN/latest/user/advanced.html)

### 报告生成
[word报告 知乎](https://zhuanlan.zhihu.com/p/25552931)
[word报告 csdn](https://blog.csdn.net/cloveses/article/details/81668797)
[html报告](https://blog.csdn.net/mlgglm/article/details/51463588)

[漏扫格式,但是用不出来](https://support.huaweicloud.com/vss_faq/vss_01_0145.html)

[word paragraph 空行](https://python-docx.readthedocs.io/en/latest/_modules/docx/text/paragraph.html)

[sql毒化](https://www.eliacom.com/mysql-gui-wp-sql-poisoning.php)

[sql 盲注](https://blog.csdn.net/qq_35544379/article/details/77351783)

[dom xss](http://blog.nsfocus.net/xss-advance/)

### 漏洞扫描优秀案例
[scannerbox](https://github.com/We5ter/Scanners-Box/blob/master/README_CN.md)

[w3af](https://github.com/andresriancho/w3af)

[WAScan](https://github.com/m4ll0k/WAScan)






### 漏洞扫描

[漏扫的一个感悟] (http://www.langzi.fun/)

[关于漏扫](https://zhuanlan.zhihu.com/p/25492970?utm_source=qq&utm_medium=social&utm_oi=1072201792204611584)

[漏洞工具集](https://bbs.ichunqiu.com/thread-17913-1-1.html)

[漏洞扫描器](https://bbs.ichunqiu.com/thread-18495-1-1.html)

[sqlmap使用扫盲贴](https://bbs.ichunqiu.com/thread-18211-1-1.html)

[版本库urllib](https://blog.csdn.net/fengxinlinux/article/details/77281253)





#### github 优秀案例
[boy-hack](https://github.com/boy-hack)

[WAScan](https://github.com/m4ll0k/WAScan/blob/master/lib/request/crawler.py)

[Sitadel](https://github.com/shenril/Sitadel)

[scrapy爬虫？](https://www.digitalocean.com/community/tutorials/how-to-crawl-a-web-page-with-scrapy-and-python-3)


[1](https://zhuanlan.zhihu.com/p/31578911?utm_source=qq&utm_medium=social&utm_oi=1072201792204611584)

[2](https://www.zhihu.com/question/21190186/answer/48480498utm_source=qq&utm_medium=social&utm_oi=1072201792204611584)

[3](https://zhuanlan.zhihu.com/p/79526694?utm_source=qq&utm_medium=social&utm_oi=1072201792204611584)




### 第三次汇报
1. tomcat进行消息队列/message

2. [数据库迁移？；似乎这样做可以可以保自己错误的底](https://flask-migrate.readthedocs.io/en/latest/)

3. 用户信息
    - 从team里点击进入
    - 直接从用户排名进入
    - 总之应该确实可以看
    - 别的人点进自己的信息，和自己点进自己的信息

3. problem.html 要po出题目描述

4. 计时器？
5. 题目？验证码

6. 猜你喜欢
    - 通过权重：您喜欢的题目类型
8. 题解

9. write up；修改write_up/创建write_up

10. contest功能----> contest服务
    - 获得所有比赛
    - 提交数据库
    - 所有比赛
11. 图片一般不放在数据库，只用文件系统进行大文件的上传

12. 美化

14. 数据库密码加密

14. 消息面板？？？？？


15. 网站安全性评估


16. ajax

17. redis，tomcat

18. 网站论坛，对内容进行爆破防止XSS；为什么不用表单实现csrf攻击呢


19. 用户头像和战队头像

20. 已经login的不能再login

21. 管理页
22. 做过题之后的显示变化
23. 





### 讨论
1. my information: 
    - 删掉submissionsproblem tried，然后最后要画个饼图，然后只保留problems solved。可以把各种题目做出的次数放到problems solved框的下面
    - 下面的我的提交（my submissions改成my solution）只保留已经提交成功的记录，并且在最右侧加一个一血二血三血的图标
    -  把那个各类的题目做题数去掉。并且加一个饼图，饼图右侧放上做题数目，饼图的每一块放入百分比
    - 注意题目的最右侧要打上时间戳（后端去做）

3. 主页中右下角
    - 的是最新做出的三道题情况；直接从用户信息中提取就可以（主要是要有信息）
4. 题目页面
    - 每个题目不同的颜色
    - 动态改变进度条，以及进度条右侧的已做/总 题目数 （模板引擎）
5. 战队
    - 在战队排行里把date数据去掉

    - 战队人数要可变，里面有几个人就显示几个
    - 可以创建战队，战队创建完之后要能在前端列表显示（列表显示采用litch的方案）
    - 在战队列表的栏目里甚至可以去掉战队的分数
    
6. 注册
    - 真实姓名可以删掉
7. 登录
    - 以后或许可以优化成输入验证码错误也不刷新
    - 是不是可以整体将页面上移，这样sign就不会漏出去了

7. homepage中战队的搜索功能可以去掉

8. 必须增加找回密码的功能

9. litch的列表建议
    - 元组列表，模板引擎，可变长------>>>>实现变长列表；你把那个list传到前端 前端去遍历list
    - 生成你的表格；嗯。也就是说我每次排名有变动的时候先在后端进行数据变动与排序，然后通过模板引擎传给前端，每次都动态生成不一样的表格？
    - 对


8. 比较困难的问题-----我先去查查资料，之后再问学长也不迟
    - ！！！点击申请加入后要能发送给队长，队长点击加入后要切实将用户加入进战队中
    - 怎样把这样一条请求向用户传递呢，利用个人消息栏？
    - 如何确定用户的登录信息；如果用户直接输入homepage，但是它的登录状态是未登录状态，就强行跳转回登陆页面

9. 出现了即便验证码不对也可以登录的问题
    - [js向flask传数据](http://www.voidcn.com/article/p-mrtkcbyy-btm.html)
    - [前端后端数据交互问题](https://www.zhihu.com/question/26532621)
    - [flask写验证码](https://blog.csdn.net/qq_41376740/article/details/79464805)


    




11. 关于占登陆页面的sign的问题(已解决)
    - [flask弹窗](https://kknews.cc/code/5gox2o8.html)
    - 使用flask函数默认再地下进行弹窗，或许可以改变位置，但是目前不知道，



13. ???
    - echarts-js可视库

14. 之后的数据测试应该怎么办呢，感觉只要出现一点问题就会很麻烦。...

10. 可能可以增加的功能
    - 邮件认证
        - 支持，和http实现差不多
        - 可以尝试使用
    - 管理员端
    - cookie
    
    - **一血二血三血的图标或许可以改得更好看**
### 课上学习
#### 要尽快解决的问题
1. 用户注销
2.  一个人最多创建一个队伍，一个人在队伍里就不能加入另一个队伍----如果数据库中有队伍的对应就不能再进行任何关于战队的操作（注销之后在考虑）
3.  战队申请和战队邀请
4. 谁创建战队谁就是队长-----只有队长才是
12. 必须尽快解决验证码的冲突问题
4. 邮箱认证未必要点击连接返回登陆页面，也可以实现只发送用户码；但是必须要提上日程
5. 拦截器要尽快实现
    
6. 排名（其实感觉一般难吧）
    
7. docker
    - 搭建环境；
    - 给一个网页 

8. 管理员界面
    
9. 用户好像本来就是profile界面

10. 可以将时间戳放在主页面
     
    
#### 一些看不太明白的东西或者不知道有没有用的东西

- 部署题目
- 旋转字体，比较好看的布局
- 加入队伍，解散队伍，创建队伍
- 阿里云云端服务器电话认证
- 会话管理，权限管理
- service层，自己调用自己写的函数——————主要写个自己定义的函数来封装复用的大逻辑问题
    - 将复杂问题下发下去。
- controller层，
- 团队名找团队；通过team0 leader找到团队；用团队找到所有成员名；
- 团队解散
- 加入队伍，权限，有很多的东西，最好先用api
- 题目撤回 
- 数据库密码加密？？？
- docker部署题目，其他网络框架搭建web app 题目
- docker部署题目和主app，主app不需要知道docker有没有得到正确的消息，只需要docker作为中间层？
- 拦截器：防止不登陆做题。直接跳转会。全部拦截到login
- 建立了团队不能再加入团队。之类的一些判断。
- logo
- 上传头像---文件上传
- 个人资料的修改
- 进入到主页的动态效果，动画
- 已经拥有队伍就不能再加入其他队伍了
- 只有队长可以对队伍进行删除
    - 队员不能删
    - 只能是
- 密码非法字符的判断以及如果全是数字就....
- 导航栏右侧，打出：“欢迎你xxxx”-----
- 路由树，路由结点和中间节点？
- session恢复与设置---跟住设备；是不是登录了；没有就增加，有了就增加新的； redis存session
- check：contest，admin，team资源层级？？？
- snapshot，管理员添加？多成员，多team

#### 课上的注意事项
1. 以后展示尽量写出关键技术
    - 实现原理，代码部分可以说一下大致的用途
    - 说出特色的东西
    - 既介绍原理，也用代码配合起来。扩展视野（反正老师爱看）
    - 尽可能做出突出工作并写出来
    - 老师也能看到，这样才能比较好一些

 
2. 实践课就是为以后的简历加分的
    - 拿得出手的对保研出国也有帮助
    - web漏洞扫描做得好的话。就是新的技术
3. 开发方法
- 设计开发，网站该有什么功能，先做信息分析。先做出需求，再考虑设计开发，这样才好做。
    - 前端
    - 后端
    - 数据库
- 敏捷开发（不用太多时间分析需求）
    - 直接写代码
    - 短平快看到结果









## 前端


1. 初始页面
    - 可以先倒是可以设一个主页，里面只有登录和注册按钮。 然后等他身份确认之后再进入正式界面
    - 之后可以为了美观做一些动态效果（粒子，动图，动态字）

2. 正式页面
    - 主页面最好能空出来 就是做一个比较简洁大方的主页面 然后顶部导航栏放注册登录等等，然后导航栏用base.html来管理（我看网上和穆克燃他们都是这么写的。。。）
    - 正式页面中的上面有几个板块分别写着一些对应的功能；
    - 然后最好在右上角有注销按钮，以及用户的一些个人状态查询按钮，这几个按钮可以做成菜单形式
    - 可以在该页面的空白处写上公告
3. 关于题目
- x血的表示和题目的展示，可以按照之前的说法去搞

[js与post](https://blog.csdn.net/JackLiu16/article/details/79590840)

## 后端

### 登录
- 在没登陆之前，如果要进入主页面的话会被强行重定向回登陆页面。
- 数据库的插入操作--二分查找？----- 用户的用户号（学号）是字符串类型
- 

### 数据库
1. 直接使用sql-connector
    - [直接使用mysql语法](https://www.liaoxuefeng.com/wiki/1016959663602400/1017802264972000)
    - [runoob](http://www.runoob.com/python3/python-mysql-connector.html)
2. 使用alchema
    - [如何用sqlalchema连接多个数据库](https://blog.csdn.net/chenmozhe22/article/details/95953027)
    - [连接数据库01](https://www.jianshu.com/p/9893aaf40b91)
    - [连接数据库02](https://www.liaoxuefeng.com/wiki/1016959663602400/1017803857459008)
    - [连接数据库03](https://blog.csdn.net/will130/article/details/48442699)

### FLASK
[flask模板学习](https://blog.csdn.net/troysps/article/details/80466916)
[注册？](https://www.jb51.net/article/110863.htm)
[redirect](https://blog.csdn.net/srg1011/article/details/74104499)
[flash](https://www.yiibai.com/flask/flask_message_flashing.html)
emmmm，看了CTFd的项目规模以后，我才发现自己一直小看了这个作业orz，三个人自己独立来写根本是太宏大的项目，找框架往里套前端和功能函数才是正道(逃

我大致看了看CTFd的结构图，学了一点flask以后貌似看得会清楚很多
先放一下**本地**跑起来的过程:
```
mkvirtualenv -p python3 CTFd   //创建虚拟环境
python3 -m pip install --upgrade pip  //升级pip
git clone https://github.com/CTFd/CTFd.git  //克隆项目到本地 
cd CTFd //进入项目
python3 -m pip install -r requirements.txt //安装项目所需的包
python3 serve.py //将本地服务器跑起来

之后访问127.0.0.1:4000即可
```
现在我jio得面临的困难主要有两个：
1. 看懂CTFd的框架结构，搞清楚他文件与文件之间的联系，不然没法修改或插入自己的东西。
2. 我们对数据库的操作还不太娴熟？？？也有可能是我看的比价少，感觉数据库占的分量还是蛮大的。。。毕竟这个东西从根本上讲就是数据，各种乱七八糟的数据排个版给大家看。。。

还有就是他这个前端巨丑，**而且貌似没有发公告的功能**
看网上一些文章说可以直接在admin页面搞东西？？？新建Page等
感觉没什么用的一些链接，貌似搜不到具体的对CTFd的分析，都是一些零碎的点：
https://blog.csdn.net/weixin_43918621/article/details/84768735
https://www.heibai.org/post/1441.html
[一些零碎的点和php题的部署方法？？](https://www.itread01.com/qiplc.html)
https://blog.zeddyu.info/2018/11/20/SUCTF%E5%B0%8F%E8%AE%B0/

### 读了一会的收获，没写的基本是不知道的，写了的也不一定对。。。

## 关于docker
理解：
其实docker就像是一个轻量级的虚拟机，他本身出现的原因就是为了解决虚拟机占用资源大，冗余等缺点，docker具有很好的移植性和隔离性，服务器上可以跑多个docker，互相之间不会相互影响。
较详细教程，看完这一篇差不多了：
[Angel_kitty师傅blog](https://www.cnblogs.com/ECJTUACM-873284962/p/9789130.html)
[dockerfile与docker-compose的辨析](https://segmentfault.com/q/1010000009883848)
[docker-compose.yml简介](https://juejin.im/post/5aed4a776fb9a07a9918bb42)

我们需要买一个云服务器么？感觉也不贵，我可以买一个，自己以后估计也可以用

### docker部署web题（working...）
我不是很知道真正的web题是个什么形式。好像web对环境的要求比较高，不同的题有不同的环境依赖，到时候真的放题时还得依据题目来配。lamp好像用的比较多。
（我看基本都是三个命令就搞定了。。。感动中国.jpg）
```
docker pull ==>拉取需要的镜像           （lamp用的较多）
docker run ==>运行容器并进行端口映射             （将docker的一个端口映射到宿主机）
docker cp ==> 将题目从本地目录部署到docker目录   （题目就是一个html文件，就等于是复制一个html文件。。。）
```
[docker搭WEB题----tutum/lamp镜像](https://xi4or0uji.github.io/2019/02/19/%E7%94%A8docker%E6%90%AD%E4%B8%AActf%E9%A2%98%E7%9B%AE/)
[docker搭WEB题----dockerfile的生成](https://www.cnblogs.com/ichunqiu/p/10601807.html)

### docker部署pwn题（已成功）
因为之前出题办比赛，之前就有自己部署过pwn题，比较简单，网上有现成的框架，xinetd一次只能部署一道题目，很操蛋，pwn_deploy_chroot更加高级和安全，已经可以成功部署，一次可以放五到十道题，且限制了用户的权限，flag可以自定义。

[ctf_xinetd--github](https://github.com/Eadom/ctf_xinetd)
[pwn_deploy_chroot--github](https://github.com/giantbranch/pwn_deploy_chroot)
[pwn_deploy_chroot教程](https://blog.csdn.net/u012763794/article/details/82988934)

crypto, misc, re正常情况下都不需要用docker部署，因为他们的flag藏在题目给的文件本身里，我们只需要通过解密来获取，不像pwn和web需要日远程服务器拿到shell看flag。



## 数据库—————数据架构已基本完成
<!--
### 根据网站架构的大概构想，进行的一些数据库数据组织方式，以及之后业务的使用方式进行的考虑

- 支持最基本的web,pwn,reserve,misc,杂项五类题型，并从网上收集相关样题（每类不少于3道）布置到CTF网站上
    - 前端：文字的显示+js的按钮效果
    - 后端的代码应该把对应数据库的数据拉出来
    - 即每一个对应的题型，都应该至少有自己的一个数据表来存储（但这个最后的实现是用docker完成的），麻烦之后研究一下数据库和docker的结合
    
#### 每个题应该有 题目号，题目名，题目类别，题目难度，被做出的次数(与后面的可加分数相关)，目前题目可加分数，一血战队号，二血战队号，三血战队号，hint状态(是否放出hint，默认为"未放出"),hint（短的话就可以放在其中）,题干（题干要不要放），一血用户号，二血用户号，三血用户号

- 对应的数据拉出来之后，以前端定义好的模式显示
- docker：部署题目（xint等）（一次部署五道题？）
- 每道题目需要显示有哪些队伍做出来（其实显示一二三血即可，高级一点的可以显所有做出来的队伍，这个感觉也不难）
- 网站必须显示各个战队的分数，做出来的题目有哪些（最好能显示一二三血），进阶：显示个人分数排行，感觉这个应该不难？
#### 战队号，战队名、总分、排名、一血次数，二血次数，三血次数，web做出次数、pwn做出次数、misc做出次数，reverse做出次数，杂项做出次数....、总题目次数

#### 战队号，一血题目号，二血题目号，三血题目号 —---战队可能会有很多个”几血“，而某个题目应该只有一种”一、二、三血“，这里应该保证每个元组中，仅有一种"几血"具有数据，其余置空

#### 学号（用户号），一血题目号，二血题目号，三血题目号 —---如法炮制
 
- 由于战队和题型之间有重叠，应该单独对这个**关系**做一个表，其中包括

#### 战队号，战队名，题目号，题目名，题目类型，题目第几次被做出(用以搞定加分，以及从题目上看一血，二血，三血的问题)，这次加了多少分，发布状态（做出题目后是否被推送的状态，默认为“未发布”） ——关系，战队与题目共同属于一个主键，因为战队不可能做两道同样的题


- 对个人而言，也应该如法炮制一个 
#### 学号（用户号），用户名，题目号，题目名，题目类型，题目第几次被做出(用以搞定从题目上看一血，二血，三血的问题)，这次加了多少分，发布状态（做出题目后是否被推送的状态，默认为“未发布”）
  
- 分数应该可以使用每个战队中个人的分来加和得到
- 战队和个人的排行榜都可以有，每发现有个人（战队）的分数发生变化，就要将数据库的数据取出来进行排序，再放回去，然后排行榜要实时更新，但数据库的更新应该去感知flag的提交——一旦出现正确的flag提交就要开始更改；实时更新可以使用异步处理

- 实名制**登录认证注册系统**（用学号登陆认证即可，不需要用身份证真的实名认证）
    
- **战队也必须有一个类似注册的系统来进行组建**
    
- 收到请求并添加数据库，学号(用户号)、
    
#### 用户号、用户名、总分、排行、所属战队号、所属战队名，、web做出次数、pwn做出次数、misc做出次数，reverse做出次数，杂项做出次数....、总题目次数，一些次数，二血次数，三血次数

- 学号应该就是“主码”
- 题目最好能实现动态分值，动态分值就是原本毎题都是1000point，做出来的队伍越多，题目的分值越少，至于最后的算法貌似可以调，就是我们可以控制每多一个队伍作出来降多少分，这个我不知道实现难不难
    - 总之先弄个简单的二分分数，直到某个值之后进行固定
    - 那可能需要动态对数据库的数值进行修改，除了要对显示的这个东西修改以外
- 题目可以放hint，这个应该也不难

- 必须有一个公告栏，就是放一些信息，比如：有哪一个队伍做出了哪一题，哪一题又放了hint，哪个队伍作弊??被逮到了。。。等等消息，还可以放一些比赛的规则之类的东西，这个应该实现也不难。。。。
    
- 需要有top10队伍的趋势图。
    - 可能需要前端的绘图库——把单独战队的排名表放在一个里面，可以通过点击选项？依次切换排名
    - 排名问题大概可以利用前面的全排名得到
- 每个用户和队伍可以显示队伍做出题目的具体情况和方向分布，排行等等；每个用户也应该有自己的个人排名。
 
    
    
    - 总题目数量，每种题目所占的百分比，柱形图（左边显示数量，右边显示百分比？，底下显示题目类型）
    - 在个人里可以看到自己的”x血“和战队的“x血”；同理，在题目里也应该能看见哪个战队进行的“x血”



-->


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


6. 操作中出现的问题 
- score---可以为负
- rank----考虑并列
- 外键去关联姓名还是序号要相同啊！
- 题目，战队的序号类型和用户类型不一样，用户的序号类型应该是字符串；
- 重复做题，不加分。后台查看发布状态，若为已发布，则不会再受理这条消息；当然，我们一定要让状态属于‘未发布’时，阻断其他的提交操作
- 并且这个状态还用来当作是否将这个题的分数赋给了对应的战队和用户
- 在发布前，还应该改变题的已做次数，以及题的现有分数（如果分数还会改变的话）
- 太好了，唯一约束对null并不起作用；
- primary似乎比unique还要更进一层，所以混用也可能不会有毛病；因为primary不能为null并且还是唯一的；当然primary是共有值的；
- user blood和 team blood 这两个，某一个blood存在的时候其他的值就必须为null这个还并没有进行很好的设置；
- primary和unique为什么能在workbench中共同显示？


- 数据库的隔离性目前使用默认的可重复读，虽然可能会造成幻读，但是串行化的话不会太慢了吗；串行化倒是没有安全隐患...

- 对于事物的控制！ commit 与 transaction


7. [也太狠了](https://www.zhihu.com/question/39967106)
8. 或许不该把用户号也算作主键吧



### ddl
- [json数组](https://www.runoob.com/json/js-json-arrays.html)
- [json字符串](https://www.haorooms.com/post/json_object_json_string)
- [js声明变量](https://blog.csdn.net/qq_27261333/article/details/69486540)
- [flask 对象json序列化](http://zhizhi.tangliangdong.me/2017/11/22/2017-11-22-flask-json-serialize/)
- [这个溜了](http://cn.voidcc.com/question/p-crhdaqap-yy.html)


### 新

#### GIT
[gitbash](https://blog.csdn.net/Lucky_LXG/article/details/77849212)
#### 编码资料
- mysql中的真utf-8--->utf8mb4
- [模组应用](https://www.ctolib.com/topics-123490.html)
- [html表单怎么定位给某个函数传数据](https://blog.csdn.net/xx123er/article/details/77945283)
- [管理静态文件](https://spacewander.github.io/explore-flask-zh/9-static_files.html)
- [帮助文档](http://docs.jinkan.org/docs/flask/quickstart.html)
    - 可加参数的url，对于每一个用户，他的用户名或许得作为url的一部分才能保证一一对应---**之后要再去看看那个flask教程**
        - [欢迎页面，hello，xxx--](https://blog.csdn.net/tingyuanss/article/details/46423699)
        - 但是这个东西感觉直接在前端模板里用后端拉取之后用模板引擎从后端拉出这个数据直接推到前面就好了
- session
- [导入其他文件的函数或类；处理复杂逻辑时，需要专门找一个文件写个函数](https://blog.csdn.net/qq_36134318/article/details/80640667)

- 用户类-战队类？题目类？
- 数据库的连接类？
- [关于类的介绍](https://www.zhihu.com/question/27699413)
- [继承与多态](https://www.cnblogs.com/feeland/p/4419121.html)
    - 战队类和用户类可以继承自同一个基类
    - 题目类本身可以定一个类
        - 然后下属每一种类型的题目再定一个？

- [装包以及init和runserver](https://dormousehole.readthedocs.io/en/stable/patterns/packages.html#larger-applications)

- [蓝图帮助+自定义静态、模板文件的位置](https://dormousehole.readthedocs.io/en/stable/blueprints.html)

- [提到了后台和管理员+蓝图](https://zhuanlan.zhihu.com/p/46034518)

- [flask入门教程](https://greyli.com/flask-tutorial-chapter-10-organize/)

- [简单版蓝图教程](https://www.zhihu.com/question/31748237)

- [竟然找到了关于session+相应+重定向的东西+蓝图+上传文件](https://www.smi1e.top/python%E6%A1%86%E6%9E%B6flask%E5%9F%BA%E7%A1%80%E5%AD%A6%E4%B9%A0/)
    - url_for()
    - session/log_out
    - 
- [蓝图](https://lvxiaoyu.com/static/posts/20170613.3.html)
    - **蓝图教程里都爱用。但目前我没有在调用模板时成功过，而且甚至程序没有报错也在登录页面的时候出现了问题，这很难受**
    - 另一方面，如果你的应用的组件之间的联系较为紧密，使用**功能式**架构会更好。如果Facebook是用Flask开发的，它将有一系列蓝图，用于静态页面(比如登出主页，注册页面，关于，等等)，面板(比如最新消息)，用户内容(/robert/about和/robert/photos)，还有设置页面(/settings/security和/settings/privacy)以及别的。这些组件都共享一个通用的布局和风格，但每一个都有它自己的布局。下面是一个非常精简的可能的Facebook结构，假定它用的是Flask。
- [功能式架构](https://spacewander.github.io/explore-flask-zh/7-blueprints.html)
-----------------
**似乎，对用户和战队进行类型定义的话还是得使用sqlalchemy。当然，可以通过映射来将已经定义好的结构直接映射过来，不幸中的万幸**
- [sqlalchemy,relationship，backref，里面也提到了filter操作](https://www.zhihu.com/question/38456789)
    - address引用外键来自user
    - relation可让user直接调用address
    - backref则让address可以直接调用user
    - 关系似乎只要有外键就可以？
- [alchemy 带定义类与方法的;to_dict](http://www.logevery.com/python/sqlalchemy_reflect_table_define.html)
- [用户管理01](https://www.cnblogs.com/franknihao/p/7414285.html)
- [用户管理02](https://blog.csdn.net/sunfengye/article/details/77400203)
- [orm无主键](https://docs.sqlalchemy.org/en/13/faq/ormconfiguration.html#how-do-i-map-a-table-that-has-no-primary-key)

- [session与事物管理；commit，remove，全局session；线程本地化；注意“scoped-session”实现对话安全](https://sunnyingit.github.io/book/section_python/SQLalchemy-session.html)
    - The ScopedSession object by default uses threading.local() as storage, so that a single Session is maintained for all who call upon the ScopedSession registry, but only within the scope of a single thread. Callers who call upon the registry in a different thread get a Session instance that is local to that other thread.Using this technique, the ScopedSession provides a quick and relatively simple way of providing a single, global object in an application that is safe to be called upon from multiple threads.
    - 注册模式，整个生命周期中只存在一个session；但却是伪注册，真本地化，为每一个session进行本地化
- [多线程sql-session](https://docs.python.org/3/library/threading.html#threading.local)

- [automap](https://docs.sqlalchemy.org/en/13/orm/extensions/automap.html)
    - **高可信度**




- [上下文,用户，flask的session，g01](https://jin-yang.github.io/post/flask-context.html)

- [上下文,用户，flask的session，g02](http://www.bjhee.com/jinja2-context.html)

- [flask session教学](https://blog.51cto.com/douya/2151255)
    - 特别注意！！！！！ flask的session和sqlalchemy的session是不同的 

- 导入app的时候一定不能加入__init__
- [蓝图教学](https://spacewander.github.io/explore-flask-zh/7-blueprints.html)
    - 蓝图试验成功，之前的错误实际上不是来自于蓝图，而是来自于蓝图+模板引擎+url_for的复杂关系。反正url_for应该不是一定需要放在模板引擎里的

- [功能式架构]()

- [蓝图动态路由](http://flask123.sinaapp.com/article/55/)
    - 注意大前提是点击一个url，根据后面的资源地址就会被视图函数分配到一个新的链接
    - 动态链接（带用户信息的）：点击链接-->截取url_slug-url片段-->由蓝图根据用户的标识动态引向各自profile主页--->此时利用装饰器定义的东西我们利用g来存储这个用户(在这之前或许要定义数据库Session注意不是flask-session)-->此时如果点击用户信息页面的其他页面，比如photo，那么利用g所保存的这个用户将会被使用，作为变量调用一些方法进入到html中
    
    - 我们可以在前缀中使用转换器(converters)，就像调用route()一样。同样也可以使用我们定义过的任意自定义转换器。通过这样做，我们可以自动处理在蓝图前缀中传递过来的值。在这个例子中，我们将根据URL片段获取用户类并传递到我们的profile蓝图中。我们将通过一个名为url_value_preprocessor()装饰器来做到这一点。
- [链接国际化](http://flask.pocoo.org/docs/patterns/urlprocessors/#internationalized-blueprint-urls)

- 某个路由的endpoint，即响应函数名。

- request.args 就是全部参数的字典;Next就是url传参啊，这个没啥可说的

- [有用用户1](https://www.cnblogs.com/franknihao/p/7414285.html)

- [有用用户2](https://blog.csdn.net/u010745324/article/details/53590188)

- [体育网](http://www.demodashi.com/demo/12380.html)
- 变化url的上传
- [websocket](https://www.cnblogs.com/franknihao/p/7550043.html)

-[有用的flask文章](https://www.cnblogs.com/franknihao/category/1059940.html)

- [邮箱](https://blog.csdn.net/u010745324/article/details/53590188)
- [flask_login教学](http://docs.jinkan.org/docs/flask-login/#flask.ext.login.make_secure_token)
    - 设置cookie
    - 可是我已经设置session了
- [外键](https://www.cnblogs.com/goldsunshine/p/9269880.html)
- 关于蓝图
    - 包蓝图----包
- [sqlalchemy标准查询删改语句](http://www.pythondoc.com/flask-sqlalchemy/queries.html)
- [金色阳光](https://www.cnblogs.com/goldsunshine/p/9269880.html)
- [多个提交按钮](https://www.cnblogs.com/xiaxiaoxu/p/10549554.html)
- [json序列化，反序列化](https://blog.csdn.net/u013205877/article/details/74895079)
- [json/jquery/flask/ajax](http://docs.jinkan.org/docs/flask/patterns/jquery.html)

- [验证码](https://zhuanlan.zhihu.com/p/26484539?utm_source=qq&utm_medium=social&utm_oi=1072201792204611584)

- [loader 不返回用户名就返回none]( https://www.jianshu.com/p/696155b1b7c6)
- [fresh login（重置密码）](http://www.bjhee.com/flask-ext8.html)

- 在视图中查询
    - 当您编写 Flask 视图函数，对于不存在的条目返回一个 404 错误是非常方便的。因为这是一个很常见的问题，Flask-SQLAlchemy 为了解决这个问题提供了一个帮助函数。可以使用 get_or_404() 来代替 get()，使用 first_or_404() 来代替 first()。这样会抛出一个 404 错误，而不是返回 None:
    - @app.route('/user/<username>')

- [sqlalchemy查询](https://my.oschina.net/jlan/blog/521854)
- [元组使用](https://www.runoob.com/python/python-tuples.html)
        - def show_user(username):
            - user = User.query.filter_by(username=username).first_or_404()
                - return render_template('show_user.html', user=user)

#### 个人考虑(逻辑部分)
1. 做题类似（就把练习部分当成比赛部分吧，大家没有那么多时间去打比赛，主要题也不多啊）
    - 进docker做题拿到flag
    - 在服务器提交比对数据库中的flag部分
    - 正确
        - 生成用户_题目关系表一条记录
            - 并对general用户表进行改变
            - 判断是否是前三次提交
            - 若是，则写入血关系表
        - 判断用户是否处于战队中
            
            - 若是，则在战队_题目关系表中添加记录
            - 并对general战队表进行改变
            - 并且如果是前三次则写入血关系表
      
       
        - 接着之前，在题目数据中做题次数+1，并对score进行改变（按照一定算法）

        - 对所有用户排名重新排序（可以使用异步刷新（这就是我们的新技术，会有分数加成）下同）
        - 对所有战队排名重新排序


2. 战队注销
    - 条件
      - 点击战队，只有队长有权限点注销（解散）按钮
      - 所有成员全退出
     
    - 删除战队所有记录
    - 删除该战队所有team_relation
    - 删除该战队所有team_blood

3. 用户加入战队
    - 将用户信息内的team赋值
    - 把用户所有relation改变之后加入到该战队的relation中
        - 冲突：目前似乎直接加入就可以，我还没想到
    
    - 战队页面的做题提交信息要增加
    
    - 对所有战队排名重新排序


4. 用户消息推送
    - 怎样就能知道用户有新消息了
    - 怎样就能把新消息推送给某个用户了（数据库存储消息状态以保证红色泡泡冒出来？）
        - 在普通用户界面新建消息状态，一旦有to表中某个用户属于响应方就在将其显示为1，并且在用户点开消息之后置0
    - 注意点击消息之后要跳入到正确的链接
        - 具体来说，点击了申请战队链接之后要跳到那个页面（或者这部分用弹窗处理也可以）

5. 申请加入战队/邀请加入战队：都是一方发出请求交给另一方并观察对方同不同意
    - 之后我会看看————不成熟的想法：新建一个用户_to_用户表，这样可以显示发起请求方与接受请求方，可以进行定位
    - 但这个数据本身没有存储的必要啊

6. 战队创建/队长权限
    - 大概数据库中用户的队长权限状态可以用一用
    - 谁创建战队，谁就是队长
    - 如果一个用户点击了创建战队，自动将他的status置适当值
    - （数据库p47，班长参照内部/这里可以改成队长参照内部？）
7. **普通用户权限/高级用户（用于鼓励做题）既然我们叫colosseo（甚至可以作为我们的创意点，就在引起用户竞争性上做文章）**

    - 做题数目高低，新建一个用户状态，如果做题超过一定数量就改变这个状态，同时改变用户界面的显示状态
    - 如果达到多少题授予一个资格
    - **增加用户等级功能，根据用户的得分情况等来判断---------------我觉得挺好玩的，但是属于优化部分**


8. 管理员权限
    - 便于程序员登录以管理
    - 管理员应该不能在user中了，看样子有可能新建一个额外数据库存储administrator的信息

9. 评论功能？write up的功能

    

# CTF平台开发收尾阶段：
## 关于在服务器上布置项目：
### 与服务器交互：
服务器IP：`49.233.168.44`
用户名：`ubuntu`
密码：`xqh000521QAQ?`
用`xshell`可连接与其进行交互

### 如何布置项目文件：
需要下载`Winscp`软件，连接方式与`xshell`相似，也是输入ip,用户名与密码.
连接上服务器以后，可将本地文件和服务器上的文件进行上传，删除，替换等。

### 如何在服务器上把项目跑起来：
项目部署方式为:`flask`+`gunicorn`+`supervisor`+`nginx`
    
**先进入虚拟环境，输入命令`workon flask_py3`，然后再进行后续操作**
    
自己测试时可在`~/web`目录下用命令`gunicorn -b 127.0.0.1:5000 runserver:app`跑起来。
    
想让多用户进行测试时，可在`~/web`目录下用`gunicorn -w 4(自己定，是并发的进程数，也是最多支持的并发请求数) -b 127.0.0.1:5000 runserver:app`跑起来项目。（需要注意的是：当用这种方式跑的时候，想停下来的时候一定要确认所有的进程都停了下来，你ctrl+c停下的只是你在的那个进程，可用`ps -ef | grep gun`来查看是否还有`gunicorn`的进程在跑）
    
当一切都布置好以后（现在还不需要），可以用`supervisor`来跑项目使项目不会因为意外而崩掉。
    
### 关于数据库:
服务器上的数据库可在本地用`workbench`进行管理
ip上面已经给了
username:`myctf`
password:`myctf`
database_name:`myctf`

当你把本地的项目传到服务器上时，不要忘了更改`database.py`文件
(其实完全可以本地也用服务器的数据库，反正都是用`workbench`来管理，而且还不用开虚拟机了。。。)

退出虚拟环境：`deactivate`
启动`supervisor`，可不在虚拟环境中启动:
`sudo supervisord -c /etc/supervisor/supervisor.conf `












