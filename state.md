### Remember

Answer these on your own, then compare answers as a group

1.  What is state?

State is an object, unique to each component that is updated by actions from the view (or other ways) and can be passed down as props to children components or rendered out on the screen by being included in the jsx.

2.  Where do you set initial state?

In the constructor of the class Component.

3.  What method do you use to update state?

setState

### Understand

Discuss this question in pairs if you have a 4-person group

4.  Explain what's happening in this component.

```jsx
import React, { Component } from "react";

class LeadMentor extends Component {
  constructor(props) {
    super(props);
    this.state = {
      questionsAnswered: 0
    };

    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({ questionsAnswered: this.state.questionsAnswered + 1 });
  }

  render() {
    <div className="lead-mentor-container">
      <h1>Tim Biles</h1>
      <h3>{this.state.questionsAnswered}</h3>
      <h3>questions answered today</h3>
      <button onClick={this.handleClick}>Increase Answers</button>
    </div>;
  }
}
```

Some initial state is being set up in this component for questions answered. Then the handle click method is being bound to each new instance of this component. Whenever the button is clicked, it will invoke the class method and then invoke setState() setting the questionsAnswered to be 1 more than the previous state for questions answered.

### Apply

Try these on your own, but work together if you start to get stuck.

5.  Create a `Student` component that keeps track of the number of questions the student has asked, with a button that adds 1 to the total when it's clicked

```jsx
class Student extends Component {
  constructor() {
    super()
    this.state = {
      questionsAsked: 0,
      question: ''
    }
  }
  incrementQuestions() {
    this.setState({
      questionsAsked: this.state.questionsAsked + 1;
    })
  }

  handleChange = (e) => {
    this.setState({
      question: e.target.value
    })
  }

  render() {
    return(
      <div>
        <h2>{this.state.questionAsked}</h2>
        <input value={this.state.question} onChange={this.handleChange}/>
        <button onClick={this.incrementQuestions}>Ask question</button>
        {this.state.questions.map(q => <div>{q}</div>)}
      </div>
    )
  }
}
```

6.  Now add a text input where the student can type in their questions with a button to add them to a list of questions that is displayed below the number of questions asked.

### Analyze, Evaluate, Create

Discuss these questions as a group

7.  Could your `Student` component be refactored into a functional component? Why or why not?

It could if it got its values from props from the parent component and the parent component was concerned with passing down bound functions and updating state.

8.  What are the pros and cons of using a class method for an event handler vs. using an arrow function inline?

pros

less writing of js code in the render method. You want to keep that as clean as possible since the render is not meant to be cluttered with complex logic.

cons

You need to make sure that the class methods are bound correctly or passed correctly to child components otherwise this won't have the correct value.

9.  The render() method is called every time a component's state is updated. For a text input, that means the render method is called for every keypress. Why isn't this bad for performance?

Because there are two stages to the render being called. The first is that the render for the virtual dom is called, it returns a virtual dom structure of the component. the next step is after the diffing happens on the virtual dom, only the nodes on the actual dom that have changed are updated. So the render method does not repaint every single html element on the view each time it's called, just what was updated.
