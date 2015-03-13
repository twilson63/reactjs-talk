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


    var MyComponent = React.createClass({
      render: function() {
        return React.createElement('h1', null, 'HelloWorld')
      }
    });

--

### es6

    class MyComponent extends React.Component {
      render() {
        return React.createElement('h1', null, 'HelloWorld')
      }
    }


--

# JSX
## JavaScript XML

--

JSX -- an XML-like syntax for constructing markup within React components. 

--

## JSX

    React.createElement('h1', { className: 'title'}, 'Hello World')


    <h1 className="title">Hello World</h1>


--

<a class="jsbin-embed" href="http://jsbin.com/wusige/1/embed?html,output">Hello React</a><script src="http://static.jsbin.com/js/embed.js"></script>

--

# Why JSX?

--

## Familiarity

--

## Semantics

--

## no JSX

    render: function() {
      return React.createElement('h1', { className: 'divider'}, 
        "Label Text",
        React.createElement('hr')
      );
    }

--

## JSX

    render: function() {
      return <div className="divider">
        Label Text<hr />
      </div>;
    }

--

## Many agree that JSX markup is easier to understand and easier to debug

--

## Abstraction

Any dsl changes to React does not affect `JSX`

--

## Separation of concerns

Seeing both the markup and code clearly separates concerns in the file.

--

### ReactJS Adventure

* Open Console

    npm i reactjs-adventure -g
    mkdir <your name>
    git clone git@github.com:twilson63/reactjs-helloworld.git
    cd reactjs-helloworld
    npm install
    reactjs-adventure

--

# Composite components

--

## Defining a custom component

    <div className="divider">
      <h2>FooBar</h2>
    </div>

--

## Defining a custom component

    var Divider = React.createClass({
      render: function() {
        return (
          <div className="divider">
            <h2>FooBar</h2>
          </div>
        );
      }
    });

--

## Dynamic values

    var Divider = React.createClass({
      render: function() {
        var text = 'FooBar';
        return (
          <div className="divider">
            <h2>{text}</h2><hr />
          </div>
        );
      }
    });

## 

## Composing the custom component

<a class="jsbin-embed" href="http://jsbin.com/movufi/1/embed?html,output">Hello React</a><script src="http://static.jsbin.com/js/embed.js"></script>

--

# JSX vs HTML

--

### Attributes

    <div id="some-id" className="some-class-name"></div>

dynamic

    var recordId = this.props.id;
    var classes = 'some-class-name';
    ...
    <div id={recordId}  className={classes}>...</div>

--

### Conditionals

    <div className={ 
      this.state.isComplete ? 'isComplete' : '' 
    }>...</div>

* use ternary logic
* set a variable 
* offload to a function
* use the && 

    <div className={
      this.state.isComplete && 'isComplete'
    }>...</div>

--

### Non-DOM Attributes

* key
* ref
* dangerouslySetInnerHTML

--

### ref
    
    <div>
      <input ref="myInput" ... />
    </div>


    this.ref.myInput // Inside your component

--

### Events

    ...
    handleClick: function(event) { ... },
    render: function() {
      return <div onClick={this.handleClick.bind(this)}>...</div>
    }

--

### Comments

    <div>
      {/* 
        a comment
      */}
    </div>

    <input 
      /*
        comment
      */
      />

    <input
      name="email" // inline comment
      />

--

### Special attributes

    <label htmlFor="for-text" ...>

    <div className={classes} ...>

--

### Styles

    var styles = {
      borderColor: '#999',
      borderThickness: '1px'
    };
    React.render(<div style={styles}>...</div>, node);

--

### Without JSX

    var DividerClass = React.createClass({ displayName: 'Divider',
      render: function() {
        return {
          React.createElement('div', {className: 'divider'}, 
            React.createElement('h2', null, this.props.children),
            React.createElement('hr', null)
          )
        }
      }
    })  

--

# Component Lifecycle

--

### Instanciation

* getDefaultProps
* getInitialState
* componentWillMount
* render
* componentDidMount

--

### All subsquent uses

* getInitialState
* componentWillMount
* render
* componentDidMount

--

### Lifetime

* componentWillRecieveProps
* shouldComponentUpdate
* componentWillUpdate
* render
* componentDidUpdate

--

### Teardown

* componentWillUnmount

--

### getDefaultProps

called only once, sets default values when not specified by parent

--

### getInitialState

called only once, chance to customize internal state

--

### componentWillMount

before the initial render, last chance to change the state 
before a render method is called.

--

### render

Builds the virtual DOM - should be a `PURE` function

can return null, false or React component

--

### componentDidMount

Can access actual node via `this.getDOMNode()`

This is the lifecycle hook for accessing non-react components

    var datasources = [...];
    var MyComponent = React.createClass({
      render: function() {
        return <input />
      },
      componentDidMount: function() {
        $(this.getDOMNode()).autocomplete({
          sources: datasources
        })
      }
    });

--

### componentWillReceiveProps

Props can change at any moment, this method gives
the component the opportunity to update the state
from the changed props.

    componentWillReceiveProps: function(nextProps) {
      if(nextProps.checked !== undefined) {
        this.setState({
            checked: nextProps.checked
          });
      }
    }

--

### shouldComponentUpdate

If you don't need to re-render the component return false.

** Be careful not to pre-optimize

--

### componentWillUpdate

Called when props change, but can't update date in this method.

--

### componentDidUpdate

similar to componentDidMount

--

### componentWillUnmount

this is where you can do any cleanup

--

### Anti-Pattern

calculated values as state

calcualate values at render time.

--

# Data Flow

--

# Parent -> Child

--

## Props

Short for Properties

--

## PropTypes

var TableRow = React.createClass({
  propTypes: {
    survey: React.PropTypes.shape({
      id: React.PropTypes.number.isRequired
    }).isRequired,
    onClick: React.PropTypes.func
  }
});

--

## getDefaultProps

called as soon as React.createClass is called

--

## State

Internal state of your component

* setState - never update state directly

--

* Try to use state for simple data
* Always consider props as the truth

--

# Event Handling

    <button className="btn btn-save" 
      onClick={this.handleSaveClicked}>
      Save
    </button>

--

# Composition

--

# Mixins

--

# DOM Manipulation

--

# Forms

--

# Animations

--

