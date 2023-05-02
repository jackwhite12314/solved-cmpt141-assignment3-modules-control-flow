Download Link: https://assignmentchef.com/product/solved-cmpt141-assignment3-modules-control-flow
<br>
<strong>Question 1</strong>

<strong>Purpose: </strong>To practice loops, and looking up and using module functions.

<strong>Degree of Difficulty: </strong>Moderate. There’s a lot of reading here for 7 marks, but most of the coding is pretty easy.

<h1>Intro: Turtle Graphics</h1>

In this question we will introduce you to turtle graphics. A turtle is a cute name for an entity that we can move around a drawing canvas to create pictures. The turtle has a pen which can be in either the up or down positions. When the turtle’s pen is in the down position, the pen draws whenever we move the turtle. We can draw a line by, say, moving the turtle 50 pixels to the right while the pen is down. We can also change the colour of the lines that the turtle draws, and we can even ask the turtle to draw specific shapes, such as a circle. When the pen is up, we can move the turtle without it drawing anything.

We can add turtle graphics to a program by importing the turtle module.t

import turtle as t

Now we can access the turtle module functions though the object . For example, we can tell the turtle to put its pen down, move 50 pixels in the direction it is currently facing (drawing a 50-pixel long line in the

process), and then lift its pen up:

t.down()

t.forward(50)

<table>

 <tbody>

  <tr>

   <td> </td>

  </tr>

 </tbody>

</table>

t.up()

You can also move the turtle to a specific location specified by an (<em>x,y</em>) coordinate: <em>x </em>is the horizontal position, <em>y </em>is the vertical position. The center of the canvas window is (0<em>,</em>0). For example, we could move

the turtle directly to position (20, 20) (down and to the right of the center) by calling: (20<em>,</em>20)  t.goto(20, 20)

If the pen is down, then this will also draw a line from the turtle’s current position to the position                         .

We can tell the turtle to draw lines of a given width (if the pen is down) like this:

t.pensize(3)

The line colour can be changed by calling:r g b       t.pencolor(r, g, b)

where , , and are values between 0 and 1 indicating the red, green, and blue values of the colour, 0.0 being none of that colour component, 1.0 the maximum amount of that colour component. E.g. t.pencolour(1.0, 1.0, 0.0) gives bright yellow (since red + green = yellow).

If you’d like another example, Lecture 6, demo 2 shows a complete program that uses turtle graphics to draw a circle wherever the user clicks the mouse. It uses all of the turtle functions described here.

For this question you will draw some random spirals using turtle graphics.

<strong>Problem Overview: Drawing Spirals</strong>

We will draw spirals as an exercise to draw pictures using turtle graphics.

<h1>How to get started</h1>

We have provided a partially complete Python program to get you started: a3q1-starter.py. You can find it on the Moodle page as a resource for Assignment 3. Download it and add it to your Python project.

The starter file a3q1-starter.py defines a function called draw_spiral() where you’ll add your code to draw a spiral. The rest of the file creates a few variables and determines a few necessary values.

Near the bottom of the file there is a place where you need to create a loop to make the correct number of function calls to draw_spiral(). When you call draw_spiral(segments,size) you will need to pass the arguments indicating the number of segments in the current spiral and the length of the first segment. The first spiral should have 20 segments, and 2nd should have a random number of segments between 20 and 30, and the third should a random number of segments between 20 and 40, and so on. In the draw_spiral() function, there are comments that tells you to write some code to produce a spiral.

<h1>How to colour your spirals</h1>

Each spiral should be drawn with a random color

<strong>Getting random colours </strong>Colours can be described by numbers. Perhaps you’ve learned something about how primary colours combine (red + yellow make orange, etc). One way to do this on a computer is to use numbers between 0 and 1 (this is not the only way). These numbers represent the “amount” of colour you want to combine; zero means none, and 1 means all. We need three such numbers to represent all the colours a computer can use, in terms of how much red, green, and blue to combine. Red is 1,0,0; green is 0,1,0; blue is 0,0,1; black is 0,0,0; white is 1,1,1.

