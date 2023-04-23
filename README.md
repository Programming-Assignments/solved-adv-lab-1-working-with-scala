Download Link: https://assignmentchef.com/product/solved-adv-lab-1-working-with-scala
<br>
<h2>LAB 1<a name="_Toc19067314"></a>: WORKING WITH SCALA</h2>

In this lab you will practice working with Scala from the command line and using an IDE, and practice using some basic Scala syntax. In the university labs Scala is located in the Windows 10 VMware image.

Task 1. Working with the REPL

In order to use the Scala REPL you need to have a Java JDK and Scala installed and your OS environment correctly configured. The environment variable JAVA_HOME should be set to the root directory of the JDK, the PATH environment should include the bin directory of your Scala installation and SCALA_HOME should be set to the root directory of your Scala installation.

Scala should be configured already in a VM on the lab PCs. You can find installation instructions at <a href="https://www.scala-lang.org/download/install.html"><strong>http://www.scala-lang.org/download/install.html</strong></a> if you need to install on your own computer. Scala runs on Windows, MacOS and Linux – the lab PCs run Windows.

<ol>

 <li>Open a system command prompt.</li>

</ol>

Enter the following command:

scala –version

You should see a message confirming the version of Scala that is installed, e.g.

<ol>

 <li>Create a folder where you want to store your working files for this lab and navigate to this in the command window. Enter the command:</li>

</ol>

scala

This should start the Scala REPL. When it is ready you should see a message and a scala&gt; prompt, e.g.

(Note that when you are finished with the REPL and want to quit to the OS command prompt you enter the command :q)

<ol>

 <li>Enter a simple variable declaration statement, e.g.</li>

</ol>

val x = 10

The result of evaluating this should be shown:

x: Int = 10

<ol>

 <li>The REPL shows the result of each expression, but you can also explicitly print to the REPL output. Enter the following:</li>

</ol>

print(x)

<ol>

 <li>Try changing the value of x by entering:</li>

</ol>

x = 20

What happens? Why? How can you make it possible to change the value of a variable?

<ol>

 <li>Declare another variable y with the value 5. Enter an expression that adds x and y. Enter a statement that prints the result of adding x and y.</li>

 <li>Operators in Scala are actually methods. Enter the following expression that adds x and y – the result should be the same as step 6:</li>

</ol>

x.+(y)

<ol>

 <li>Enter the following function definition. This function calculates the nth power of a number, e.g. 2<sup>4</sup> = 16. Note that the REPL allows you to enter multiline statements like this and recognises when the statement is completed:</li>

</ol>

def power(value:Int, power:Int):Int = {

var result = 1

for(i &lt;- 0 to power-1) {

result = result * value

}

result

}

Pay careful attention to the syntax, if you don’t get it right you will have to start again. When you have entered the function definition correctly you should see the result – a function definition is evaluated to a description of the signature of the function:




power: (value: Int, power: Int)Int

<ol>

 <li>Enter an expression that calls the power function, e.g.</li>

</ol>

power(2,4)

Did you get the correct result? Try some more calls to power, with different values. Do you always get the result you expect?

<ol>

 <li>You can define modules (classes/singleton objects) in the REPL. Enter the following definition for a singleton object</li>

</ol>

object HelloWorld{

def main(args: Array[String]) {

println(“Hello ” + args(0))

}

}

Call the main method of the object:

HelloWorld.main(Array(“Jim”))

<ol>

 <li>Exit the REPL using :q to return to the OS command prompt. Keep the command window open.</li>

 <li>Task2. Running scripts and compiling classes</li>

</ol>

The REPL is useful for experimenting interactively with Scala. However, it can be more convenient sometimes to write your Scala code in a file in a text editor, and run it as a script. That way, if you have made an error in your code, you can just edit it and run the script again.

<ol>

 <li>Use a text editor (e.g. Notepad or TextPad) to create a file <em>script1.scala</em> in your working folder.</li>

 <li>In the editor, enter the definition of the power method from Task 1, and some println statements which print the result of calling the function with various values. Save the script file.</li>

 <li>At the command prompt, run the script with the command:</li>

