## 一、Redux三大原则
#### 单一数据源
整个应用的state被储存在一棵object tree中，并且这个object tree只存在于唯一一个store中。

#### state是只读的
唯一改变state的方法就是触发action,action是一个用于描述已发生事件的普通对象。

#### 使用纯函数来执行修改
为了描述action如何改变state tree，你需要编写reducers。

## 二、基础
#### Action
Action是把数据从应用（这里之所以不叫view是因为这些数据有可能是服务器响应，用户输入或者其他非view的数据）传到store的有效载荷。它是store数据的唯一来源。一般来说你会通过store.dispatch()将action传到store。


#### Reducers



#### Store


#### 数据流



## 三、高级
#### 异步Action


#### 异步数据流


#### Middleware


#### 搭配React Router

## 四、API文档
#### 1createStore(reducer, [initialState], enhancer)
创建一个Redux store来存放应用中所有的state，应用中应有且仅有一个store。<br/>

**参数**

1. reducer(Function):接收两个参数，分别是当前的state树和要处理的action,返回新的state树。
2. [initialState]:初始时的state。
3.


#### 2.Store


#### 3.combineReducers(reducers)
随着应用变得复杂，需要对reducer函数进行拆分，拆分后的每一块独立负责管理state的一部分。combineReducers辅助函数的作用是，把一个由多个不同reducer函数作为value的object,合并成一个最终的reducer函数，然后就可以对这个reducer调用createStore。合并后的reducer可以调用各个子reducer,并把它们的结果合并成一个state对象。state对象的结构由传入的多个reducer的key决定。
<p>通过为传入对象的reducer命名不同来控制state key的命名。例如，你可以调用combineReducers({todos:myTodosReducer, counter:myCounterReducer})将state结构变为{todos,counter}。通常的做法是命名reducer,然后state再去分割那些信息，因此你可以使用ES6的简写方法：combineReducers({counter,todos})。这与combineReducers({counter:counter, todos:todos})



#### 4.applyMiddleware



#### 5.bindActionCreators(actionCreators, dispatch)
把action creators转化拥有同名keys的对象，但使用dispatch把每个aciton creator 包围起来，这样可以直接调用它们。一般情况下，你可以直接在Store实例上调用dispatch。如果你在React中使用Redux,react-redux会提供dispatch。唯一使用bindActionCreators的场景是当你需要把aciton creatore往下传到一个组件上，却不想让这个组件觉察到Redux的存在，而且不希望把Redux store或dispatch传给它。
**参数**
1. actionCreators(Function or Object):一个action creator,或者键值是action creators的对象。
2. dispatch(Function):一个dispatch函数，由Store实例提供。
**返回值**
(Function or Object):一个与原对象类似的对象，只不过这个对象中的每个函数值都可以直接dispatch action。如果传入的是一个函数，反悔的也是一个函数。



#### 6.compose

#### 7.<Provider store>
<Provider store>使组件层级中的connect()方法都能够获得Redux store。正常情况下，你的根组件应该嵌套在<Provider>中才能使用connect()方法。
