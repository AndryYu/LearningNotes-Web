## React Router
1. 基本路由跳转
2. 嵌套路由
3. 带路径参数的嵌套路由
4. 保护式路由

#### 一、基本路由跳转
** Router**

React Router API中使用两种类型的路由：
*  ```<BrowserRouter>```
*  ```<HashRouter>```

他们之间的区别在于它们所创建的URL
```
// <BrowserRouter>
 http://example.com/about
//<HashRouter>
 http://example.com/#/about
```

** history**

history对象有history.push()和history.replace()这些方法来实现。当你点击<Link>组件会触发history.push(),使用<Redirect>则会调用history.replace()。其他方法-例如history.goBack()和history.goForward()-用来根据页面的后退和前进来跳转history堆栈。

** Links and Routers**

<p>```<router>```是React Router里最重要的组件。若当前路径匹配route的路径，它会渲染对应的UI。理想来说，```<Route>```应该有一个叫path的prop,当路径名跟当前路径匹配才会渲染。</p>

<p>另一方面，```<Link>```用来跳转页面。可以类比HTML的锚元素。然而，使用锚链接会导致浏览器的刷新，这不是我们想要的。所以，我们可以使用```<Link>```来跳转至具体的URL，并且视图重新渲染不会导致浏览器刷新。