You can set a turtle’s pen-colour using three random numbers. You can ask the random module to return a number between 0 and 1 (inclusive) using its random() function (just to be clear, the module’s name is random, and it contains a function of the same name random()). The number is random in the sense that you cannot predict what it will return, and it will change every time you ask for one. The function randint(A,B) from the random module yields a random integer between A and B (inclusive). The starter code does not import the random module, you’ll have to do that yourself. The documentation for functions in the random module can be <a href="https://docs.python.org/3/library/random.html">found here (click to link)</a><a href="https://docs.python.org/3/library/random.html">.</a>

<h1>Start a spiral at a random location</h1>

Each spiral should begin at a random location with its x coordinate being an integer between -100 and 100, and likewise its y coordinate should be an integer between -100 and 100.

<h1>Drawing a spiral</h1>

You should draw a spiral by drawing a series of line segments one at a time in a loop. For each segment you should select a random pensize between 1 and 6. To draw the first segment you move the turtle forward length units, then turn the turtle to the right by 45 degrees. To draw the 2nd segment, you move the turtle forward 2 × length units, and then turn the turtle to the right by 45 – 1/2 = 44.5 degrees. To draw the ith segment you move the turtle forward length × i units, and then turn the turtle to the right by 45 – (i-1)/2 degrees

<h2>Other Hints</h2>

The documentation for the turtle module containing descriptions of how to use the turtle module functions can be found <a href="https://docs.python.org/3/library/turtle.html#turtle-methods">here (click to link)</a><a href="https://docs.python.org/3/library/turtle.html#turtle-methods">.</a> Click on the name of a function to get more details.

When you run a program that uses turtle graphics, it pops up a canvas window on the screen. This window will often hide behind other windows (such as PyCharm) so if you think nothing is happening when you run your program, make sure you move your windows and look behind them. Also, the program is only terminated when you close the canvas window, so make sure you close the window between runs or you may get confused by having multiple drawing canvases open at the same time.




<strong>Question 2</strong>

<strong>Purpose: </strong>To practice using loops to repeat actions until a condition is met (and solve a practical problem at the same time!).

<strong>Degree of Difficulty: </strong>Easy

A friend of yours has gotten the new “Rocket” credit card. Every dollar purchased gets you 1000 meters towards a free one-way trip to the planet Venus! To attract customers the card offers a novel interest rate. For each month in debt, the percentage owed in interest increases by a power of 2. For example, after 1 month, the interest owed is equal to 2% (2<sup>1</sup>) of the <strong>original </strong>debt. After 2 months, the interest is 4% (2<sup>2</sup>) of the <strong>original </strong>debt and so on. In general:

<em>interest</em>(<em>m</em>) = <em>d </em>×(2<em><sup>m</sup>/</em>100)

Note: This formula is not a Python assignment statement! It is an equation that says that if you know the quantities <em>m </em>(the number of months) and <em>d </em>(the original debt), you can calculate a value using the right side of the equation, giving you a quantity that tells you the the total interest after <em>m </em>months.

Write a program which does the following:

<ul>

 <li>Prompt the user to enter an initial amount of Rocket credit card debt. You must make sure that the user enters a positive number. If they do not enter a positive number, print a message informing them so, and prompt them to enter the initial amount of debt again. Keep doing this until they enter a positive number.</li>

 <li>Starting from month 1, print to the console the total payment owed at 1-month intervals. Thus, for month 1, month 2, etc., you should print out the total payment owing, which consists of the interest <strong>plus </strong>the original debt. Your program should stop after the first month where the total payment owing is greater than <strong>100 times </strong>the original debt (that’s the point at which the credit company calls in its debts, whether you like it or not!).</li>

</ul>

Don’t forget to import the math module if you need math functions. Using the math module is not required and there are correct solutions that don’t use it.

Hint: A correct solution should make use of two separate while-loops.

<h2>Sample Run</h2>

