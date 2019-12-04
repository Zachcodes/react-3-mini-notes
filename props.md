### Remember

Answer these on your own, then compare answers as a group

1.  What are props?

Props are key value pairs that are passed down from parent to child in React. These values are treated as read only meaning that the child component should never directly manipulate the values directly. Instead, if they need to cause an update in the parent, they can invoke a function that is passed down from the parent that is bound to the context of the parent.

2.  How do you pass props from a parent to a child?

```jsx
<Test name="hello" hello={someVariable} />
```

3.  How do you access props from a class based child component?

this.props

4.  How do you access props from a functional component?

props parameter passed as the first param.

5.  How do you bind a function to a parent component so that it can be passed to a child?

this.method = this.method.bind(this) in the constructor will create a new bound instance of the class method on the newly created component
Alternatively, you can use the arrow function syntax in the class body definition which will also bind to the created component instance

### Understand

Discuss this question in pairs if you have a 4-person group

6.  What's happening in this component?

```jsx
import React, { Component } from "react";

class Queue extends Component {
  constructor(props) {
    super(props);

    this.state = {
      questions: []
    };

    this.askQuestion = this.askQuestion.bind(this);
    this.answerQuestion = this.answerQuestion.bind(this);
  }
  askQuestion(newQuestion) {
    const questions = [...this.state.questions, newQuestion];
    this.setState({ questions });
  }
  answerQuestion(index) {
    const questions = [...this.state.questions];
    questions.splice(index, 1);
    this.setState({ questions });
  }
  render() {
    <div className="queue-container">
      <h1>The Queue</h1>
      <h3>{this.state.questions.length}</h3>
      <h3>questions need answers</h3>
      <Student askQuestion={this.askQuestion} />
      <Mentor
        answerQuestion={this.answerQuestion}
        //added this to answer question 7
        questions={this.state.questions}
      />
    </div>;
  }
}
```

Constructor is being invoked immediately followed by super(props). This allows access to this and this.props in the constructor. Both class methods are then bound in the constructor so that each new instance of Queue has the bound version of this function as its own property.

The render method then renders our the number of questions in state and a Student and Mentor component. The Student and Mentor component are both passed props whose values are the bound functions on the Queue component.

When either Student or Mentor invokes these functions, they will invoke using Queue as the value of this so these functions will correctly set the state of the Queue component.

### Apply

Try these on your own, but work together if you start to get stuck.

7.  Using the `Queue` component above, create a `Student` component that can add a question as a string and a `Mentor` component that can remove a question from the array.

```jsx
class Student extends Component {
  constructor(props) {
    super(props);
    this.state = {
      question: ""
    };
  }

  handleChange = e => {
    this.setState({
      question: e.target.value
    });
  };

  render() {
    return (
      <div>
        <input value={this.state.question} onChange={this.handleChange} />
        <button onClick={this.props.askQuestion}>Ask Question</button>
      </div>
    );
  }
}
```

```jsx
function Mentor(props) {
  return (
    <div>
      {props.questions.map((q, i) => {
        return (
          <div key={`${q}-${i}`}>
            {q}{" "}
            <button onClick={props.answerQuestion(i)}>Answer question</button>
          </div>
        );
      })}
    </div>
  );
}
```

### Analyze, Evaluate, Create

Discuss these questions as a group

8.  In the Queue component above, why are we holding state in the Queue component instead of Mentor or Student?

Because both Mentor and Student need to be aware of the current value of questions on state.