</ol>

scala script1.scala

You should see the output from the print statements in your script. Note this will not work if your command prompt current folder is not the one where your script file was saved.

<ol>

 <li>Create a new file <em>Classes.scala</em> in your working folder and use your text editor to enter the following in that file:</li>

</ol>

class Point(var x: Int, var y: Int) {

def move(dx: Int, dy: Int): Unit = {

x = x + dx

y = y + dy

}

override def toString: String =

“(” + x + “, ” + y + “)”

}




object Classes extends App {

val pt = new Point(1, 2)

println(pt)

pt.move(10, 10)

println(pt)

}

This defines a class called Point that represents a point in 2D space, and a singleton object called Classes with a main method as an entry point to run this as a program. Note that here, the object extends App, which means you don’t have to put code inside a main method.

<ol>

 <li>At the command prompt, compile this code with the following command:</li>

</ol>

scalac Classes.scala

If there are no errors you should see no message – no news is good news!

Look at the contents of your working folder. You should see files <em>Classes.class</em> and Point.class. These are Java class files that have been create by the Scala compiler – Scala is compiled to Java bytecode.

<ol>

 <li>Run this code from the command prompt with the command:</li>

</ol>

scala Classes

Do you see the output you expect? Note that here you are running compiled code, rather than a script, and you need to have code with complete classes rather than fragments of code as you can have in a script.

Task 3. Working with an IDE

Some developers like to work with the command prompt, and it is possible to do so even with large projects, with the help of the <em>sbt</em> build tool, which can be used in this way. Others prefer to use an IDE, which provides many features to help developer productivity. Here, you will look at the IntelliJ IDE from JetBrains. In order to use the IntelliJ for Scala you need to have the Scala plugin installed in the IDE and configured correctly.  IntelliJ should be configured already in the VM on the lab PCs.

<ol>

 <li>Start IntelliJ. You should see a Welcome window which gives you the option to create a new project. Click Create New Project.</li>

 <li>In the New Project window select Scala in the list on the left, and Scala in the main pane, and click Next.</li>

 <li>In the next step, navigate to your working folder and add lab1project to the path name in the Location box. For example, if your folder is c:lab1 your location should be <em>c:lab1lab1project</em>. The project name should then be set automatically to <em>lab1project</em>.  The Project SDK and Scala SDK boxes should be populated already – if not you will have to select the root folder of either or both of the JDK and Scala installation on your machine. Click Finish. Click OK if you get a prompt to create a new directory.</li>

</ol>

The new project should be created, and the project window in IntelliJ should look like this

Scala worksheet

The IDE provides an alternative way to work interactively with code, <u>Scala worksheets</u>. A worksheet allows you to enter Scala expressions and have them evaluated immediately.

<ol>

 <li>Right-click on the project root in the project window and select New &gt; Scala Worksheet from the pop-up menus. Enter the name <em>lab1</em> for the worksheet. It will appear in the project window as <em>lab1.sc</em> (worksheets have the extension .<em>sc</em>) and open in the editor.</li>

 <li>Enter the same simple variable declarations as you did in the REPL in task 1. When you enter an expression it should be evaluated (almost) immediately, and the result display in a separate pane alongside the code. This may take a few moments the first time you enter an expression, and you may have to click the green Evaluate Worksheet button above the code to start with – make sure Interactive mode is checked, and evaluation should happen automatically after that.</li>

</ol>

If the code in the worksheet contains no errors then you should see green ticks in the code pane and above the results pane. If there are errors, these will be indicated. You can go back and edit the code in the worksheet and it will then be evaluated again.




<ol>

 <li>Repeat the remaining exercises that you did in the REPL, this time in the worksheet. When you finish, the worksheet will contain all the code you entered, with all the results shown. This is like a REPL session that you can go back into and re-run and change as you like without having to re-enter code.</li>

</ol>

<ul>

 <li>Enter the power function, and a call to this function</li>

 <li>Enter the HelloWorld object, and a call to its main method. In this case, you should see both the output from the println statement and the return value of the method – what is the return value and type? What does this mean?</li>

</ul>

