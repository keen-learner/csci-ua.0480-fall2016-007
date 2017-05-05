---
layout: slides
title: "React Continued"
---

<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

<p><small></small></p>
</section>

<section markdown="block">
## A Little Bit of Refresher

__What's react again?__ &rarr;

On its own __React__ is  a library for generating the user interface of an application. 
{:.fragment}

* {:.fragment} think of it as the __view__ in an MVC app
* {:.fragment} it provides an API for creating and rendering reusable view components
	* {:.fragment} including state management
	* {:.fragment} ...and event handling

</section>

<section markdown="block">
## Running a React App

__What did we use to demonstrate our small React examples?__ &rarr;

We used Codepen (jsbin is also an option). However... __we had to do a little bit of configuration first.__ &rarr;
{:.fragment}

* {:.fragment} for __codepen__: 
	* {:.fragment} set __Babel__ as the JavaScript preprocessor
	* {:.fragment} add the __react libaray__ as external JavaScript
* {:.fragment} for __jsbin__:
	* {:.fragment} use __Add Library__ to add react
	* {:.fragment} select __JSX (React)__ in the JavaScript drop down

</section>

<section markdown="block">
## Creating an Element

ReactElements are elements in a _virtual DOM_.  __Here's what creating a ReactElement looks like...__ &rarr;

<pre><code data-trim contenteditable>
React.createElement('h1', {className: 'hello'}, 'Hi There!'); 
</code></pre>
{:.fragment}

<code>createElement</code> has 3 parameters:
{:.fragment}

* {:.fragment} first parameter... element that you want to create as a string
* {:.fragment} second parameter... its attributes (note that __class is className__!)
* {:.fragment} third parameter... its text content
* {:.fragment}it'll return a __ReactElement__ object

</section>

<section markdown="block">
## Rendering

Changes in the virtual DOM are combined together and applied to the actual DOM in a way that minimizes DOM modification. __Here's what rendering a ReactElement looks like.__ &rarr;

<pre><code data-trim contenteditable>
ReactDOM.render(
    React.createElement('h1', {className: 'hello'}, 'Hi there!'), 
	document.body
);
</code></pre>
{:.fragment}

<code>render</code> has two arguments
{:.fragment}

* {:.fragment} first parameter... a <code>ReactElement</code>
* {:.fragment} second parameter... an insertion point (where to add element as a child - can be a regular <code>HTMLElement!</code>)

__Let's give it a try.__ &rarr;
{:.fragment}
</section>

<section markdown="block">
## Another Way

Sooo... there was another _unusual_ way of creating ReactElements. __What was it?__ &rarr;

__Using JSX, we could...__ &rarr;
{:.fragment}

<pre><code data-trim contenteditable>
ReactDOM.render(
	<h1 className="hello">Hi there!</h1>, 
	document.body
);
</code></pre>
{:.fragment}
</section>

<section markdown="block">
## Another Way Explained....

__Why did that look so unusual?__ &rarr;

<pre><code data-trim contenteditable>
ReactDOM.render(
	<h1 className="hello">Hi there!</h1>, 
	document.body
);
</code></pre>

Hey - there's markup in my JavaScript. It's an unquoted string! What!?
{:.fragment}
</section>

<section markdown="block">
## JSX

__So, what's JSX again?__ &rarr;


__JSX__ is an extension to JavaScript syntax that allows _XML-like_ syntax without

* {:.fragment} it's essentially a JavaScript preprocessor
	* {:.fragment} it takes in JavaScript with JSX syntax
	* {:.fragment} and _compiles_ JSX to plain vanilla JavaScript 
* {:.fragment} its usage is optional; you could just use plain JavaScript with react
* {:.fragment} also... __browsers don't quite understand JSX__ (maybe yet?)
	
</section>

<section markdown="block">
## JSX Continued

So that means... this JSX

<pre><code data-trim contenteditable>
<h1 className="hello">Hi there!</h1>
</code></pre>

...is equivalent to this vanilla JavaScript

<pre><code data-trim contenteditable>
React.createElement('h1', {className: 'hello'}, 'Hi there!'), 
</code></pre>

