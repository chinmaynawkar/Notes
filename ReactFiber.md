# React Fiber Learning Notes

## What is reconciliation?

**Reconciliation**: The algorithm React uses to diff one tree with another to determine which parts need to be changed.

**Update**: A change in the data used to render a React app. Usually the result of `setState`. Eventually results in a re-render.

## What is React Fiber?

React Fiber is a reimplementation of React's core algorithm for rendering and updating user interfaces. 

Think of it as a new engine inside React that helps it handle complex updates and renderings more efficiently. 

It's designed to make apps smoother, especially when dealing with animations, gestures, and complex layouts.

## Why Was React Fiber Introduced?

As web applications became more interactive and feature-rich, the need for React to handle updates more efficiently grew. React Fiber was introduced to:

- **Improve Performance**: By breaking down rendering work into smaller chunks, React can spread this work over multiple frames, preventing the UI from freezing.

- **Enable Prioritized Updates**: Not all updates are equally important. React Fiber allows the system to prioritize certain updates (like user input) over others (like data fetching).

- **Support New Features**: Laying the groundwork for advanced features like concurrency (handling multiple tasks at once) and error boundaries (catching errors in components).

### The key points are:

- In a UI, it's not necessary for every update to be applied immediately; in fact, doing so can be wasteful, causing frames to drop and degrading the user experience.

- Different types of updates have different priorities — an animation update needs to complete more quickly than, say, an update from a data store.

- A push-based approach requires the app (you, the programmer) to decide how to schedule work. A pull-based approach allows the framework (React) to be smart and make those decisions for you.

## Key Concepts of React Fiber

### 1. Breaking Work into Units
Imagine you have a big homework assignment. Instead of doing it all in one sitting, you break it down into smaller tasks and tackle them one at a time.

**In React Fiber**: The rendering work is divided into small units called fibers. This allows React to pause and resume work, making the app more responsive.

### 2. Scheduling and Priorities
If you have to choose between studying for a test tomorrow or cleaning your room, you'd prioritize studying because it's more urgent.

**In React Fiber**: React can assign priorities to different updates. User interactions might be high priority, while background data fetching might be lower priority.

### 3. Incremental Rendering

When loading a web page, you might see content appear piece by piece rather than all at once.

**In React Fiber**: Instead of rendering the entire UI in one go, React can render parts of it incrementally, improving load times and responsiveness.

### 4. Error Handling

If you're playing a game and make a mistake, you might restart the level.

**In React Fiber**: If a part of the UI fails to render, React can mark that part as incomplete and try again later.

## How Does React Fiber Work?

### Custom Call Stack
- **Call Stack Basics**: In programming, a call stack keeps track of function calls. When a function is called, it's added to the stack, and when it finishes, it's removed.

- **React Fiber's Approach**: React Fiber creates its own version of the call stack using fiber nodes, which are JavaScript objects representing units of work.

- **Benefit**: This custom stack allows React to pause, resume, or prioritize work, which isn't possible with the regular JavaScript call stack.

### Fiber Nodes Structure

Each fiber node contains information about: 
- **Component Type**: What kind of component is it? (e.g., a function, a class, a DOM element)
- **Props and State**: The inputs to the component.
- **References to Other Fibers**: Pointers to child, sibling, and parent fibers, forming a tree structure.

## Real-World Coding Example

### Building a Chat Application

**Scenario**: You're creating a chat app where messages appear in real-time, and users can scroll through previous messages.

**Challenge**: New messages need to appear instantly, but loading older messages (when the user scrolls up) can be less urgent.

#### Without React Fiber

The entire chat window might re-render when new messages arrive, causing lag, especially on slower devices.

#### With React Fiber

- **Prioritized Updates**: React Fiber can prioritize rendering new messages (high priority) over loading older messages (low priority).

- **Smooth Scrolling**: If the user is scrolling, React can prioritize the rendering of visible messages to keep the interface responsive.

- **Paused Work**: React can pause the loading of older messages if a higher priority task comes in (like a new incoming message).

## Benefits of React Fiber

### 1. Improved User Experience
**Smooth Animations and Transitions**: By handling updates more efficiently, animations don't stutter, and transitions appear seamless.

### 2. Better Resource Management
**Avoiding UI Freezes**: Large updates can be broken down, preventing the app from freezing during heavy computations.

### 3. Enhanced Control Over Updates
**Developers Can Optimize**: With Fiber, developers have more tools to optimize how and when components update.

## Key Takeaways
- React Fiber is like a new engine for React, making it better at handling complex and high-priority updates.

- It introduces scheduling, allowing React to prioritize important updates and pause less critical ones.

- By breaking down tasks, React can keep apps responsive and smooth, even as they grow in complexity.
