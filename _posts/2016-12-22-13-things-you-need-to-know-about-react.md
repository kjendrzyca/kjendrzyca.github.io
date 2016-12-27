---
layout: post
title: 13 things you need to know about React
categories: []
tags: [javascript, react, concepts]
published: true
date: 2016-12-22
comments: true
---

![React](/img/react.jpg)
*Image by [Franco Folini](https://www.flickr.com/photos/livenature/)*

I've been using React for over a year now. I'm also conducting training to help people learn it from scratch.
I noticed that on every training session I'm explaining the same set of concepts over and over.
I think those concepts are essential if you want to "speak React". If you are in a middle of learning it right know, you might be interested in reading this post.

<span class="more">--</span>

## 1) It's not a framework

Angular or Ember are frameworks where some decisions are already made for you. React is just a library and you need to make all decisions by yourself. It focuses on helping you to build user interfaces using components.

It doesn't help you with server communication, translations, routing and so on. Some perceive this as a weakness. I agree with one wise man that once said:

> "Framework solves the problem of its creators" ~one of my mentors

React is thin and it's extremely easy to mix it with other 3rd party libraries. Rich JS ecosystem has a library for everything. You can choose your favorite one and plug it in without dealing with the design decisions/limitations of the framework.

Of course, there is [famous JS fatigue](https://medium.com/@ericclemmons/javascript-fatigue-48d4011b6fc4#.ovtpj2ypn). If you feel the same way and don't want to make every decision yourself, do a 30 min research, pick one of the [opinionated starter kits/boilerplates](http://andrewhfarmer.com/starter-project/), change whatever you want and just use it.

## 2) JSX

When looking at React examples you've probably seen [JSX](https://facebook.github.io/react/docs/introducing-jsx.html) in action already. But React code can be written in plain JS too:

```javascript
const rootElement =
  React.createElement('div', {},
    React.createElement('h1', {style: {color: 'red'}}, 'The world is yours'),
    React.createElement('p', {}, 'Say hello to my little friend')
  )

ReactDOM.render(rootElement, document.getElementById('app'))
```

Some people don't fancy writing entire markup code as function calls. That's probably why people at Facebook came up with JSX - a "syntactic sugar for the React.createElement(component, props, ...children) function".

That's why we can refactor the above example to this:

```html
const RootElement = (
  <div>
    <h1 style={{color: red}}>The world is yours</h1>
    <p>Say hello to my little friend</p>
  </div>
)

ReactDOM.render(RootElement, document.getElementById('app'))
```

During the build process [Babel](https://babeljs.io/docs/plugins/preset-react/) will transpile the markup to plain JS.

## 3) It's JavaScript

To generate markup dynamically in React you also use JS:

```html
<select value={this.state.value} onChange={this.handleChange}>
  {somearray.map(element => <option value={element.value}>{element.text}</option>)}
</select>
```

In the above example, the `somearray` array is mapped using `map` function to a list of `<option>` elements. The only deviation from normal HTML here is a `value` on `<select>` element that sets the `selected` attribute for you.

It's not required to use it though:

```html
<select onChange={this.handleChange}>
  {somearray.map(element => (
      <option
        value={element.value}
        selected={this.state.value === element.value}
      >
        {element.text}
      </option>
    ))}
</select>
```

Many popular frameworks use templating languages for operations like the one above. Every framework comes with its own. So every time you want to use a framework you need to learn a new templating language, its quirks and drawbacks.

> The code above renders with a warning about missing *key* property.
> To know why and how to solve that visit [this page](https://facebook.github.io/react/docs/lists-and-keys.html) or just read the error message in your dev tools ;).

I remember my first time using a `<select>` control in Angular 1. There is a special `ngOptions` directive that will generate all possible `<options>` for you.

```html
<select
  ng-model="selectedItem"
  ng-options="item as item.name for item in items">
</select>
```

To this day I don't know what `item as item.name for item` means.

There are smarter people than me, who memorized how to use all kinds of templating languages. I often switch from backend to frontend development. There are long periods when I'm not doing frontend at all. And the knowledge fades if you don't use it. That's why memorization doesn't work for me. I'm familiar with `map()` function and HTML though, so the React way is very appealing to me.

Another bonus is that static code analysis is free. It's definitely easier to [lint](https://github.com/yannickcr/eslint-plugin-react) JS than custom templating markup.

For me templating is String Driven Development. There is no serious linting. Just some magic in HTML which is not checked in any way. JSX adds more stuff to JS to make it more powerful. That's also the reason I don't agree when people call JSX a templating language.

## 4) It's declarative

In React you use declarative style to write your components. Let's look at the previous example with `<select>`:

```html
<select value={this.state.value} onChange={this.handleChange}>
  {somearray.map(element => <option value={element.value}>{element.text}</option>)}
</select>
```

In this `<select>` example you are not using `for` loop to manually create a mapped collection. You are not saying *what should be done* just *how it should look like*.

## 5) You separate the concerns

In React you keep HTML, JS and often CSS together as a component. If you want to display a row on the grid you create a `Row` component and put HTML, logic and behavior in one file.

For many years we split JS, HTML, and CSS into different files. [Pete Hunt called that a separation of technologies](https://www.youtube.com/watch?v=x7cQ3mrcKaY). It shouldn't be confused with separation of concerns.

I often get questions if I consider this "lack of separation" strange. But what's strange for me are the examples people often give to defend the strategy of keeping HTML and JS separate:

"If you keep HTML and JS in separate files you can easily replace the HTML and keep the JS intact".

It doesn't work that way if you think about it. Most changes to the HTML structure require refactoring of JS logic.

> "Display logic and markup are inevitably tightly coupled" ~Pete Hunt

If you change the text input to checkbox you need to rewrite your logic. No going away from that.

## 6) Data goes down

In React data goes down the tree of the components. If you want to pass data from parent to child component you need to use [**props**](https://facebook.github.io/react-native/docs/props.html). From JSX point of view props are HTML attributes.

Parent component:

```html
<div>
  <Greetings color={red} text='Hello' />
</div>
```

In the child component, props are available under `this.props`.

Child component:

```javascript
const Greetings = React.createClass({
  render () {
    const {color, text} = this.props
    const divStyle = {padding: 10, backgroundColor: 'black'}
    const headingStyle = {color: color}

    return (
      <div style={divStyle}>
        <h1 style={headingStyle}>{text}</h1>
      </div>
    )
  }
})
```

## 7) State

Until now, we discussed only static components with static data passed down the components tree. Often, it's needed to create a [**stateful component**](https://facebook.github.io/react/docs/state-and-lifecycle.html) where the state is changing over time.

Let's consider an `<input>` where you can type in a text that will be displayed below.

```javascript
const InputBox = React.createClass({
  getInitialState () {
    return {
      text: ''
    }
  },

  changeText (event) {
    this.setState({text: event.target.value})
  },

  render () {
    return (
      <div>
        <input type='text' onChange={this.changeText} placeholder='text' value={this.state.text} />
        <span>{this.state.text}</span>
      </div>
    )
  }
})
```

At the beginning, you set the default state of the component. In this case, we want to have an empty `text` value. To do that you use component method `getInitialState()` that has to return state object for the component.

To update the state an event handler `changeText()` is assigned to the `onChange` event. To update the state React expects you use built-in [`setState()`](https://facebook.github.io/react/docs/react-component.html#setstate) method.

The state update will be scheduled and the component will re-render when it's done. `setState()` call needs to be used to inform React about pending state change so it can apply the changes. There are no loops of any kind that track if something has changed.

You need to remember that `setState()` is asynchronous. The results are not immediate. Examples below show both bad and good way to access the state immediately after the change is applied:

```javascript
// BAD:
// ...
someFunction (value) {
  this.setState({someValue: value})
  // may not be changed at this point
  console.log('New value: ', this.state.someValue)
}
// ...
```

```javascript
// GOOD:
// ...
someFunction (value) {
  this.setState({someValue: value}, () => {
    // do stuff with new state
    console.log('New value: ', this.state.someValue)
  })
}
// ...
```

Ok, but what if there is a need to propagate the state changes to the parent component?

## 8) Events go up

Let's say we have a `Parent` component that needs to get the data from the child `InputBox` from the previous example.

```javascript
const Parent = React.createClass({
  gimmeThatState (textFromInput) {
    console.log(textFromInput)
    // or this.setState({text: textFromInput})
  },

  render () {
    <InputBox pushChangesUp={this.gimmeThatState} />
  }
})
```

`Parent` component passes down a function (as a prop) that can be used by `InputBox` to push some data up.

The updated `InputBox` could look like this:

```javascript
const InputBox = React.createClass({
  propTypes: {
    pushChangesUp: React.PropTypes.func.isRequired
  },

  getInitialState () {
    return {
      text: ''
    }
  },

  changeText (event) {
    this.setState({text: event.target.value})
  },

  pushChangesUp () {
    this.props.pushChangesUp(this.state.text)
  }

  render () {
    return (
      <div>
        <input type='text' onChange={this.changeText} placeholder='text' value={this.state.text} />
        <span>{this.state.text}</span>
        <button onClick={this.pushChangesUp}>Push changes up</button>
      </div>
    )
  }
})
```

The first thing you see is a `propTypes` property at the beginning of the component declaration. It's used to validate the props. For me, it serves a similar purpose as an interface in OOP. By looking at `propTypes` I immediately know what I need to provide to the component to make it work.

Next, the local `pushChangesUp()` event handler is assigned to the `onClick` event on a button. When clicked, the function uses `pushChangesUp()` from props to push the data up.

Now, `Parent` component can save the data in its own state and pass it down to a different component.

## 9) How rendering works

Every `setState()` call informs React about state changes. Then, React calls `render()` method to update the components representation in memory ([Virtual DOM](http://reactkungfu.com/2015/10/the-difference-between-virtual-dom-and-dom/)) and compares it with what's rendered in the browser. If there are changes, React does the smallest possible update to the DOM.

Child components know that they need to re-render because their props changed.

I often compare that to a diff mechanism in Git. There are two snapshots of component tree that React compares and just swaps what needs to be swapped.

I was looking for a clever diagram describing the render flow but couldn't find one. You can read more about it [here](https://facebook.github.io/react/docs/react-component.html) though.

## 10) Composition is the key

Parent components that own the state are often referred to as **container components**. They are responsible for state management and rendering children (this sounds so odd). Child components are used to trigger event handlers passed down from parents (like the `InputBox` component in previous examples) and to display the data.

Child components that are responsible for displaying the data are called **presentational components**.

Container component is often responsible for fetching data, API calls (see [`componentDidMount()`](https://facebook.github.io/react/docs/react-component.html#componentdidmount) lifecycle method) and so on. You should keep this in one place to avoid side-effects in presentational components. Those should be as dumb as possible about everything other than displaying the data.

This separation of concerns and terminology were popularized by Dan Abramov, the author of [Redux](http://redux.js.org/). You can read more about it in [his article](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.t7vy4hwfy).

You can see that it all fits together. When every component follows single responsibility principle it can be composed with others and reused.

The biggest challenge is to figure out how to divide those responsibilities and where to put the state. If you want to know more about the topic search for ["thinking in react"](https://facebook.github.io/react/docs/thinking-in-react.html) articles.

## 11) Keep the state small

On my training, there is often an exercise involving some kind of list filtering. Let's say you have a list of todos:

```javascript
const initialState = [
  {id: 1, text: 'laundry'},
  {id: 2, text: 'shopping'}
  // ...
]

const List = React.createClass({
  getInitialState () {
    return {
      todos: initialState
    }
  },

  render () {
    return (
      <div>
        <ul>
          {this.state.todos.map(todo => <li key={todo.id}>{todo.text}</li>)}
        </ul>
      </div>
    )
  }
})
```

And now, you want to add a search box. 50% people would go with some variation of this approach:

```javascript

const initialState = [
  {id: 1, text: 'laundry'},
  {id: 2, text: 'shopping'}
  // ...
]

const List = React.createClass({
  getInitialState () {
    return {
      todos: initialState,
      filteredTodos: null
    }
  },

  search (searchText) {
    const filteredTodos = this.state.todos(todo => todo.text.indexOf(searchText) > 0)

    this.setState({filteredTodos: filteredTodos})
  },

  render () {
    const {filteredTodos, todos} = this.state // get todos from state

    const list = filteredTodos === null ? todos : filteredTodos // if there are filtered todos use them

    return (
      <div>
        <SearchBox onChange={this.search} />
        <ul>
          {list.map(todo => <li key={todo.id}>{todo.text}</li>)}
        </ul>
      </div>
    )
  }
})
```

What you can see here is duplicated state, two sources of truth and introduction of spaghetti code. Just imagine that you want to update one of the todos with search filter turned on.

What's better? Keep the state as small as possible. If something can be [calculated on the fly](https://facebook.github.io/react/docs/thinking-in-react.html#step-3-identify-the-minimal-but-complete-representation-of-ui-state) then it should be.

Here is a better solution:

```javascript
const initialState = [
  {id: 1, text: 'laundry'},
  {id: 2, text: 'shopping'}
  // ...
]

const List = React.createClass({
  getInitialState () {
    return {
      todos: initialState,
      searchText: null
    }
  },

  search (searchText) {
    this.setState({searchText: searchText})
  },

  filter (todos) {
    if (!this.state.searchText) {
      return todos
    }

    return todos.filter(todo => todo.text.indexOf(this.state.searchText) > 0)
  },

  render () {
    return (
      <div>
        <SearchBox onChange={this.search} />
        <ul>
          {this.filter(list).map(todo => <li key={todo.id}>{todo.text}</li>)}
        </ul>
      </div>
    )
  }
})
```

Here you keep only the `searchText` that is used to filter the list before rendering. A much cleaner approach, a smaller state, and no duplication.

## 12) Conditional rendering

In the previous example, the list was rendered depending on some conditional logic. It's often needed to render one part of the markup if some conditions are met, and the other if they are not. In React there are a few ways to do that.

### Ternary operator

In JSX it's possible to use [ternary operator](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) to perform conditional rendering:

```javascript
React.createClass({
  getInitialState () {
    return {
      hideTodos: true
    }
  },

  render () {
    return (
      <div>
      {
        hideTodos ? 'Sorry there is no data' : <TodoList />
      }
      </div>
    )
  }
})
```

Possible variations:

- ternary operator outside `return` expression
- if/else block outside `return` expression

### Helper function

```javascript
React.createClass({
  getInitialState () {
    return {
      hideTodos: true
    }
  },

  renderTodos () {
    if (this.state.hideTodos) {
      return 'Sorry there is no data'
    }

    return <TodoList />
  }

  render () {
    return (
      <div>
      {
        this.renderTodos()
      }
      </div>
    )
  }
})
```

A useful approach, but when the component is bigger you need to jump up and down between the helper and a `render()` method.

### A component

This is probably the cleanest approach, works well as a [feature toggle](http://martinfowler.com/bliki/FeatureToggle.html).

```javascript
React.createClass({
  getInitialState () {
    return {
      hideTodos: true
    }
  },

  render () {
    return (
      <div>
        <HideIf condition={this.state.hideTodos}>
          <TodoList />
        </HideIf>
      </div>
    )
  }
})

const HideIf = React.createClass({
  render () {
    if (this.props.condition) {
      return <span>'Sorry there is no data'</span>
    }

    return this.props.children // children is what's inside <HideIf> element
  }
})
```

## 13) You don't need Flux

Probably the most common misconception among React newcomers is that you need to use it with Redux or some other Flux implementation.

Redux is great. It's the most popular Flux implementation thanks to [great tutorials](https://egghead.io/courses/getting-started-with-redux), lots of features and clean, functional, testable approach. [But you might not need it](https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367#.cdf363ebw).

If you are learning React, if your app is small, if you don't need global state or you don't have any problems with tracking the state changes in your app - *don't use it*.

If you want to know more read about it [here](http://redux.js.org/docs/faq/General.html#general-when-to-use).

## Wrap-up

So, this was my list of React concepts I discuss with people the most. I highly recommend reading [React docs](https://facebook.github.io/react/docs/hello-world.html) as it is the best source of knowledge if you read it from cover to cover. I also recommend watching early React videos (from ~2013-2014) describing what problems Facebook was trying to solve when they created React. It will help you recognize if you have similar problems *and React would help you* or you should stick to some other technology.
