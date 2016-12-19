请求servlet/jsp时，服务器发送数据到浏览器前，jsp脚本已经被web服务器解析完毕，是一个字符串了。

    Application/Session/Request域对象都是在服务器端的内存中的，Servlet/JSP容器解析jsp的动态数据是从内存中获取，解析后的纯字符串发送到浏览器（即Javascript和html代码），也就是在浏览器中右键点击看到的源代码了。浏览器只会解析javascript和渲染html。

    因此通过Ajax请求+嵌套jsp脚本在当前的js中，而不刷新整个页面是行不通的。 这也是出现要刷新一次才能会显示数据成功的原因。

    要实现原来的功能，可以在servlet中out.prinln中增加那些你想要在html显示的数据。字符串格式可以是xml，也可以是json，或者自定义规则的字符串。然后ajax接收到数据后，通过js的函数截取其中有用的数据，再利用js改变浏览器中所渲染的html的内容。
