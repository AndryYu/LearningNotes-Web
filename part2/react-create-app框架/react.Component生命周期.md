## React.Component 生命周期

#### Mounting(组件挂载)
* constructor()
 <br/>构造函数，在创建组件的时候调用一次。实现constructor(props)方法，在做其他声明之前，需要调用super(props)，否则this.props会出现未定义问题。
* componentWillMount()
* render()
* componentDidMount()

#### Updating(组件状态更新)
* componentWillReceiveProps()
* shouldComponentUpdate()
* componentWillUpdate()
* render()
* componentDidUpdate()


#### Unmounting(组件卸载)
* componentWillUnmount()


#### Error Handling(异常处理)
* componentDidCatch()

#### Other APIs
Each component also provides some other APIs:
* setState()
* forceUpdate()

#### Class Properties
* defaultProps
* displayName

#### Instance Properties
* props
* state

#### 参考文献
[React.Component](https://reactjs.org/docs/react-component.html)
