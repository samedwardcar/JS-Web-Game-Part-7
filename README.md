# Web Game VII

This is an activity for FSWD Lesson 5.4.6- Practicing Async & Await

Please refer to the Activity Guide in Canvas for directions.


Activity: Web Game Part VII
In this activity, we will add NPCs to our web game just as we did with callback functions and promises in a previous lesson. This time, we will use the async and await keywords to make each walk function asynchronous.

Setup
Instructions:
Click HERE for the link to the repo.
Fork (not clone) it to your OWN GitHub account.
Now to clone the repo to your machine, click the green 'Code' button and then copy the URL.
In a new terminal, or Git Bash, go to where you want to clone the repo.
Type git clone in the terminal or Git Bash, then a space, then paste the URL you copied from your repo. Example:
undefinedClick here to copy
Hit "Enter" or "Return", whichever is on your keyboard.
Now, in your terminal, change to your repository directory (cd repo name)
Open your repository in Visual Studio Code.
Open terminal in your Visual Studio Code.
In your terminal, run npm install to install the required node_modules.
After the install, run npm start in the terminal.
Do the assignment in Visual Studio Code and stage your changes using the git add -A command.
Make at least one commit by using the git commit -m "write your message here" command. Example:
undefinedClick here to copy
Finally, push your changes using the git push command. Example:
undefinedClick here to copy
1) Preparing to Use Async and Await
Open newNonPlayableCharacter.js. On line 26, we define walkEast, a function that makes the character walk from left to right. As with previous activities, we want to update the walkEast function so it accepts a number of milliseconds as a parameter, starts moving the character east, waits the specified number of milliseconds, and then stops the character. We generally use setTimeout to wait a number of milliseconds, but this time we will use await instead. This means we need a promise, not a function that accepts a callback function. In a previous lesson, we saw a sleep function that does just that.

Is sleep built into the browser?

Yes
No
Copy the following code and paste it at the end of newNonPlayableCharacter.js:

undefinedClick here to copy
This only defines a function that wraps setTimeout (a function that accepts a callback) with a function that returns a promise instead. This practice is often used with older JavaScript functions that do not support promises and is commonly referred to as promisifying. (If there is one thing the JavaScript community is good at, it is inventing goofy new words.)

Next, we will review how this sleep function works.

What would the following function do when invoked?

undefinedClick here to copy
Log 'Hello World' and then wait five seconds.
Nothing
Wait five seconds and then log 'Hello World'.
Throw an error.
Would the following function behave any differently than the one above?

undefinedClick here to copy
Yes
No
Now that we have sleep defined and a solid grasp of how it works, we will use it to make changes to walkEast.

2) Add the Ability to Wait for walkEast
Make it asynchronous using the async keyword.
Make it accept time as a parameter.
At the end of the function, invoke sleep and pass it time as an argument.
Use await to pause walkEast until sleep (time) has resolved.
After sleep has resolved, invoke stop to stop the character.
3) Test It
Open index.js. On line 8, invoke npc.walkEast() and pass it 2000 as an argument. Check the result in your browser. It should look something like this:

undefined
Use console.log to inspect the return value of npc.walkEast. What does it return?

A function
A time
A 'Promise' object
A direction
4) Wait for walkEast in index.js
After the character walks east, we now will have it walk south. Wait for npc.walkEast(2000) to finish by putting await in front of it. Next, write npc.walkSouth() on the following line. Return to your browser.

Did it work as expected?

Yes
No
You probably received an error like this:

undefined
This is because you cannot use await outside an async function. The browser cannot pause the main script. That would subvert the whole point of making our logic asynchronous. To fix this problem, wrap your asynchronous logic in an async function and then immediately invoke it:

undefinedClick here to copy
Now, the character should move in an L shape:

undefined
5) Add the Ability to Wait for the Other Directions
Use the same pattern to make walkNorth, walkSouth, and walkWest asynchronous. Be sure to test each method as you complete it, as this is the easiest way to detect and resolve bugs.

6) Implement a Complex Track
Now that all four walking methods have been converted to async functions that accept time as a parameter, we can build a more complex track. Program a path for the NPC using the following directions and durations:

North for 1400 ms
East for 1200 ms
South for 300 ms
East for 1500 ms
South for 1500 ms
West for 2700 ms
North for 400 ms
When you are finished, the NPC should walk all the way around the screen, zigzagging slightly to move around the well, and end up where it started.

7) Reflect
Think back on our journey to the current implementation of an NPC following a programmed track:

A) Synchronous Implementation
When we first tried to move a character on a track, we had no way to express that we wanted to wait for the character to finish going one direction before moving in another direction. As a result, the character only went the last direction that was specified:

undefinedClick here to copy
B) Asynchronous Callback Functions
Our first successful implementation of an NPC following a track used callback functions, but our code became very nested and difficult to read:

undefinedClick here to copy
C) Asynchronous Promises
Using promises, we were able to clean up our code:

undefinedClick here to copy
D) Asynchronous Using Async and Await
Finally, using async and await, we managed to express asynchronous logic that is almost as easy to read as the synchronous logic we started with:

undefinedClick here to copy
Under the hood, async and await rely on promises, which rely on callback functions. Just because each progressive tool in this list is older and lower level does not mean it is no longer relevant. Promises are more flexible than async/await, and callback functions are more flexible than promises. We recommend sticking with async and await for now, as they are the easiest to use. However, in time and with experience, you will learn to choose the best tool for the problem at hand.

Bonus
If you have time, below are some ideas to develop your mastery of async and await:

Loop the track, so once the character finishes, it starts to circle around the screen again.
You may have done this before in a previous lesson, but now that you are using async and await, try utilizing a while loop to implement this behavior.
Read about generator functions in MDN's documentation. The generator function is another block on which async and await are built. While it is uncommon to use the generator function syntax directly, it is a very interesting tool for customizing your functions.
Acceptance Criteria
When opening the game in the browser, the green character walks around the screen on the intended track and returns to its initial position.
When viewing newNonPlayableCharacter.js, function moveNPC() must exist.
When viewing newNonPlayableCharacter.js, function moveNPC() must be an async/await function that moves the character along the intended track.
Before submitting, make sure you do a self review of your code, check for formatting, spelling, include comments in your code, and ensure you have a healthy commit history.

Make sure to submit your github repository link on the submission page.