<h3>Scala classes</h3>




The Scala worksheet is useful for experimenting and learning, but when you are building an application you will instead create <u>Scala classes</u>. These normally go in the project’s <em>src</em> folder. In larger projects they will be organised into packages in the same way as you do with Java.




<ol>

 <li>Right-click on the src folder in the project window and select New &gt; Scala class from the menu. Enter the name Point for the class. It will appear in the project window as Point and open in a new editor tab. Note the icon in the project window which indicates that this is a Scala class.</li>

</ol>




<ol>

 <li>Replace the code in the editor with the code for the Point class that you created in task 2.</li>

</ol>




<ol>

 <li>Create another class in the <em>src</em> folder, with the name Classes. In the Create New Scala class dialog where you enter the name, select Object from the drop-down box instead of Class. Note the icon in the project window which indicates that this is a Scala class.</li>

</ol>




<ol>

 <li>Replace the code in the editor with the code for the Classes singleton object that you created in task 2.</li>

</ol>




<ol>

 <li>The object Classes contains the main method, so you can run it. Note that the main method uses the Point class that you created separately. Right-click on Classes in the project window and select Run ‘Classes’ from the menu. Your code will be compiled and run, and the output will be shown in the output window which is normally below the editor.</li>

</ol>




<ol>

 <li>Running Classes once like this creates a run configuration. Run configurations can be selected, edited and run and debugged from the controls above the editor.</li>

 <li>Task 4. Practicing Scala</li>

</ol>

You have now tried a number of tools of ways of working with Scala. In this task you will now practice writing some Scala expressions yourself. You can use whichever of these tools you prefer to attempt the following exercises. If you choose to use a Scala worksheet you can continue with the same worksheet as in task 3, or start a new one. You should use your lecture notes and references listed under ‘Further reading’ to help you.

<ol>

 <li>Write and test a function called <em>square</em> that takes a parameter of type Double and returns a Double that is the square of the parameter</li>

 <li>Write and test a function called <em>distance</em> that takes parameters x1,y1,x2 and y2, all of type Double as parameters. These represent the coordinates of two points in 2D space (x1,y1) and (x2,y2). Your function should return the distance between these points, using the distance formula:</li>

</ol>

For example, distance(0,0,1,1) should return 1.414 (approximately)

You can make use of your square function in the distance function. You will also need to use Scala’s <em>sqrt</em> function, which is in the <em>scala.math</em> package, so you will need the following statement:

import scala.math.sqrt

<ol start="3">

 <li>Modify your distance function to use default and named parameters so that it can be called with two parameters only, and the distance from (0,0) to that point will be calculated, e.g.</li>

</ol>

distance(x2=1,y2=1)

<ol start="4">

 <li>Write an expression to create an array of integers containing the values 4,7,3,2,6</li>

 <li>Write a function called <em>max</em> that takes an array of integers as a parameter and returns the highest value in the array. Use a for expression and an if expression in your function so that you can practice using these. Note that there are more “functional” ways of doing this computation, which you will see later on in the module.</li>

 <li>Create a new class called <em>Circle</em> with two constructor parameters:</li>

</ol>

<ul>

 <li>center, of type Point (you will need the Point class you created previously)</li>

 <li>radius, of type Integer</li>

</ul>

Add a method called <em>area</em> which returns the area of the circle (πr<sup>2</sup>) as a Double

Add a method <em>toString</em>, similar to the one in Point, that returns the details of the Circle as a string, for example <em>(10,10), radius = 5</em>. Use the Point class as an example to help you.

<ol start="7">

 <li>Test your Circle class by adding the following code to the Classes object you created previously and run it:</li>

</ol>

val circ = new Circle(pt,5)println(circ)println(circ.area)println(circ.radius)circ.radius = 10println(circ)

Note that when you wite circ.radius you are using a getter or setter method created by the compiler – the notation for this is similar to properties in C# rather than getter/setter methods in Java.

What happens if you use each of the following for the radius parameter in your Circle class? Why?

<ul>

 <li>var</li>

 <li>val</li>

 <li>neither var nor val</li>

</ul>