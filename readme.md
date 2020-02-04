# Choose your own Adventure

An introduction to coding.

## Languages

* HTML
* Javascript
* css

## Tutorial

### Plan

#### Product overview

Choose your adventure stories follow a decision tree. Each "Page" in the book represents a node on the tree. Each node should have a few attributes:

* The narration of the story at that node (page)
* The text that represents taking choice 1
* The test that represents taking choice 2

:white_check_mark: Take time to draw your story tree and annotate with these items.

See this tree, for example:

#### Interactions

It's important to keep in mind what actions your user will be able to take. Take time to describe in words how the user should be able to interact and what should happen when the user interacts.

:white_check_mark: Think through the entire product (from beginning to end) and document all interactions and the way the product should change / respond based on those interactions.

### Set up HTML / CSS / Javascript

#### Background

We'll use three languages to create our story:

* HTML -- Creates elements on the web page like text boxes, buttons, links etc.
* CSS -- Controls the styling of elements on the page like color, font size, etc.
* Javascript -- Controls the interactions on the page like clicking a button or changing the text that is displayed

To start, let's use a free tool that makes it easy to work with these three languages:

#### Setup

:white_check_mark: Go to [codepen.io](https://codepen.io/) and click to create a new "pen". This sets you up in a coding environment where you can write the three languages we'll use. The screen will reflect in real time the interface that you're creating.

To start, let's add three simple components in our HTML section like this:

```
<h1>
  My title goes here
</h1>
<Button>
  Click on option 1
</Button>
<Button>
  Click on option 2
</Button>
```

You should see the three elements appear on the web pay you are creating.

`h1` stands for "Heading 1". What happens if you change it to `h2` or `h6`?

#### Basic styling

Let's add some basic styling to our buttons. HTML elements come with basic styling out of the box (you'll notice buttons kind of look like buttons and when we changed the `h1` to `h2`, the font size adjusted).

Many times, we want to provide our own style "overrides" to make the site look the way we want.

Styling is written in css. With css you can "target" certain elements where you'd like to have your style applied.

You can target elements using one of these three methods:
* Target the `type` of element (ex: `<Button>`, `<h1>`, etc.)
* Target the `id` of the element. An `id` is an attribute you can add to an element that is unique. Only one element on a page should have this `id`
* Target a `class`. A `class` is a name you can assign to an element and re-use across many elements for shared styles.

:white_check_mark: Adjust your html as follows:

```
<h1 class="green-text">
  My title goes here
</h1>
<Button id="button1" class="green-text">
  Click on option 1
</Button>
<Button id="button2">
  Click on option 2
</Button>
```

:white_check_mark: Add the following css code in the css section:

```
button {
    padding: 20px;
}
#button1 {
    background-color: blue;
}
#button2 {
    background-color: green;
}
.green-text {
    color: green;
}

```

:white_check_mark: Take a look at the `css` code and see if you can identify the syntax used for targeting a:
* Element type
* id
* class

:white_check_mark: Look at each element (our `h1` and two `Button`s) and determine which styles are present and why.

### Capture interactions

Cool, we've got a site with some text and some buttons, but the buttons don't do anything :sob:.

Enter, Javascript.

Javascript powers interactions on sites. With javascript, you can write `functions`. Functions are re-usable pieces of code that do a specific thing.

#### Practice javscript function
Here is an example of a function you could write:

```
function addOne(inputNumber) {
    return inputNumber + 1
}
```
If I input a number to this function, it will return the number plus one.

For example:
```
addOne(3)
```
This will give you 4.

:white_check_mark: Give this addition function a try in the `JS` part of your work space. First, past the function definition. Then, execute the function, passing in an integer, as shown above.

Cool, your function ran... but you didn't see anything. That is because javascript doesn't by default display anything on the screen. If you want to to display, you have to tell it to.

When coding you also have another place you can output information called the `console`. To have information show up in the console, you need to wrap it in a function called `console.log()`.

