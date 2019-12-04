### Remember

Use https://reactjs.org/docs/react-component.html#the-component-lifecycle and http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/ to answer these on your own then compare answers as a group

1.  Each component has several `lifecycle methods` that you can override to do what?

Run code at various points in the lifecycle of the React component.

2.  What are the 4 categories of lifecycle methods? (these are the headings from the first link)

Mounting 
Updating
Unmounting
Error Handling

3.  What are the names of the 5 commonly used lifecycle methods? (these are in bold in the first link)

constructor
render
componentDidMount
componentDidUpdate
componentWillUnmount

### Understand

Discuss this question in pairs if you have a 4-person group

4.  What's going on in this code?

```jsx
import React, { Component } from "react";

class Mentor extends Component {
  componentDidUpdate() {
    console.log("Logan saved the day!");
  }
  render() {
    return (
      <div>
        <h1>Logan Mace</h1>
        <h2>{this.props.questions.length}</h2>
        <h3>questions to answer</h3>
        <button onClick={this.props.answerQuestion}>Answer a question!</button>
      </div>
    );
  }
}
```
Everytime that the state or the props of this component updates, the componentDidUpdate lifecycle method gets invoked and will console log Logan saved the day. The h2 is displaying the length of the questions from the props questions property. The button will invoke a function passed down on the props in the parent component. 

### Apply

Try these on your own, but work together if you start to get stuck.

5.  Update the `Mentor` component above so that the message that is currently being console.log'd is displayed below the number of questions answered instead.

```jsx
import React, { Component } from "react";

class Mentor extends Component {
  componentDidUpdate() {
    console.log("Logan saved the day!");
  }
  render() {
    return (
      <div>
        <h1>Logan Mace</h1>
        <h2>{this.props.questions.length}</h2>
        <p>Logan saved the day!</p>
        <h3>questions to answer</h3>
        <button onClick={this.props.answerQuestion}>Answer a question!</button>
      </div>
    );
  }
}
```