<table width="652">

 <tbody>

  <tr>

   <td width="652">Enter amount of debt in dollars: -7Error! Debt must be a positive number!Enter amount of debt in dollars: 1 After 1 months, you owe: $1.02After 2 months, you owe: $1.04After 3 months, you owe: $1.08After 4 months, you owe: $1.16After 5 months, you owe: $1.32After 6 months, you owe: $1.6400000000000001After 7 months, you owe: $2.2800000000000002After 8 months, you owe: $3.56After 9 months, you owe: $6.12After 10 months, you owe: $11.24After 11 months, you owe: $21.48After 12 months, you owe: $41.96After 13 months, you owe: $82.92 After 14 months, you owe: $164.84 Time to pay up!</td>

  </tr>

 </tbody>

</table>

Sample input and output (input typed by the user is shown in green text):




<h2>Testing</h2>

Test your program first using <em>d </em>= 1, and then using two more inputs of your choice — these should be unique to you and unlikely to be chosen by two different students. Make sure to look closely at the results and do a few calculations by hand to convince yourself that your program is correct! Copy the console output of your three test runs to a document, and hand it in with your program code (see below).

<strong>Question 3 :</strong>

<strong>Purpose: </strong>To practice using modules. Practice with mixing loops and conditionals.

<strong>Degree of Difficulty: </strong>Moderate.

A video game developer is ready to publish their new game, Meteors II (sequel to their breakout hit Meteors). In addition to the regular edition, the developers want to offer a special edition of the game containing extra goodies (e.g. squishy meteor plushies!). They are trying to set the selling price of the game’s special edition, and determine how many copies of it they should make.

Suppose the number of units the publisher can manufacture is determined by the <em>supply </em>function <em>S</em>(<em>P</em>) if they sell the game for price <em>P </em>:

<h2><em>S</em>(<em>P</em>) = 500+90<em>P</em></h2>

Suppose the number of copies they expect to sell is determined by the <em>demand </em>function <em>D</em>(<em>P</em>) if they set the selling price as <em>P </em>:

<h2><em>D</em>(<em>P</em>) = 10000−35<em>P</em></h2>

If the game is priced lower than the optimal price then they would not make enough copies for the number of fans who want to buy the special edition of the game (demand would exceed supply) and lose out on potential sales. If they were to set the selling price of the game higher than the optimal price, then they would saturate the market with too many copies of the game (supply would exceed demand) and might fail to make a profit.

This means that the optimal price for the company to sell the special edition for is the price at which the number of copies produced by the publisher is the same amount as the number of copies demanded by the consumers, that is, the price at which supply equals demand:

<h2><em>S</em>(<em>P</em>) = <em>D</em>(<em>P</em>)</h2>

In economics, this optimal selling price is known as the <em>equilibrium price</em>.

Since the functions <em>S</em>(<em>P</em>) and <em>D</em>(<em>P</em>) given above are quite simple, we could set the two expressions equal to each other and solve for <em>P </em>using Grade 10 algebra. But supply and demand functions are not always so simple, and for more complicated functions, it might be hard to solve for <em>P </em>using algebra.

A very handy way to solve problems requiring complicated algebra is to write a Python program to find the optimal value for <em>P numerically</em>, that is, by searching for a numeric value of <em>P </em>that makes <em>S</em>(<em>P</em>) equal to <em>D</em>(<em>P</em>). Solving complex algebraic problems numerically is a common problem solving paradigm in computer science. In fact, numerical calculations like this dominated the early use of computers in the dark ages before computers had screens.

Here’s a guide for getting this program working. You should try your program out every time you reach a point where you’ve accomplished one of the items in the list. Don’t wait to the end to try it out. This should be a very gradual process of getting something working, then moving on to the next part.

