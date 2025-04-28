# cs108-homework-3-solved
**TO GET THIS SOLUTION VISIT:** [CS108 Homework 3 Solved](https://www.ankitcodinghub.com/product/cs108-stanford-2/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;115586&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS108 Homework 3 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
Part A – Sudoku

For this part of the project, you will build code to solve Sudoku puzzles. Our approach will concentrate on OOP and API design, and give us a chance to start doing some GUI coding. You do not need to be good at Sudoku to build this code. I’m quite slow at them. In fact, this whole project is perhaps cheap revenge against the Sudoku puzzles I’ve struggled with.

Sudoku is a puzzle where you fill numbers into a grid. The history is that it originated in the Dell puzzle magazine in the 1970’s, and later became very popular in Japan, possibly filling the niche that crossword puzzles play in English newspapers, as the Japanese language is not suited to crossword puzzles. Sometime around 2005 it because a worldwide sensation. (See the Wikipedia page for the full story.)

The Sudoku rules are: fill the empty squares in the 9×9 grid so that each square contains a number in the range 1..9. In each row and each column across the grid, the numbers 1..9 much appear just once (“Sudoku” translating roughly as “single”). Likewise, each of the nine 3×3 squares that make up the grid must contain the just numbers 1..9.

Here is an easy Sudoku puzzle. I can solve this one in about 5 minutes. Look at the topmost row. It is only missing 1 and 7. Looking down the columns, you can figure out where the 1 and 7 go in that row. Proceed in that way, looking at rows, columns, and 3×3 squares that are mostly filled in, gradually figuring out the empty squares. A common technique is to write the numbers that might go in a square in small letters at the top of the square, and write in a big number when it’s really figured out. Solve this puzzle to get a feel for how the game works (the solution is shown on the next page).

Sudoku Strategy

There are many ways to solve Sudoku. We will use the following approach which is a sort of OOP interpretation of classic recursive backtracking search. Call each square in the puzzle a “spot”. We want to do a recursive backtracking search for a solution, assigning numbers to spots to find a combination that works. (If you are rusty with recursion, see the practice recursion problems at javabat.com).

• When assigning a number to a spot, never assign a number that, at that moment, conflicts with the spot’s row, column, or square. We are up-front careful about assigning legal numbers to a spot, rather than assigning any number 1..9 and finding the problem later in the recursion. Assume that the initial grid is all legal, and make only legal spot assignments thereafter.

• There are 81 spots in the game. You could try making assignments to the blank spots in any order. However, for our solution, first sort the spots into order by the size of their set of assignable numbers, with the smallest set (most constrained) spots first. Follow that order in the recursive search, assigning the most constrained spots first. Do not re-sort the spots during the search. It works well enough to just sort once at the start and then keep that ordering. The sorting is just a heuristic, but it’s easy and effective.

• We will set a max number of solutions of 100 — if the recursive search gets to a point where it has 100 or more solutions, it can stop looking and just return how many have been found so far.

Sudoku OOP Design

For this project, the starter code has some routine code and data, and the rest of the design is up to you. Your goal is to design classes and APIs so that the solve() method (below) is clean expression of the strategy described above, and the main() and GUI clients are clean.

We will take an OOP approach to the search by treating each spot as its own capable little object. Create a

Sudoku class that encapsulates a Sudoku game and give it a “Spot” inner class that represents a single spot in the game. Constant factor efficiency is not a big concern — we’re going for correctness, clarity, and a reasonably smart strategy.

Concentrate on OOP design around the Spot class — push complexity into the Spot, making things easy for clients of the Spot. For example, the Spot has its own access to the grid (remember, it’s an inner class of Sudoku). Consider these two examples of client code:

// Bad

grid[spot.getRow()][spot.getCol()] = 6;

// Good spot.set(6);

• Sudoku(String text) — takes in puzzle in text form — 81 numbers. (Starter file provides some parsing code.)

• String toString() — override toString() to return a String made of 9 lines that shows the rows of the grid, with each number preceded by a space (use the StringBuilder class which replaces the old StringBuffer). (Essentially, the reverse of the text constructor.) For example, here is the toString() of the “medium 5 3” puzzle…

5 3 0 0 7 0 0 0 0

6 0 0 1 9 5 0 0 0

0 9 8 0 0 0 0 6 0

8 0 0 0 6 0 0 0 3

4 0 0 8 0 3 0 0 1

7 0 0 0 2 0 0 0 6

0 6 0 0 0 0 2 8 0

0 0 0 4 1 9 0 0 5

0 0 0 0 8 0 0 7 9

• int solve() — tries to solve the puzzle using the strategy described above. Returns the number of solutions and sets the state for getSolutionText() and getElapsed() (below). The original grid of the sudoku should not be changed by the solution (i.e. toString() is still the original problem). The included puzzles have 1 solution each.

• long getElapsed() — after a solve, returns the elapsed time spent in the solve measured in milliseconds. See System.currentTimeMillis(). In particular, it’s interesting to get visibility into the timing effects of some of your code changes.

• You do not need to write javadoc.

It’s fine to use Integer or int or whatever to track the grid state — whatever you find most convenient. It’s good to leverage Set&lt;Integer&gt;/HashSet&lt;Integer&gt; and their built in methods contains(), addAll(), removeAll() to help solve the problem.

Do not pre-compute and store the possible numbers for a spot. Pre-computation worked very well in tetris, but it does not work well here. Each spot assignment changes the possible numbers for 20 other spots. However, in the search, you only care about the possible numbers for the one spot you look at next. Therefore, doing the computation for all 20 spots ahead of time is a bad strategy — better to compute the possible numbers for a spot at the moment you need them, based on the grid state at that moment.

Deliverable main()

Your Sudoku main() should be as below, using your code to print the problem and solution for the “hard 3 7” puzzle. As usual, comment out your other extraneous printing before turning in, so we can run your code to see just your clean output.

public static void main(String[] args) { Sudoku sudoku;

sudoku = new Sudoku(hardGrid);

System.out.println(sudoku); // print the raw problem

int count = sudoku.solve();

System.out.println(“solutions:” + count);

System.out.println(“elapsed:” + sudoku.getElapsed() + “ms”);

System.out.println(sudoku.getSolutionText());

}

Deliverable GUI

Finally, with the core logic of the Sudoku done, it’s time to nest it inside a SudokuFrame to make your hard algorithmic work available to a grateful public. The idea is that someone building a Sudoku puzzle could use this to play around with a puzzle they are building. The included puzzles all have a single solution. However, as you start adding 0’s, they get more solutions. For example, changing the 7 of the hard 3 7 puzzle should yield 6 solutions. (This is easiest to play with when you have the GUI working.)

We’ll make a simple layout like this: Use a BorderLayout(4,4) — the “4” is a little spacer between the areas. Create 15×20 JTextArea in the center to hold the “source” puzzle text. Create a second 15×20 JTextArea in the east to hold the results. Create a horizontal box in the south to hold the controls. The code — textarea.setBorder(new TitledBorder(“title”)) — puts the little titled border around any component.

When the Check button is clicked, construct a Sudoku for the text in the left text area and try to solve it:

• If the text is mal-formed in any way so the construction of the Sudoku throws an exception, just write “Parsing problem” in the results text area. (Use a try/catch.)

• Otherwise, after the solve(), if there is at least one solution, write its text into the results text area.

• If there is a solution, write the “solutions:xxx ” “elapsed:xxx ” at the end of the results text area.

• Finally, the “Auto” checkbox should make it so that every keystroke add/delete in the text area automatically does a “Check”. To implement this, get the “document” object from the text area. The document supports a DocumentListener object which gets notifications whenever the text changes. The Auto feature should work only if the auto checkbox is checked, which it should be by default.

Part B – Database

Here is what your application should look like:

The graphical layout of your application does not have to be an exact match with this screenshot, but it should contain the same information shown here and should look reasonably attractive and organized.

The application will provide options allowing the user to either search for metropolises matching particular criteria or to add a new metropolis to the database. The application should include a JTable which displays information gathered from the metropolises database. This table should start out empty and only show data in response to Search or Add requests.

Adding Data

When in add mode, the application will take the Metropolis, Continent, and Population as entered in the text boxes and enter them into the metropolises database. When an add operation is performed, reset the central table to display the newly added entry only. Do not worry about the possibility of duplicate entries.

Searching for Data

The user can enter search criteria in any or all of the Metropolis, Continent, and Population text fields. If no text is entered in a particular text field, we will assume that the user does not care about that particular criterion. If all fields are left blank, display all data in the database.

In addition to the text fields, two pull down menus are provided.

Population Pulldown – This JComboBox allows the user to determine if we are looking for metropolitan areas with populations greater or smaller than the number entered in the Population Text Field. It is ignored if the Population field is left empty.

Match Type Pulldown – This JComboBox allows the user to determine if the Metropolis and Continent text fields contain substrings we are searching for or exact matches. For example if this is set to ―Exact Match‖ and the Continent text field contains ―North‖ no matches will be found, whereas if the pulldown is set to ―Partial Match‖ metropolitan areas in North America will be listed.

Strategy

In contrast with previous assignments, the database part of this assignment comes with no starter files, you are to build it from scratch. This is good practice, as in industry there are, of course, no starter files and usually no directions provided on how to go about solving a problem. But here is a brief hint to get you started.

The JTable which is at the heart of the application should be constructed using a custom table model, which you can base on AbstractTableModel. Your table model will retrieve its data from the MySQL database. When the user changes the search criteria, the table model will retrieve new data from MySQL and will use the fireTableDataChanged to inform the JTable that it needs to redraw itself.

Documentation

Enter comments in your Java source code, and then export it to HTML using the JavaDoc tool. Comments preceded by /** instead of /* will be picked up by the JavaDoc tool. For descriptions on individual parameters, use the @ followed by the name of the parameter and then your description. For return values use @return followed by a description. Consider for example the following comments before the textToGrid method:

/**

* Given a single string containing 81 numbers, returns a 9×9 grid.

* Skips all the non-numbers in the text.

* (provided utility)

* @param text string of 81 numbers

* @return grid

*/

public static int[][] textToGrid(String text) {

…

}

This will generate the following documentation:

You can find additional examples in Sudoku.java.

Eclipse can run JavaDoc by selecting a class and then right-mouse clicking and choosing Export. JavaDoc will show up under the ―Java‖ category of the Export Dialog box. As I showed in class earlier this quarter the first time you run JavaDoc from Eclipse, you will need to show Eclipse where the JavaDoc executable is. It should be in your Java folder in the JDK binary directory. On my computer it is in:

C:Program FilesJavajdk1.6.0_05in

http://www.oracle.com/technetwork/java/javase/downloads/index.html

Database Administration

Remove your password from the source code when turning in your files—just leave an empty string “” where the password should go. We will be using a different database account for testing purposes, and will replace your account name, password, and database name with our own.
