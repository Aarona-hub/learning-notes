## Express

### 1. 中间件

> http://www.expressjs.com.cn/resources/middleware.html

![点击查看源网页](https://ss0.bdstatic.com/94oJfD_bAAcT8t7mm9GUKT-xh_/timg?image&quality=100&size=b4000_4000&sec=1565941864&di=3808b80f0147f59a36048b8bd582bf2e&src=http://www.dfhxt.cn/uploads/img1/20160419/57158cfd5a244.png)

中间件的本质就是一个请求处理方法，我们把用户从请求到响应的整个过程分发到多个中间件中去处理，这就做的目的是提高代码的灵活性，动态可扩展的。

+ 同一个请求所经过的中间件都是同一个请求对象和响应对象

#### 1.1. 应用程序级别中间件

万能匹配(不关心任何请求路径和请求方法)：

```javascript
app.use(function(req,res,next){
    console.log('Time:',Date.now())
    next()
})
```

只要是以'/xxx/'开头的：

```javascript
app.use('/a',function(req,res,next){
     console.log('Time:',Date.now())
     next()
})
```

#### 1.2. 路由级别中间件

get：

```javascript
app.get('/',function(req,res){
    res.send('hello world')
})
```

post:

```javascript
app.post('/',function(req,res){
    res.send('Got a POST request')
})
```

put:

```javascript
app.put('/user',function(req,res){
    res.send('Got a PUT request at /user')
})
```

delete:

```javascript
app.delete('/user',function(req,res){
    res.send('Got a DELETE request at /user')
})
```

#### 1.3. 错误处理中间件

```javascript
app.use(function(err,req,res,next){
    console.error(err.stack)
    res.status(500).send('Something broke')
})
```

#### 1.4. 内置中间件

- [express.static](http://www.expressjs.com.cn/en/4x/api.html#express.static) serves static assets such as HTML files, images, and so on.
- [express.json](http://www.expressjs.com.cn/en/4x/api.html#express.json) parses incoming requests with JSON payloads. **NOTE: Available with Express 4.16.0+**
- [express.urlencoded](http://www.expressjs.com.cn/en/4x/api.html#express.urlencoded) parses incoming requests with URL-encoded payloads.  **NOTE: Available with Express 4.16.0+**

#### 1.5. 第三方中间件

> http://www.expressjs.com.cn/resources/middleware.html

+ [body-parser](http://www.expressjs.com.cn/en/resources/middleware/body-parser.html)
+ [compression](http://www.expressjs.com.cn/en/resources/middleware/compression.html)
+ [cookie-parser](http://www.expressjs.com.cn/en/resources/middleware/cookie-parser.html)
+ [morgan](http://www.expressjs.com.cn/en/resources/middleware/morgan.html)
+ [response-time](http://www.expressjs.com.cn/en/resources/middleware/response-time.html)
+ [serve-static](http://www.expressjs.com.cn/en/resources/middleware/serve-static.html)
+ [session](http://www.expressjs.com.cn/en/resources/middleware/session.html)