:white_check_mark: Pop open the console. Replace the function execution in your javascript code with:
```
console.log(addOne(3))
```
What do you see in the console? Is it working? Change the input number and see what happens. Change the `+ 1` in the function and see what happens.

#### Javascript function to handle button click

Now you've got the tools you need to handle an interaction like a button click.

First, let's write a function that we want to execute when the button is clicked. An easy starting point is:

```
function onButtonClick() {
    console.log('Clicked!')
}
```

:white_check_mark: Replace your javascript code with this function. What happens when you click the button?

You probably noticed that nothing happens still when you click the button. It's because we also need to tell the `Button` element that we want it to execute this function when it receives a click event.

:white_check_mark: Adjust your `Button`s to that they have this attribute: `onClick="onButtonClick()"`

Your buttons will look like this afterward:

```
<Button onClick="onButtonClick()" id="button1" class="green-text">
  Click on option 1
</Button>
<Button onClick="onButtonClick()" id="button2">
  Click on option 2
</Button>
```

Click the buttons, what happens in the console?

#### Identify the button click

Let's make the fuction do something more useful when it's clicked. As part of our plan we know that we will need to change text when a button is clicked. We also need to know which button is clicked, so that we can take the reader down the correct story path.

Let's clarify which button is being clicked first.

Javascript functions can accept `arguments`. These are variables (like you'd use in algebra) that you can pass into the function. The variables give the function information it needs to perform it's job.

In this case, we can pass a variable to our function that tells it which button has been pressed.

We need to make two small changes:
* Set up the function to accept an argument
* Set up the button to send an argument when the button is pressed

:white_check_mark: Adjust your HTML and Javascript as follows:
* `onButtonClick()` in the `Button` element becomes `onButtonClick(1)` for button 1, and `onButtonClick(2)` for button 2
* `function onButtonClick() {` becomes `function onButtonClick(buttonType) {`

I suggest also adding a `console.log(buttonType)` in the body of the function so you can make sure things work properly.

#### Change text on button click

Now we need to change the text when a button is clicked. According to our plan, we'll need to update the following when a button is clicked:
* Story text
* Button 1 text
* Button 2 text

Changing text has two steps:
1) Locate the element that contains the text you want to change
2) Update the text value for that element

To locate an element, we can use the element type, class, or id as we did with css. In this case, we want to be very specific about which element we target and we want to only target one element at a time. `id` is best for this since `id`s should be unique across a web page.

:white_check_mark: Adjust your `onButtonClick` method to look like this:

```
function onButtonClick(buttonType) {
  var element = document.getElementById('button1')
  element.innerText = 'Test Text'
}
```

What do you expect will happen when you click a button? Why does it only change the text of the first button?

Let's set up our function to update all the text we need it to when a button is clicked.

We need to set our function up to do different things based on which button is clicked. This invoves `if` logic.

if logic generally takes this form:
```
if (something is true) {
    then do something
} else {
    do something else
}
```

In our case, for example, it will look something like this:
```
function onButtonClick(buttonType) {
  if (buttonType === 'a') {

  } else {

  }
}
```

The triple equals sign means equality, as in this should be true only if the values on either side of the equals are the same.

:white_check_mark: Use your knowledge of how to update text on the screen to fill in the things that should happen in the if logic. **Hint: You'll need to add an `id` to the `h1`.


### Create re-usable configurations & build tree

Now we've got one page working for our apps. But how do we move to the next page?

Ideally we can re-use the code we have already written and just fill in different text ("strings") as needed depending on which node we're at in the decision tree you designed at the first step.

A smart way to do this is to define a repeatable configuration object that follows the same pattern. We can call each of these objects a page, or node in the tree.

#### Object background

First we should decide what the object will look like for page one. In Javascript, objects are created by using squigly brackets. The data inside an object is a series of key, value pairs. A key is generally a standard name for the value.

For example, if you had objects to represent pets, they may look like this:

