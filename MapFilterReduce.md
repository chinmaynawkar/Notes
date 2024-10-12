### Map, Filter, Reduce

### Map: Transforming Every Item
- The map function is like having a **magic paintbrush**. 
- It lets you **transform every item** in an array into something new without changing the original array.

#### Example: Doubling Numbers
Let's say you have an array of numbers:

const numbers = [1, 2, 3, 4, 5];

You want to double each number. Here's how you'd do it with map:
const doubledNumbers = numbers.map((number) => {
  return number * 2;
});

console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
console.log(numbers); // Output: [1, 2, 3, 4, 5] // Original array unchanged

#### Explanation:
1. numbers.map(...): We use the map function on our numbers array.
2. (number) => { ... }: This part is like a mini-function (called an "arrow function") that tells map what to do with each number.
3. return number * 2;: Inside the mini-function, we double the current number and return the result.
4. map takes all these doubled results and creates a brand new array called doubledNumbers.


### Filter: Picking Specific Items
- The filter function is like a **detective**. 
- It helps you **find and keep only the items** in an array that match a certain condition.

#### Example: Finding Even Numbers
Using our numbers array again, let's find only the even numbers:

const evenNumbers = numbers.filter((number) => {
  return number % 2 === 0; 
});

console.log(evenNumbers); // Output: [2, 4]

#### Explanation:
1. numbers.filter(...): We use the filter function on our numbers array.
2. (number) => { ... }: Our mini-function again, this time to check for even numbers.
3. return number % 2 === 0;: This checks if a number is perfectly divisible by 2 (meaning it's even). If it is, it returns true (keep it!), otherwise false (don't keep it!).
4. filter creates a new array called evenNumbers containing only the even numbers.

### Real-World Example 

Imagine you're building a website that shows a list of online friends. You get the data from the server like this:

const friendsData = [
  { name: "Alice", online: true },
  { name: "Bob", online: false },
  { name: "Charlie", online: true },
];

#### Task 1: Display only the names of online friends.

const onlineFriends = friendsData.filter((friend) => {
  return friend.online;
}).map((friend) => {
  return friend.name;
});

console.log(onlineFriends); // Output: ["Alice", "Charlie"]

#### Task 2: Send a notification to each online friend.

friendsData.filter((friend) => {
  return friend.online;
}).forEach((friend) => {
  console.log("Sending notification to", friend.name);
  // Code to actually send the notification would go here
});

In these examples, filter helps us find the online friends, and then we can either map their data to display just the names or perform some action (like sending a notification) for each online friend.

### Reduce: Combining Elements

#### The reduce Function 

- Imagine reduce as a **super-smart robot** that can walk through a list of items, remember things, and combine information in any way you tell it to. 
- It's **incredibly versatile** and can do the job of many other array methods, but it's especially good at taking a bunch of values and combining them into a single result.

#### How reduce Works:
1. It goes through each item in an array, one by one.
2. It carries a "backpack" (called an **accumulator**) where it can store and update information as it goes.
3. For each item, it does something you specify and updates what's in the "backpack".
4. At the end, it gives you what's in the "backpack" as the final result.

#### Basic Structure

const result = array.reduce((accumulator, currentItem) => {
    // Do something with accumulator and currentItem
    return updatedAccumulator;
}, initialValue);

#### Example: Summing Numbers
Let's start with a simple example - adding up all the numbers in an array:

const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((total, number) => {
    return total + number;
}, 0);

console.log(sum); // Output: 15

#### Explanation:
- We start with total (our accumulator) set to 0.
- For each number, we add it to total.
- The final total becomes our sum.