They both produce a ReactElement!
</section>

<section markdown="block">
## Components

You can bundle elements together into a single component. __Here's an example.__ &rarr;

<pre><code data-trim contenteditable>
var MyComponent = React.createClass({
  render: function() {
    return (
      &lt;div&gt; &lt;h1&gt;A Message&lt;&#47;h1&gt;{this.props.message}&lt;&#47;div&gt;
    );
  }
});

</code></pre>

<pre><code data-trim contenteditable>
ReactDOM.render(
  <MyComponent message="Hi there!" &#47;>,
  document.body
);
</code></pre>
</section>

<section markdown="block">
## Components and Props

To make a component, use <code>React.createClass</code>, which takes an object as a parameter or use __ES6 classes__.

* the object must have a function called __render__ (it'll generate elements)
* note that a __component variable must start with uppercase__
* once you have a component, you can pass it to render using JSX, with the variable name as the tag name
* you can access attributes defined in JSX via __this.props__ in your component
</section>

<section markdown="block">
## Say Hi or Bye!

__Let's try to create a component that...__ &rarr;

* displays "hi" if the attribute, <code>greet</code> is true
* otherwise, it'll display "bye" instead

<br>
For example... rendering...

<pre><code data-trim contenteditable>
<MyComponent greet={true} &#47;>,
</code></pre>

Gives us

<pre><code data-trim contenteditable>
<div>hi</div>
</code></pre>

Changing <code>greet</code> to false would give us <code>bye</code> instead.
</section>

<section markdown="block">
## Say Hi or Bye!

<pre><code data-trim contenteditable>
var MyComponent = React.createClass({
  render: function() {
    var msg = this.props.greet ? 'hi' : 'bye';
    return (
      &lt;h1&gt;{msg}&lt;&#47;h1&gt;
    )
  }
});
</code></pre>

<pre><code data-trim contenteditable>
ReactDOM.render(
	<MyComponent greet={true} &#47;>, 
	document.body
);
</code></pre>

</section>

<section markdown="block">
## Events

To add an event handler in JSX... add an inline attribute (wait, what!?). For example, click events would be represented by <code>onClick</code>:

<pre><code data-trim contenteditable>
var MyButton = React.createClass({
  onButtonClick: function(evt) {
    alert("Clicked!");
  },

  render: function() {
    return <div onClick={this.onButtonClick}>Press This Button<&#47;div>;
  }
});

ReactDOM.render(
  <MyButton &#47;>,
  document.body
)
</code></pre>
</section>

<section markdown="block">
## State

__state__ is internal data controlled by the component (contrast this with __props__, which are controlled by whatever renders the component).

To initialize state properties when your component is created, __define a <code>getInitialState</code> within your component definition... and return the desired state properties as property value pairs within an object.__ &rarr;

<pre><code data-trim contenteditable>
{ // within a component definition
  getInitialState: function() {
    return {
      prop: val,
    }
  }
}
</code></pre>
{:.fragment}

__To read state....__ &rarr;
{:.fragment}

<pre><code data-trim contenteditable>
this.state.propertyName
</code></pre>
{:.fragment}

To set state:
{:.fragment}

<pre><code data-trim contenteditable>
this.setState({stateName: stateValue});
</code></pre>
{:.fragment}
</section>

<section markdown="block">
## Using State... an Example

__Let's define a couple of state variables, and put their values in a list when the component is rendered.__ &rarr;

<pre><code data-trim contenteditable>
var MyComponent = React.createClass({
  render: function() {
    return (
      <ul>
      <li>{this.state.var1}</li>
      <li>{this.state.var2}</li>
      </ul>
    )
  },
  getInitialState: function() {
    return {
      var1: 'this is the first variable',
      var2: 'and a second variable'
    }
  }
});
</code></pre>
</section>

<section markdown="block">
## State With ES6 Classes

__Things are slightly different if you're using ES6 Classes to define your components__ &rarr;

* {:.fragment} instead of defining `getInitialState`, create a constructor that sets the state property to an object:
* {:.fragment} also, you'll have to watch out for how `this` works (`createClass` handles it for you, but ES6 classes do not)


</section>

<section markdown="block">
## From `getInitialState` to `constructor`

__Instead of defining `getInitialState`...__ &rarr;

Create a constructor (optionally defining a props parameter), call `super` and assign an object to `this.state`
{:.fragment}

<pre><code data-trim contenteditable>
constructor() {
  super();
  this.state = {
    title: 'A React Component'
  };
}
</code></pre>
{:.fragment}

Pass in `props` to your constructor if you want access to "attributes" (`this.props` isn't available within the constructor yet, so props can be accessed via parameter):
{:.fragment}

<pre><code data-trim contenteditable>
constructor(props) { ... }
</code></pre>
{:.fragment}

</section>

<section markdown="block">
## `createClass` and `this`

Let's check out an event example with `createClass`. __There's something a little suspicious about the code - what's weird about it?__ &rarr;

<pre><code data-trim contenteditable>
var MyButton = React.createClass({
  getInitialState: function() {
    return { msg: 'Clicked!!!' };
  },

  handleClick: function(evt) { alert(this.state.msg); },

  render: function() {
    return <div onClick={this.handleClick}>Press Me!<&#47;div>;
  }
});
</code></pre>

* {:.fragment} `this` _should_ refer to the global object, but it doesn't; everything works just fine!
* {:.fragment} fortunately, when we use `createClass`, `this` is automatically set to the instance of the created `ReactElement` for us!
</section>

<section markdown="block">
## Events, State, ES6 Classes

Unfortunately, __ES6 classes__ do not set `this` for us like `createClass` does. __Consequently, the code below, which _looks_ equivalent, will not work!__ &rarr;

<pre><code data-trim contenteditable>
class MyButton extends React.Component {
  constructor() {
    super();
    this.state = { msg: 'Clicked!!!' };
  }

  // Y U NO WORK??????
  handleClick(evt) { alert(this.state.msg); }

  render() {
    return <div onClick={this.handleClick}>Press Me!</div>;
  }
}
</code></pre>

</section>

<section markdown="block">
## Fixing `this`

__Let's modify the following lines so that `this` is bound to the instance rather than the global object.__ &rarr;

<pre><code data-trim contenteditable>
handleClick(evt) { alert(this.state.msg); }

render() {
  return <div onClick={this.handleClick}>Press Me!</div>;
}
</code></pre>

* {:.fragment} use good 'ol bind!
    * {:.fragment} `<div onClick={this.handleClick.bind(this)}>`
* {:.fragment} wrap `handleClick` in an arrow function to capture `render`'s `this`:
    * {:.fragment} `<div onClick={() => {this.handleClick()}}>`
</section>


<section markdown="block">
## A Challenge

Using events and state, create a component that:

* renders a div with a class of number
* the number starts at 0
* every time you click on the div, the number increases

<br />

<div markdown="block" class="img">
![number click](../../resources/img/number-click.gif)
</div>


</section>


<section markdown="block">
## A Solution

Start off with some boiler plate...

<pre><code data-trim contenteditable>
var MyComponent = React.createClass({
	// render, getInitialState and event handler
	// goes here...
});
</code></pre>

<pre><code data-trim contenteditable>
ReactDOM.render(
	<MyComponent &#47;>, 
	document.body
);
</code></pre>

</section>

<section markdown="block">
## A Solution (Continued)

Within your component definition:


<pre><code data-trim contenteditable>
  getInitialState: function() {
    return {
      count: 0,
    }
  }
</code></pre>

<pre><code data-trim contenteditable>
  handleClick: function() {
    this.setState({count: this.state.count + 1});
  }
</code></pre>

<pre><code data-trim contenteditable>
  render: function() {
    return (
      <div className="number" 
	  onClick={this.handleClick}>{this.state.count}<&#47;div>
    )
  }
</code></pre>
</section>

<section markdown="block">
## What About These Components?

__Now let's try adding 3 counters to our render...__ &rarr;
<pre><code data-trim contenteditable>
ReactDOM.render(
  &lt;div&gt;&lt;Counter /&gt;&lt;Counter /&gt;&lt;Counter /&gt;&lt;/div&gt;,
    document.body
);
</code></pre>


</section>

<section markdown="block">
## Oh, Also, an ES6 Class Version

<pre><code data-trim contenteditable>
class Clicker extends React.Component {
  constructor() {
    super();
    this.state = {count: 0};
  }
  
  render() {
    return <div onClick={() => {this.handleClick()}}><h2>{this.state.count}</h2></div>;
  }
  
  handleClick() {
    this.setState({count: this.state.count + 1});
  }
}
</code></pre>

</section>

<section markdown="block">
## More Complex Components

__When you're actually writing _real_ components__ &rarr;

* you'll often find that you'll be creating components that have nested components interacting with each other
* ... for example, a button and a text field that set some text in the containing element/component

<br>

__The common pattern for this is to:__ &rarr;

* {:.fragment} move state out of the child components
* {:.fragment} all of the state will go in the parent
* {:.fragment} the parent will orchestrate interactions
* {:.fragment} ...this will be done by the parent setting props on its children
    * {:.fragment} such as event handler functions
    * {:.fragment} ...and any other attributes


</section>


<section markdown="block">
## Communication Between Components

From the react docs: __When you want to__ &rarr;

1. aggregate data from multiple children 
2. ... or have two child components communicate with each other

<br>
__Move the state upwards so that it lives in the parent component:__ &rarr;

* The parent can then pass the state back down to the children __via props__... 
* so that the child components are always in sync with each other and with the parent.

</section>

<section markdown="block">
## Ceding Control to Parent 

__In this example, the child component doesn't define its own click handler, but instead receives one from its parent via props.__ &rarr;

<pre><code data-trim contenteditable>
class Parent extends React.Component {
  // this handleClick will be used by the child!
  handleClick() {
    alert('cliiiiick me');
  }
  
  render() {
    // pass handlClick to child as a prop
    return <Child onClick={this.handleClick} />
  }
}
</code></pre>

<pre><code data-trim contenteditable>
class Child extends React.Component {
  render() {
    return (&lt;div onClick={this.props.onClick}&gt;
      PRESS ME&lt;/div&gt;);
  }
}
</code></pre>

<pre><code data-trim contenteditable>
ReactDOM.render(&lt;Parent /&gt;, document.body);
</code></pre>
</section>

<section markdown="block">
## Counting Revisited

__Let's try rewriting our counter so that the state is moved up to a parent element.__ &rarr;

Start with our parent class...

<pre><code data-trim contenteditable>
class Parent extends React.Component {
}
</code></pre>
{:.fragment}

Within that parent class, define a constructor to create initial state.
{:.fragment}

<pre><code data-trim contenteditable>
  constructor() {
    super();
    this.state = {
      count:0
    }
  }
</code></pre>
{:.fragment}

</section>

<section markdown="block">
## Parent Class Continued: `handleClick`

__Now let's define `handleClick`__ &rarr;

* {:.fragment} `handleClick` sets the state like it did previously
* {:.fragment} but note that in order to do set state, it needs access to `this`!


<pre><code data-trim contenteditable>
  handleClick() {
    this.setState({count: this.state.count + 1});
  }
</code></pre>
{:.fragment}


</section>

<section markdown="block">
## Parent Class Continued: `render`

__`render` creates a child element and passes down a click handler and a count as props__ &rarr;

<pre><code data-trim contenteditable>
  render() {
    // note that we have to bind this so that we have 
    // access to the  this of the instance that render is 
    // called on(and consequently this.state!
    const handler = this.handleClick.bind(this);
    return (
      &lt;Child onClick={handler} val={this.state.count} /&gt;
    );
  }
</code></pre>
{:.fragment}

* {:.fragment} use `bind` to bind context of handleClick to instance
* {:.fragment} alternatively, you can inline and arrow function as the value of onClick in JSX:
    * {:.fragment} `onClick={() => {this.handleClick()}}`
    * {:.fragment} note that if you're using an arrow function, call the click handler!
  
</section>

<section markdown="block">
## A Slightly More Efficient Version

__If you're worried about making too many function objects, you can set this.handleClick to the bound version in the constructor rather than each time `render` is called__ &rarr;

<pre><code data-trim contenteditable>
  constructor() {
    // add this line...
    this.handleClick = this.handleClick.bind(this);
}
</code></pre>

<pre><code data-trim contenteditable>
  render() {
    // change back to using this.handleClick
    return (
      &lt;Child onClick={this.handleClick} val={this.state.count} /&gt;
    );
  }
</code></pre>
</section>


<section markdown="block">
## Child Component

__Finally, for the child component, use props to define its click handler and its text content.__ &rarr;

<pre><code data-trim contenteditable>
class Child extends React.Component {
  render() {
    return (
      &lt;div onClick={this.props.onClick}&gt;
        {this.props.val}
      &lt;/div&gt;);
  }
}
</code></pre>
{:.fragment}

Of course, call `render`:
{:.fragment}

<pre><code data-trim contenteditable>
ReactDOM.render(&lt;Parent /&gt;, document.body);
</code></pre>
{:.fragment}
</section>


<section markdown="block">
## Two Clickers!

Your event handler may require an argument. __For example, it's a way to specify which child component was clicked without the child explicitly__ 

<pre><code data-trim contenteditable>
// passing args to handle click, fixing arity, computer property names
class Parent extends React.Component {
}
</code></pre>

Again, start with a constructor, but now we have state for two click boxes!
<pre><code data-trim contenteditable>
  constructor() {
    super();
    this.state = {
      box1:0,
      box2:0
    }
  }

</code></pre>

</section>

<section markdown="block">
## Two Clickers Continued

__Notice that our handleClick function will take an argument, the name of the box:__ &rarr;

<pre><code data-trim contenteditable>
  handleClick(name) {
    // setState will be called based on this name!
    // this is using shorthand syntax for dynamic keys:
    this.setState({[name]: this.state[name] + 1});
  }
  
</code></pre>

Lastly, when we define render, note that we're passing in different arguments to the call to handleClick.

<pre><code data-trim contenteditable>
  render() {
    return (<div>
        <Child onClick={() => {this.handleClick('box1')}} val={this.state.box1} />
        <Child onClick={() => {this.handleClick('box2')}} val={this.state.box2} />
      </div>);
  }
</code></pre>
</section>

<section markdown="block">
## Child

And, of course, our Child component code:

<pre><code data-trim contenteditable>
class Child extends React.Component {
  render() {
    return <div onClick={this.props.onClick}>{this.props.val}</div>;
  }
}


</code></pre>


Rendering ...

<pre><code data-trim contenteditable>
ReactDOM.render(<Parent />, document.body);
</code></pre>

</section>

<section markdown="block">
## Another Example

__Let's change our original clicker so that:__ &rarr;

* the button is a nested component
* the count is shown in the button
* the count is shown outside of the button as well

<br>

<pre><code data-trim contenteditable>
Parent Count: 4
Child Count: 4
</code></pre>




</section>

<section markdown="block">
## Parent: `ClickCounter`

__This component is the parent; you can see that it:__ &rarr;

* controls what the child component will do on click by handing down the `onClick` function via props
* and sets props on its child by using the values from its own state

<pre><code data-trim contenteditable>
class ClickCounter extends React.Component {
  constructor() {
    super();
    this.state = { count: 0 };
  }
  handleClick(arg) {
    alert(arg + ' ' + this.state.count);
    this.setState( { count: this.state.count + 1} );
  }
  render() {
    // wrap onclick callback in arrow function to handle this
    return <div><h1>Parent Count: {this.state.count}</h1><Clicker count={this.state.count} onClick={() => {this.handleClick("clicked!")}} /></div>;
  }
}
</code></pre>

</section>


<section markdown="block">
## Child: `Clicker`

__Aaaand here's our child implementation__ &rarr;

<pre><code data-trim contenteditable>
class Clicker extends React.Component {
  render() {
    return <div onClick={() => {this.props.onClick()}}>Child Count:{this.props.count}</div>;
  }
}
</code></pre>

Of course... rendering:

<pre><code data-trim contenteditable>
ReactDOM.render(
  <ClickCounter />,
  document.body
)
</code></pre>
</section>
