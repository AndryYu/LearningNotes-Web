## 区别
React.js和React Native的原理是相同的，都是由js实现的虚拟dom来驱动界面View层渲染。只不过React.js是驱动html dom渲染;React Native是驱动android/ios原生组件渲染。

## 虚拟DOM(Virtual DOM)的机制
在浏览器端用Javascript实现了一套DOM API。基于React进行开发时所有的DOM构建都是通过虚拟DOM进行，每当数据变化时，React都会重新构建整个DOM树，然后React将当前整个DOM树和上一次的DOM树进行对比，得到DOM结构的区别，然后仅仅将需要变化的部分进行实际的浏览器DOM更新。而且React能够批处理虚拟DOM的刷新，在一个事件循环（Event Loop）内的两次数据变化会被合并。
