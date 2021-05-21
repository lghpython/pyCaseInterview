## python 面试题 - 高级能力

##### *1.阅读下列Django代码，在横线上填入（ ）后，代码的效率最高
```python
books = Book.objects.filter(..) 
_______
 	do_some_stuff()*
```

     A. if books:
     B. if books.exists():
     C. if len(books) > 0:
     D. if books.count() > 0:
     E. if len(Book.objects.filter(..)) > 0:

>  相关知识点： 如果想要知道总共有多少条数据，那么建议使用 count ，而不是使用 len(articles) 这种。因为 count 在底层是使用 select count(*) 来实现的，这种方式比使用 len 函数更加的高效；如果要判断某个条件的元素是否存在，那么建议使用 exists ，这比使用 count 或者直接判断 QuerySet 更有效得多。

#####  *2.以下选项中不是反爬虫措施的是（ A）*

     A. 通过分析用户请求的请求体信息进行反爬 虫。
     B. 通过判断同一个IP在短时间内是否频繁访问对应 网站等进行分析
     C. 通过使用用Firebug或者HttpFox对网络请求进行分析
     D. 通过动态页面增加爬取的难度，达到反爬虫的目的。

> 相关知识点： 应该是通过分析用户请求的请求头信息进行反爬虫。

##### *3.以下哪个Scrapy不能实现？（D）*

     A. 同时在不同的url上爬行
     B. 支持shell方式，方便独立调试
     C. 通过管道的方式存入数据库
     D. 支持分布式

> 相关知识点：scrapy基于python的爬虫框架，扩展性比较差，不支持分布式

##### *6.Redis产生缓存雪崩的原因是（ D）*

     A. key对应的数据在数据源并不存在，每次针对此key 的请求从缓存获取不到，请求都会到数据源，从而 可能压垮数据源。
     B. 由于缓存保存的是所有操作命令，导致存的缓存会 过大，而且数据库中有可能数据进行过删除，因此 缓存中的一些命令就相当于无效。
     C. key对应的数据存在，但在redis中过期，此时若有大 量并发请求过来，这些请求发现缓存过期一般都会 从后端DB加载数据并回设到缓存，这个时候大并发 的请求可能会瞬间把后端DB压垮。
     D. 当缓存服务器重启或者大量缓存集中在某一个时间段失效， 这样在失效的时候，也会给后端系统(比如DB)带来很大压力。

>  相关知识点： A选项是缓存穿透的原因，C选项是缓存击穿的原因，而B选项的说法本身就是错误的]

##### *7.在开发API给其他服务使用的场景下，Flask 的蓝图可以将大型应用分解，进行模块化开发，其实际用途不包括（B ）*

     A. 扩展请求的URL地址数量
     B. 增加服务调用的并发数量
     C. 注册蓝图以使用不同的URL规则
     D. 提供静态文件、模板和其他工具

> 相关知识点： Flask 中蓝图有以下用途：
> - 把一个应用分解为一套蓝图。 
> - 在一个应用的 URL 前缀和（或）子域上注册一个蓝图。 URL 前缀和（或）子域的 参数成为蓝图中所有视图的通用视图参数（缺省情况下）。 
> - 使用不同的 URL 规则在应用中多次注册蓝图。 
> - 通过蓝图提供模板过滤器、静态文件、模板和其他工具。蓝图不必执行应用或视图 函数。 
> - 当初始化一个 Flask 扩展时，为以上任意一种用途注册一个蓝图。

##### *8.WEB开发中，容易产生sql注入风险的是（ C）*

     A. 通过预编译方式执行sql语句
     B. 数据库账号降权
     C. 使用字符串拼接方式执行sql语句
     D. 全局过滤特殊符号

相关知识点： [拼接字符串易产生sql注入漏洞, 都需通过预编译方式带入查询。](javascript:;)

##### *9.在构建的Flask应用程序，使用SQLAlchemy中为解决 app上下文的问题：RuntimeError: working outside of request context时的解决方式不正确的是（ D）*

     A. db.init_app(app) db.create_all(app=app)
     B. db.init_app(app) with app.app_context(): db.create_all()
     C. db = SQLAlchemy(app=app)
     D. with app.app_context(): db.create_all(app=app)

>  相关知识点： SQLAlchemy模块不需要立即使用应用的初始化，在app上下文的处理时， 为解决working outside of request context问题，不能用D. with app.app_context(): db.create_all(app=app)的写法。

##### *10.web开发中，以下做法正确的是（ ）*

     A. 后端手机验证码验证通过后，跳转到设置新密码页面，https+post提交用户名、新密码，设置新密码完成密码重置功能
     B. 点击重置密码按钮，系统发送一条重置密码的链接到邮箱，格式为：http://www.xxx.com/password/reset?key=1563785498&username=045g6hgd4771h909uiwq5k001923r2p6（其中key是unix时间戳，username是用户名的md5值）
     C. 某网站的cookie生成方法为：固定字符串+用户名+时间戳的base64编码
     D. 以上都不对

相关知识点： [A选项，验证码校验和重置密码是不能分开两步提交的，容易绕过；B的问题主要是无法避免数据篡改，需要增加签名sign=f(param + secret)防止数据被篡改；其次md5加密的用户名并不知道是哪个用户，另外敏感数据应该用https；C项base64可逆，解密之后破解规则，可以伪造登录状，无法避免数据篡改]()