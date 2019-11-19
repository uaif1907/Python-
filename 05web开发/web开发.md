#### 1. 简述同源策略
```
同源策略需要同时满足以下三点要求：
1）协议相同
2）域名相同
3）端口相同
 http:www.test.com与https:www.test.com 不同源——协议不同
 http:www.test.com与http:www.admin.com 不同源——域名不同
 http:www.test.com与http:www.test.com:8081 不同源——端口不同
 只要不满足其中任意一个要求，就不符合同源策略，就会出现“跨域”
```
#### 2. 简述cookie和session的区别
```
1，session 在服务器端，cookie 在客户端（浏览器）
2、session 的运行依赖 session id，而 session id 是存在 cookie 中的，也就是说，如果浏览器禁用了 cookie ，同时 session 也会失效，存储Session时，键与Cookie中的sessionid相同，值是开发人员设置的键值对信息，进行了base64编码，过期时间由开发人员设置
3、cookie安全性比session差
```
#### 3.请说出三种减低页面加载时间的方法
```
压缩css、js文件
合并js、css文件，减少http请求
外部js、css文件放在最底下
减少dom操作，尽可能用变量替代不必要的dom操作
```
#### 4.浏览器是如何渲染页面的？
```
1.解析HTML文件，创建DOM树
自上而下，遇到任何样式（link、style）与脚本（script）都会阻塞（外部样式不阻塞后续外部脚本的加载）。
2.解析CSS
优先级：浏览器默认设置<用户设置<外部样式<内联样式<HTML中的style样式。
3.将CSS与DOM合并
构建渲染树（Render Tree）。
4.布局和绘制
重绘（repaint）和重排（reflow）。
```
#### 5.cookie 、sessionStorage、localStorage的区别
```
1.cookie数据始终在同源的http请求中携带（即使不需要），在服务器和浏览器之间来回传递。大小限制：4K
2.sessionStorage：不会把数据发送到服务器，仅保存到本地，大小不同浏览器有不同限制，大概在5M左右。数据有效期不同，只在当前会话内有效。不在不通的浏览器内共享。
3.localStroage：在所有同源窗口中都会是共享的。大小同5M左右。可以持久保存。
```
#### 6.什么是W3C，它为什么很重要？
```
W3C 的意思是 World Wide Consortium，它是一个专注于开发和标准化 Web 的国际社区。作为Web开发人员，强制执行这些标准可确保所有浏览器都能访问Web内容，并优化用户体验。例如：使用符合 W3C 标准的 CSS 和 XML 可以使每个网站的功能相似，也可以改善搜索引擎优化。
```
#### 7.Http与Https的区别：
```
HTTP 的URL 以http:// 开头，而HTTPS 的URL 以https:// 开头
HTTP 是不安全的，而 HTTPS 是安全的
HTTP 标准端口是80 ，而 HTTPS 的标准端口是443
在OSI 网络模型中，HTTP工作于应用层，而HTTPS 的安全传输机制工作在传输层
HTTP 无法加密，而HTTPS 对传输的数据进行加密
HTTP无需证书，而HTTPS 需要CA机构wosign的颁发的SSL证书
```
#### 8.什么是Http协议无状态协议?怎么解决Http协议无状态协议?
```
无状态协议对于事务处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息
也就是说，当客户端一次HTTP请求完成以后，客户端再发送一次HTTP请求，HTTP并不知道当前客户端是一个”老用户“。
可以使用Cookie来解决无状态的问题，Cookie就相当于一个通行证，第一次访问的时候给客户端发送一个Cookie，当客户端再次来的时候，拿着Cookie(通行证)，那么服务器就知道这个是”老用户“。
```
#### 9.常用的HTTP方法有哪些？
```
GET： 用于请求访问已经被URI（统一资源标识符）识别的资源，可以通过URL传参给服务器
POST：用于传输信息给服务器，主要功能与GET方法类似，但一般推荐使用POST方式。
PUT： 传输文件，报文主体中包含文件内容，保存到对应URI位置。
HEAD： 获得报文首部，与GET方法类似，只是不返回报文主体，一般用于验证URI是否有效。
DELETE：删除文件，与PUT方法相反，删除对应URI位置的文件。
OPTIONS：查询相应URI支持的HTTP方法。
```
#### 10.HTTPS工作原理
```
一、首先HTTP请求服务端生成证书，客户端对证书的有效期、合法性、域名是否与请求的域名一致、证书的公钥（RSA加密）等进行校验；
二、客户端如果校验通过后，就根据证书的公钥的有效， 生成随机数，随机数使用公钥进行加密（RSA加密）；
三、消息体产生的后，对它的摘要进行MD5（或者SHA1）算法加密，此时就得到了RSA签名；
四、发送给服务端，此时只有服务端（RSA私钥）能解密。
五、解密得到的随机数，再用AES加密，作为密钥（此时的密钥只有客户端和服务端知道）。
客户端发起HTTPS请求->服务端的配置->传送证书->客户端解析证书->传送加密信息->服务段解密信息->传输加密后的信息->客户端解密信息
```
#### 11.常见的HTTP相应状态码
```
200：请求被正常处理
204：请求被受理但没有资源可以返回
206：客户端只是请求资源的一部分，服务器只对请求的部分资源执行GET方法，相应报文中通过Content-Range指定范围的资源。
301：永久性重定向
302：临时重定向
303：与302状态码有相似功能，只是它希望客户端在请求一个URI的时候，能通过GET方法重定向到另一个URI上
304：发送附带条件的请求时，条件不满足时返回，与重定向无关
307：临时重定向，与302类似，只是强制要求使用POST方法
400：请求报文语法有误，服务器无法识别
401：请求需要认证
403：请求的对应资源禁止被访问
404：服务器无法找到对应资源
500：服务器内部错误
503：服务器正忙
```
#### 12.HTTP优化方案
```
TCP复用：TCP连接复用是将多个客户端的HTTP请求复用到一个服务器端TCP连接上，而HTTP复用则是一个客户端的多个HTTP请求通过一个TCP连接进行处理。前者是负载均衡设备的独特功能；而后者是HTTP 1.1协议所支持的新功能，目前被大多数浏览器所支持。
内容缓存：将经常用到的内容进行缓存起来，那么客户端就可以直接在内存中获取相应的数据了。
压缩：将文本数据进行压缩，减少带宽
SSL加速（SSL Acceleration）：使用SSL协议对HTTP协议进行加密，在通道内加密并加速
TCP缓冲：通过采用TCP缓冲技术，可以提高服务器端响应时间和处理效率，减少由于通信链路问题给服务器造成的连接负担。
```
#### 13.GET和POST的区别：
```
简单来说：GET产生一个TCP数据包，POST产生两个TCP数据包
严格的说：对于GET方式的请求，游览器会把http header和data一并发送出去，服务器响应200（返回数据）；
而对于POST请求。游览器先发送header，服务器响应100 continue，游览器再发送data，服务器响应200 ok（返回数据）
```
#### 14.HTTP请求报文与响应报文格式
```
请求报文包含三部分：
a、请求行：包含请求方法、URI、HTTP版本信息
b、请求头部（headers）字段
c、请求内容实体(body)
响应报文包含三部分：
a、状态行：包含HTTP版本、状态码、状态码的原因短语
b、响应头部（headers）字段
c、响应内容(body)实体
```
#### 15.一次完整的HTTP请求所经历的7个步骤
```
建立TCP连接
Web浏览器向Web服务器发送请求行
Web浏览器发送请求头
Web服务器应答
Web服务器发送应答头
Web服务器向浏览器发送数据
Web服务器关闭TCP连接
```
#### 16.什么是HTTP协议无状态协议？怎么解决http协议无状态协议？
```
无状态协议对于事物处理没有记忆能力。缺少状态意味着后续的处理需要前面的信息。
无状态协议的解决办法：通过1）Cookie ; 2)通过session会话保存。
```
#### 17.为什么HTTPS安全
```
因为网络请求需要中间有很多的服务器路由器的转发。中间的节点都可能篡改信息，而如果使用HTTPS，密钥在你和终点站才有。https之所以比http安全，是因为他利用ssl/tls协议传输。它包含证书，卸载，流量转发，负载均衡，页面适配，浏览器适配，refer传递等。保障了传输过程的安全性
```
#### 18.关于Http 2.0 你知道多少？
```
HTTP/2引入了“服务端推（server push）”的概念，它允许服务端在客户端需要数据之前就主动地将数据发送到客户端缓存中，从而提高性能。
HTTP/2提供更多的加密支持
HTTP/2使用多路技术，允许多个消息在一个连接上同时交差。
它增加了头压缩（header compression），因此即使非常小的请求，其请求和响应的header都只会占用很小比例的带宽
```
#### 19.在浏览器键入URL，按下回车之后的流程是什么？
```
（1）、DNS解析：浏览器会根据URL逐层查询DNS服务器缓存，解析出URL中的域名所对应的IP地址。DNS缓存分别有浏览器缓存，系统缓存，路由器缓存，IPS服务器缓存，根域名服务器缓存，顶级域名服务器缓存。从上面的哪一级缓存查询到后直接返回IP地址，不再查询。
（2）、TCP连接：在得到服务器的IP地址之后，就会尝试和服务器建立连接（具体内容可以看之前的博文）
（3）、发送HTTP请求：在浏览器和服务器之间建立好连接之后，浏览器就会发送HTTP请求报文
（4）、服务器处理请求并返回HTTP报文：服务器返回给浏览器带有HTML的响应报文
（5）、浏览器解析渲染页面
（6）、浏览器释放连接，即TCP四次挥手。
```
#### 20.什么是跨域
```
协议、端口和域名不一致成为跨域
跨域是因为浏览器需要遵守同源策略，发出的请求即使相应成功，也会被浏览器拦截下来
解决方案：
1、通过jsonp跨域
2、document.domain + iframe跨域
3、 location.hash + iframe
4、window.name + iframe跨域
5、postMessage跨域
6、跨域资源共享（CORS）
7、nginx代理跨域
8、nodejs中间件代理跨域
9、WebSocket协议跨域
```
#### 21.什么是Flask,有什么优点？
```
Flask是一个Web框架,就是提供一个工具,库和技术来允许你构建一个Web应用程序.这个Web应用程序可以是一些Web页面,博客,wiki,基于Web的日里应用或商业网站.
　优点:
　　Flask属于微框架（micro-framework)这一类别,微架构通常是很小的不依赖外部库的框架.
　　- 框架很轻量
　　- 更新时依赖小
　　- 专注于安全方面的bug
Flask的依赖:
　　Werkzeug 一个WSGI工具包（web服务网关接口（Python Web Server Gateway Interface,缩写为WSGI）是为python语言定义的web服务器和web应用程序或框架之间的一种简单而通用的借口,其他语言也有类似的接口）
　　jinja2模板引擎
```
#### 22.Flask-WTF是什么,有什么特点？
```
Flask-wtf是一个用于表单处理,校验并提供csrf验证的功能的扩展库
Flask-wtf能把正表单免受CSRF<跨站请求伪造>的攻击
```
#### 23.Flask脚本的常用方式是什么?
```
在shell中运行脚本文件
在python编译器中run
```
#### 24.如何在Flask中访问会话?
```
会话（seesion）会话数据存储在服务器上.会话是客户端登录到服务器并注销的时间间隔.需要在此会话中进行的数据存储在服务器上的临时目录中.
from flask import session 导入会话对象
session['name'] = 'admin' 给会话添加变量
session.pop('username', None) 删除会话的变量
```
#### 25.解释Python Flask中的数据库连接?
```
python中的数据库连接有两种方式:
在脚本中以用第三方库正常连接,用sql语句正常操作数据库,如mysql关系型数据库的pymsql库
用ORM来进行数据库连接,flask中典型的flask_sqlalchemy,已面向对象的方式进行数据库的连接与操作
```
#### 26.Flask框架依赖组件?
```
Route(路由)
templates(模板)
Models(orm模型)
blueprint(蓝图)
Jinja2模板引擎
```
#### 27.Flask蓝图的作用?
```
蓝图Blueprint实现模块化的应用
- book_bp = Blueprint('book', __name__）创建蓝图对象
- 蓝图中使用路由@book_bp.route('url')
- 在另一.py文件里导入和注册蓝图from book import book_bp app.register_blueprint(book_bp)
作用:
　　将不同的功能模块化
　　构建大型应用
　　优化项目结构
　　增强可读性,易于维护（跟Django的view功能相似）
```
#### 28.列举使用过的Flask第三方组件?
```
flask_bootstrap
flask-WTF
flask_sqlalchemy
```
#### 29.简述Flask上下文管理流程?
```
每次有请求过来的时候,flask会先创建当前线程或者进程需要处理的两个重要上下文对象,把它们保存到隔离的栈里面,这样视图函数进行处理的时候就能直接从栈上获取这些信息.
```
#### 30.Flask中多app应用是怎么完成?
```
请求进来时,可以根据URL的不同,交给不同的APP处理
```
#### 31.wtforms组件的作用?
```
WTForms是一个支持多个web框架的form组件,主要用于对用户请求数据进行验证.
```
#### 32.Flask框架默认session处理机制?
```
Flask的默认session利用了Werkzeug的SecureCookie,把信息做序列化(pickle)后编码(base64),放到cookie里了.
过期时间是通过cookie的过期时间实现的.
为了防止cookie内容被篡改,session会自动打上一个叫session的hash串,这个串是经过session内容、SECRET_KEY计算出来的,看得出,这种设计虽然不能保证session里的内容不泄露,但至少防止了不被篡改.
```
#### 33.ORM的实现原理?
```
概念: 对象关系映射（Object Relational Mapping,简称ORM,或O/RM,或O/R mapping）,是一种程序技术,用于实现面向对象编程语言里不同类型系统的数据之间的转换.
详细介绍:
让我们从O/R开始.字母O起源于"对象"(Object),而R则来自于"关系"(Relational).几乎所有的程序里面,都存在对象和关系数据库.在业务逻辑层和用户界面层中,我们是面向对象的.当对象信息发生变化的时候,我们需要把对象的信息保存在关系数据库中.
当你开发一个应用程序的时候(不使用O/R Mapping),你可能会写不少数据访问层的代码,用来从数据库保存,删除,读取对象信息,等等.你在DAL中写了很多的方法来读取对象数据,改变状态对象等等任务.而这些代码写起来总是重复的.
ORM解决的主要问题是对象关系的映射.域模型和关系模型分别是建立在概念模型的基础上的.域模型是面向对象的,而关系模型是面向关系的.一般情况下,一个持久化类和一个表对应,类的每个实例对应表中的一条记录,类的每个属性对应表的每个字段.
　　ORM技术特点：
　　1.提高了开发效率.由于ORM可以自动对Entity对象与数据库中的Table进行字段与属性的映射,所以我们实际可能已经不需要一个专用的、庞大的数据访问层.
　　2.ORM提供了对数据库的映射,不用sql直接编码,能够像操作对象一样从数据库获取数据.
```
#### 34.什么是wsgi?
```
WSGI（Web Server Gateway Interface，Web 服务器网关接口）则是Python语言中1所定义的Web服务器和Web应用程序之间或框架之间的通用接口标准。
WSGI就是一座桥梁，桥梁的一端称为服务端或网关端，另一端称为应用端或者框架端，WSGI的作用就是在协议之间进行转化。WSGI将Web组件分成了三类：Web 服务器（WSGI Server）、Web中间件（WSGI Middleware）与Web应用程序（WSGI Application）。
Web Server接收HTTP请求，封装一系列环境变量，按照WSGI接口标准调用注册的WSGI Application，最后将响应返回给客户端。
```
#### 35.Django和Flask有什么区别?
```
Flask
Flask确实很“轻”，不愧是Micro Framework，从Django转向Flask的开发者一定会如此感慨，除非二者均为深入使用过
Flask自由、灵活，可扩展性强，第三方库的选择面广，开发时可以结合自己最喜欢用的轮子，也能结合最流行最强大的Python库
入门简单，即便没有多少web开发经验，也能很快做出网站
非常适用于小型网站
非常适用于开发web服务的API
开发大型网站无压力，但代码架构需要自己设计，开发成本取决于开发者的能力
各方面性能均等于或优于Django
Django自带的或第三方的好评如潮的功能，Flask上总会找到与之类似第三方
Flask灵活开发，Python高手基本都会喜欢Flask，但对Django却可能褒贬不
Flask与关系型数据库的配合使用不弱于Django，而其与NoSQL数据库的配合远远优于Django
Flask比Django更加Pythonic，与Python的philosophy更加吻合
Django
Django太重了，除了web框架，自带ORM和模板引擎，灵活和自由度不够高
Django能开发小应用，但总会有“杀鸡焉用牛刀”的感觉
Django的自带ORM非常优秀，综合评价略高于SQLAlchemy
Django自带的模板引擎简单好用，但其强大程度和综合评价略低于Jinja2
Django自带ORM也使Django与关系型数据库耦合度过高，如果想使用MongoDB等NoSQL数据，需要选取合适的第三方库，且总感觉Django+SQL才是天生一对的搭配，Django+NoSQL砍掉了Django的半壁江山
Django目前支持Jinja等非官方模板引擎
Django自带的数据库管理app好评如潮
Django非常适合企业级网站的开发：快速、靠谱、稳定
Django成熟、稳定、完善，但相比于Flask，Django的整体生态相对封闭
Django是Python web框架的先驱，用户多，第三方库最丰富，最好的Python库，如果不能直接用到Django中，也一定能找到与之对应的移植
Django上手也比较容易，开发文档详细、完善，相关资料丰富
```
#### 36.Flask中上下文管理主要涉及到了那些相关的类？并描述类主要作用？
```
RequestContext  #封装进来的请求（赋值给ctx）
AppContext      #封装app_ctx
LocalStack      #将local对象中的数据维护成一个栈（先进后出）
Local           #保存请求上下文对象和app上下文对象
```
#### 37.为什么要Flask把Local对象中的的值stack 维护成一个列表
```
# 因为通过维护成列表，可以实现一个栈的数据结构，进栈出栈时只取一个数据，巧妙的简化了问题。
# 还有，在多app应用时，可以实现数据隔离；列表里不会加数据，而是会生成一个新的列表
# local是一个字典，字典里key（stack）是唯一标识，value是一个列表

```
#### 38.SQLAlchemy如何执行原生SQL？
```
# 使用execute方法直接操作SQL语句(导入create_engin、sessionmaker)
engine=create_engine('mysql://root:*****@127.0.0.1/database?charset=utf8')
DB_Session = sessionmaker(bind=engine)
session = DB_Session()
session.execute('alter table mytablename drop column mycolumn ;')
```
#### 39.SQLAchemy中如何为表设置引擎和字符编码？
```
sqlalchemy设置编码字符集，一定要在数据库访问的URL上增加'charset=utf8'
否则数据库的连接就不是'utf8'的编码格式

eng=create_engine('mysql://root:root@localhost:3306/test2?charset=utf8',echo=True)
1. 设置引擎编码方式为utf8。
    engine = create_engine("mysql+pymysql://root:123456@127.0.0.1:3306/sqldb01?charset=utf8")
2. 设置数据库表编码方式为utf8
class UserType(Base):
    __tablename__ = 'usertype'
    id = Column(Integer, primary_key=True)
    caption = Column(String(50), default='管理员')
    # 添加配置设置编码
    __table_args__ = {
        'mysql_charset':'utf8'
    }
这样生成的SQL语句就自动设置数据表编码为utf8了,__table_args__还可设置存储引擎、外键约束等等信息。
```
#### 40.SQLAchemy中如何设置联合唯一索引？
```
通过'UniqueConstraint'字段来设置联合唯一索引
__table_args=(UniqueConstraint('h_id','username',name='_h_username_uc'))
#h_id和username组成联合唯一约束
```
#### CSRF攻击
https://www.jianshu.com/p/67408d73c66d
#### SQL注入
https://www.jianshu.com/p/5c67414bfcb6
