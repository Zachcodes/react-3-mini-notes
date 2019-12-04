### Remember

Answer these on your own, then compare answers as a group

1.  What is React?

React is a JavaScript library. It utilizes component based architecture and a virtual dom. It can be implemented into an existing web page incrementally or used to build an app from the ground up.

2.  What is create-react-app?

create-react-app is a cli tool designed by the engineering team at facebook to allow for quick configuration of a react project. This saves developers time in configuring webpack, hot reload and ensuring that all of the necessary packages are downloaded.

3.  What is Component Based Architecture?

It's when reusable bits of code known as components are all used together to build an application. Component based architecture is tree shaped and data always flows down the tree, not up.

4.  What is JSX?

JSX stands for JavaScript XML and is a syntax extension for JavaScript. It's closer to JavaScript than HTML and so things like props are camel cased. Example being className instead of the html attribute class. It allows us to write HTML and JavaScript all in the same place instaed of moving our JavaScript into an external file and bringing it in under the script tag.

5.  What is the virtual DOM?

The virtual dom is an abstraction of the DOM. The DOM holds an object in memory for every single html node on the screen. It contains all of the properties, classes, styles e.t.c for every single node. Every time the dom is changed, it causes the screen to be repainted. This takes a lot of processing power and time.

The virtual dom is much quicker because it doesn't need to repaint the screen. Whenever a component is rendered or rerendered every single dom object in the virtual dom is rebuilt. This is extremely quick because it's all in memory. Then, once the rebuild is complete, the new virtual dom is compared to a snapshot of the virtual dom from right before the update. In a process called diffing the virtual dom determines what dom objects have actually changed. Then it goes and updates those objects on the actual dom and only those objects which causes the screen to be redrawn for only those html elements.

6.  What is unidirectional (one-way) data flow?

It means two things. The first is that data can only flow from parent to child component. It can never flow from child to parent. Second is that the view fires off actions, which cause the state of a component to change, which then lets the view know of the updated state and it's reflected to show that change. This is different from an mvc framework like angular that allows for the model to update the view and the view to also update the model.

### Understand

Discuss these questions in pairs if you have a 4-person group

7.  Summarize what happens when you run `create-react-app my-app`

node modules are installed, babel is configured, package.json file is written, public folder is created with the index.html, and the src folder is created that contains all of the boilerplate react set up.

8.  Explain what this code does:

```jsx
import React from "react";

const Mentor = props => (
  <div className="mentor-container">
    <h1 className={props.title === "Lead Mentor" ? "lead" : ""}>Tim Biles</h1>
    <ul>
      <li>Fort Worth, TX</li>
      <li>My email address is timbilestimbiles@gmail.com</li>
    </ul>
  </div>
);

export default Mentor;
```

This is a presentational or stateless component that takes in props, then displays the name of a mentor, their address and their email address. Based on the title property on the prop object, the className will be dynamically chosen.

9.  Explain how data is passed from a parent component to a child component.

When a child component is rendered out in the render method or returned from a functional component, key value pairs can be placed on the tag of the component that will be mapped as props to the child component.

### Apply

Try these on your own, but work together if you start to get stuck.

10. Use `create-react-app` to create a new React application called `student-directory`

11. Use the code from `Mentor` above to create a new functional, stateless component called `User` with a list of friends. Hard code the list of friends, do not use state or props.

### Analyze, Evaluate, Create

Discuss these questions as a group

12. What are the benefits and drawbacks of using a tool like create-react-app?

Pros

Little to no configuration from the developer. Saves initial set up.

Cons

Developer probably has no idea what is happening in the config files of the project. No ability to control what is installed and what version etc. May bring in unnecessary modules inflating the size of the project.

13. Compare and contrast JSX with other templating options, such as those used in Angular or Vue

JSX is very easy to read if you know HTML and JavaScript. That can make it a friendly option to pick up for new devs where you need a bit more understanding of how Angular actually works to understand all the ng stuff. Vue also reads fairly easily and it can be nice to have it all split in one file.

14. Compare and contrast one-way data flow with two-way data binding.

One way data flow is less error prone because you know the exact source of the data. It's also easier to debug as you know where to look for changes to the data.

One way data binding can require a bit more work from the developer to ensure the correct values are being updated compared to something like angular that does a lot of work for you using models
