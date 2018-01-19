关于redux-form的三个主要模块
* formReducer reducer:表单的各种操作以Redux action的方式，通过此reducer来促使Redux store数据的变化。
* reduxForm() HOC:此高阶组件用以整合Redux action绑定的用户交互与您的组件，并返回一个新的组件供以使用。
* ```<Field/>```:用此代替您原本的```<input/>```组件，可以与redux-form的逻辑相连接。

## 基本使用
##### 1. formReducer

<p>store需要知道组件如何发送action，因此我们需要在你的store中注册```formReducer```，它可以服务于整个app中你定义的所有表单组件，因此只需要注册一次。</p>

```
import { createStore, combineReducers } from 'redux'
import { reducer as formReducer } from 'redux-form'

const rootReducer = combineReducers({
  // ...your other reducers here
  // you have to pass formReducer under 'form' key,
  // for custom keys look up the docs for 'getFormState'
  form: formReducer
})

const store = createStore(rootReducer)
```
注：在reducer中合并的formReducer的key必须命名为‘form’。

##### 2. form component

为了使你的表单可以与store进行交互，我们需要使用高阶函数```reduxForm()```来包裹你的组件。它可以在你执行提交表单等操作时，以props的方式提供表单内的state。

```
import React from 'react'
import { Field, reduxForm } from 'redux-form'

let ContactForm = props => {
  const { handleSubmit } = props
  return (
    <form onSubmit={ handleSubmit }>
      { /* form body*/ }
    </form>
  )
}

ContactForm = reduxForm({
  // a unique name for the form
  form: 'contact'
})(ContactForm)

export default ContactForm;
```
现在我们已经有一个表单组件了，接下来添加一些input组件。

##### 3. form ```<Field/>``` Components


```<Field/>``` 组件可以连接所有input类型组件的数据到store中，基本用法如下：

```
<Field name="inputName" component="input" type="text"/>
```
它创建了一个text类型的```<input/>```组件,还提供了诸如value、onChange、onBlur等属性，用于跟踪和维护此组件的各种状态。

##### 4. Reacting to submit
提交的数据以JSON对象的形式注入了此表单组件的onSubmit方法里了
```
import React from 'react'
import ContactForm from './ContactForm'

class ContactPage extends React.Component {
  submit = (values) => {
    // print the form values to the console
    console.log(values)
  }
  render() {
    return (
      <ContactForm onSubmit={this.submit} />
    )
  }
}
```
ContactForm组件代码如下：
```
import React from 'react'
import { Field, reduxForm } from 'redux-form'

const ContactForm = props => {
  const { handleSubmit } = props
  return (
    <form onSubmit={ handleSubmit }>
      <div>
        <label htmlFor="firstName">First Name</label>
        <Field name="firstName" component="input" type="text" />
      </div>
      <div>
        <label htmlFor="lastName">Last Name</label>
        <Field name="lastName" component="input" type="text" />
      </div>
      <div>
        <label htmlFor="email">Email</label>
        <Field name="email" component="input" type="email" />
      </div>
      <button type="submit">Submit</button>
    </form>
  )
}

ContactForm = reduxForm({
  // a unique name for the form
  form: 'contact'
})(ContactForm)

export default ContactForm;
```
