title: ReactJS CodeCampCHS
author:
  name: Tom Wilson
  twitter: twilson63
  url: http://jackrussellsoftware.com
output: index.html
controls: true

--

# ReactJS 
## Introduction

--

# What is ReactJS?

--

### A State Machine

1. Updating the DOM
2. Responding to Events

--

# Background

## Created at Facebook as a port of PHP Framework XHP

--

# What React is not?

--

## No opinions:

* AJAX
* routing
* storage
* structure

--

# Why React?

--

### Hello, ReactJS

<a class="jsbin-embed" href="http://jsbin.com/hafefe/1/embed?html,output">Hello React</a><script src="http://static.jsbin.com/js/embed.js"></script>

--

# Components

--

> Components are used to separate concerns, not templates and 
> display logic. When using React, you must embrace the idea that
> markup, and the code that generates it, are inherently tied together.

--

### es5

``` js
var MyComponent = React.createClass({
  render: function() {
    return React.createElement('h1', null, 'HelloWorld')
  }
});
```
--

### es6

``` js
class MyComponent extends React.Component {
  render() {
    return React.createElement('h1', null, 'HelloWorld')
  }
}
```

--

# JSX
## JavaScript XML

--

JSX -- an XML-like syntax for constructing markup within React components. 

--

``` js
React.createElement('h1', { className: 'title'}, 'Hello World')
```

``` html
<h1 className="title">Hello World</h1>
```

--

<a class="jsbin-embed" href="http://jsbin.com/wusige/1/embed?html,output">Hello React</a><script src="http://static.jsbin.com/js/embed.js"></script>

--

# Why JSX?

--

## Familiarity

--

## Semantics

--

``` js
render: function() {
  return React.createElement('h1', { className: 'divider'}, 
    "Label Text",
    React.createElement('hr')
  );
}
```

--

``` jsx
render: function() {
  return <div className="divider">
    Label Text<hr />
  </div>;
}
```

--

## Many agree that JSX markup is easier to understand and easier to debug

--

## Abstration

--

## Separation of concerns

--

### ReactJS Adventure

* Open Console

```
npm i reactjs-adventure -g
mkdir <your name>
git clone git@github.com:twilson63/reactjs-helloworld.git
cd reactjs-helloworld
npm install
reactjs-adventure
```
--

# Composite components

--