<ul>

 <li>Write a function called supply() with parameter <em>P </em>, returning the value of <em>S</em>(<em>P</em>), as above. Document it with a docstring.</li>

 <li>Write a function called demand() with parameter <em>P </em>, returning the value of <em>D</em>(<em>P</em>), as above. Document it with a docstring.</li>

 <li>Print the three columns (<em>p</em>, <em>S</em>(<em>p</em>), and <em>D</em>(<em>p</em>)) in the console. Do this using a for-loop, for each price <em>p </em>between $10 and $160 at intervals of $1. Start a new line for each new <em>p</em>.</li>

 <li>Add an if-statement to your for-loop from part (c) that you will use to remember the price <em>p </em>for which <em>S</em>(<em>p</em>) = <em>D</em>(<em>p</em>). After the loop is finished, have your program print the optimal price. Make sure you check that the price is indeed the right price!</li>

 <li>Now we’re going to make modifications to your program so that it displays a nice graph instead of a table of numbers. The first step will be to add a line of code at the top of your program to import matplotlib.pyplot. Nothing that follows in this list will work if you skip this step!</li>

 <li>Call the figure() function of matplotlib.pyplot to prepare Python for the creation of a new figure. This function should be called before computing any of the data you want to plot. It has no actions you can see, but if you don’t call this function, none of the remaining steps will work!</li>

 <li>Call the function show() of matplotlib.pyplot, near the end of your program. This function will display all the stuff that gets plotted since the call to figure(). Since we haven’t plotted any data yet, if you run the program, Python will pop-up a window that is mostly empty. While this window is on the screen, your program is still running; so, to allow your program to finish normally, close this window when you are done admiring it.</li>

 <li>In the for-loop that creates the table of data, call the plot() function from matplotlib.pyplot to put the data into the graph. Call plot() once to plot the point (<em>p,S</em>(<em>p</em>)) and again to plot the point (<em>p,D</em>(<em>p</em>)). The plot() function has three parameters in this order: the x-coordinate of the point to plot (price), the y-coordinate of the point to plot (quantity), and a <em>style string</em>. Use the style string literal ’og’ (’g’ meaning green, ’o’ meaning circles) when plotting the supply value, and ’ob’ (’b’ meaning blue, ’o’ meaning circles) for the demand value. When you get this going, you can delete the line of code that displayed the data in tabular form. It was only useful as a stepping point to our graph!</li>

 <li>Change the if-statement in the loop so that in addition to printing the optimal price, it plots the point (<em>p,S</em>(<em>p</em>)) for the optimal price <em>p</em>. Use the style string ’ro’ so that the point is a red circles (the order of the characters is irrelevant, so you could use ’or’ too).</li>

 <li>Now, make your graph look nicer. Look up the xlim() and ylim() functions from the matplotlib.pyplot module. Use them to set the minimum and maximum values on the x-axis of your figure to be between 0 and 170, and the y-axis values to be between 0 and 16000, as in the sample output figure below.</li>

 <li>Look up the xlabel(), ylabel(), and title() functions from the matplotlib.pyplot module. Use them to add a plot title and labels to the x- and y-axes as in the sample output figure below.</li>

 <li>Look up the annotate() function from the matplotlib.pyplot module. Use it to label the point (optimal_price, supply(optimal_price)) with the string “Optimal Price” as in the sample output figure below.</li>

 <li>Be sure that the optimal price and the quantity to be produced at that price (i.e. the value of supply(optimal_price)) is still displayed on the console. This is the solution to the problem we set out to solve! <strong>pyplot</strong></li>

</ul>

Documentation for matplotlib.pyplot is available at <a href="https://matplotlib.org/api/pyplot_api.html">http://matplotlib.org/api/pyplot_api.html</a><a href="https://matplotlib.org/api/pyplot_api.html">.</a> You can find information on how to use xlim(), ylim(), annotate(), xlabel(), ylabel(), and title() there.

<strong>Sample Output </strong>Your console output should look something like this:

The optimal selling price of $76 will result in the sale of 7340 units.

Your graph should look more or less like this:

Price of Special Edition VS Quantity Produced

Side Note: A Word of Caution about Solving Equations Numerically

We have carefully crafted the supply() and demand() functions so that an integer value of <em>P </em>is the optimal price. In general, numerical solutions use floating-point values, and determining whether two floatingpoint values are equal requires more care, because of the limited precision of floating-point numbers. If we aren’t careful, a program can fail to discover when two numbers are equal (for all intents and purposes), because of tiny errors in their calculation. In such situations, instead of equality, we check if two numbers are “close enough.” But you don’t worry about that for this question.