```
var pet1 = {
    name: "Fido",
    goodRating: "Good boy",
    age: 1,
}

var pet2 = {
    name: "Sanchez",
    goodRating: "Goodest boy",
    age: 1.5,
}
```

The keys are `name`, `goodRating`, and `age`. The values are the actual details to apply to the specific pet you are modeling with the object.

If you want to access a value from an object, you can do so using `.` (dot) or `[]` bracket notation.

:white_check_mark: Paste the two pet definitions into your javascript section. Then add `console.log` statements for the following ways to access the information:
* `pet1.name`
* `pet1['name']`

Any difference between the two? Nope. Can you access the other information on the objects?

#### Define a base object format

Let's define a base object format that we can use to model the pages of our story. We want it to be reusable and contain all the information we need to power our page (text to display, action to do on click, etc.)

Here is a structure that should work:

```
var pancake = {}
var salmon = {}

var beginning = {
    "story": "Jeff found himself in front of a spread of amazing breakfast foods.",
    "optionAText": "Eat the Pancake",
    "optionBText": "Eat the smoked salmon",
    "optionANextCase": pancake,
    "optionBNextCase": salmon,
}
```

See if you can figure out the purpose of each of the keys. What does `pancake` refer to when it is referenced as the value for `"optionANextCase":`?

In that instance, `pancake` is a variable that represents the empty object defined above. If you fill information there in the same format, it will become the next page of the book when a user pushes button 1.

:white_check_mark: Build your tree according to your plans. You should have an object for each page. The final pages will not have `optionANextCase` or `optionBNextCase` sine there is not a page to follow them.

My finished story looks like this:

```
var creepyHouse = {
  "story": "Jeff got eaten by a robot.",
}

var salmonella = {
  "story": "Jeff got salmonella and died.",
}

var iceCream = {
  "story": "Jeff is lactos intolerant. Yummy ice cream, need to wash his pants.",
}

var happy = {
  "story": "Jeff lived hapilly ever after"
}

var run = {
  "story": "The pancake was delicious. Jeff then went for a long run in the woods",
  "optionAText": "Take some Tums",
  "optionBText": "Throw up and go eat the pancakes",
  "optionANextCase": salmon,
  "optionBNextCase": happy,
}

var salmon = {
  "story": "The salmon gave him an upset stomach",
  "optionAText": "Take some Tums",
  "optionBText": "Throw up and go eat the pancakes",
  "optionANextCase": salmonella,
  "optionBNextCase": happy,
}

var pancake = {
  "story": "The pancake was delicious. Jeff then went for a long run in the woods",
  "optionAText": "Run past the creepy house",
  "optionBText": "Run to the ice cream store",
  "optionANextCase": creepyHouse,
  "optionBNextCase": iceCream,
}

var beginning = {
  "story": "Jeff found himself in front of a spread of amazing breakfast foods.",
  "optionAText": "Eat the Pancake",
  "optionBText": "Eat the smoked salmon",
  "optionANextCase": pancake,
  "optionBNextCase": salmon,
}
```

### Use configurations to power page state changes

Now that we have our configurations, let's hook them up to our code so that the correct thing happens when we push buttons.

First, we need to define a variable that will track the current state of the book (what page are we on?). Let's call it `currentPage`.

You can define it right after all of your object definitions (you'll want those at the top, by the way, and your button logic at the bottom).

To define it, set you first page as the variable like this:

```
var currentPage = beginning
```

Now, we need to make sure two things happen:
1) The correct text is set when the page loads
2) The correct text is updated when a button is clicked

For ease, I recommend just changing the text in your html `h1` and `Button`s to match the text in the first page of your story. Then we'll just need to worry about what happens on click

You've already got the function all set up. What you need to add is:
* Override the `currentPage` variable to be the next case option from the `currentPage`. Think of this like you are turning the page and setting the new config as the current page.
* Set all the text on the page to match what is specified in the now `currentPage`


After doing this, you'll notice that on the last page, we're still showing buttons. We'll handle that next.

### Hide buttons


### Prepare to publish

### Publish