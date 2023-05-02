Download Link: https://assignmentchef.com/product/solved-comp1410-assignment-2-maze-traversal
<br>
The following grid is a double-subscripted array representation of a maze.

The # symbols represent the walls of the maze, and the periods (.) represent squares in the possible paths through the maze. There’s a simple algorithm for walking through a maze that guarantees finding the exit (assuming there’s an exit). If there’s not an exit, you’ll arrive at the starting location again. Place your right hand on the wall to your right and begin walking forward. Never remove your hand from the wall. If the maze turns to the right, you follow the wall to the right. As long as you do not remove your hand from the wall, eventually you’ll arrive at the exit of the maze. There may be a shorter path than the one you have taken, but you’re guaranteed to get out of the maze.

For this assignment, the initial maze will use 1’s instead of #’s and 0’s instead of .’s, leading to the representation of the maze above in the form:

111111111111

100010000001

001010111101

111010000101

100001110100

111101010101

100101010101

110101010101

100000000101

111111011101

100000010001

111111111111




<strong>Your task is to: </strong>




Write a complete, well documented C program to walk through the maze, starting from the maze entrance location, and attempts to locate the exit from the maze.




<strong>Requirements and Hints: </strong>

<ol>

 <li>Given the input maze, your program logic will:

  <ol>

   <li>Find the maze entrance (start point, see Figure below) from the left side of the input maze</li>

  </ol></li>

</ol>

(first column)

<ol>

 <li>Then, start to traverse the maze to find the next valid move</li>

 <li>If the movement is valid and it is not the maze exit (i.e. a coordinate on the maze edge, including the starting position)

  <ol>

   <li>place character X in that location in the path</li>

   <li>print the current state of the maze</li>

  </ol></li>

</ol>

<ul>

 <li>Go back to step (b)</li>

</ul>

<ol>

 <li>Steps b. and c. will continue until finding the maze exit coordinate.</li>

</ol>

<ol start="2">

 <li>This solution assumes that there is only one entrance on the left edge of the maze and one exit on any other edges of the given maze (including the left edge). So, there are only two zeroes (one for entrance and one for exit) on the edges.</li>

 <li>Your program should implement at least the following functions:

  <ol>

   <li><strong>void findStart()</strong>, that will find the start point from the first column of the input maze (maze[][1]).</li>

   <li><strong>void mazeTraversal( ), </strong>is a <strong>recursive</strong> function that gives maze, current x and y coordinate and direction as an input. There are four valid directions of up, down, left and right. Also, the first (X,Y) coordinate to call mazeTraversal function is the found start point (maze entrance).</li>

   <li><strong>void printMaze( )</strong>,that will print the current state of the maze after each movement.</li>

   <li><strong>int validMove( )</strong>, that will determine the validity of the next movement (input coordinates).</li>

   <li><strong>int coordsAreEdge( )</strong>, that check the input coordinate are edge or not.</li>

  </ol></li>

</ol>

<strong> </strong>

<strong>Declaration of maze data, or Input: </strong>

A 12-by-12 character array representing the maze that has 1 symbols showing the walls of the maze and zeroes (0) showing squares in the possible paths through the maze. You can get the maze from a file or easily declare the maze data in main() of your program, manually.




<strong>Output </strong>

Placing the character X in each square in the path and displaying the maze after each move so the user can watch as the maze is solved.  (Note that a move can revisit a square with an X in it.)




<strong>Sample declaration of maze data, or input:  </strong>

char maze[12][12] ={ {‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’, ‘1’},

{‘1’, ‘0’ ,‘0’ ,‘0’ ,‘1’, ‘0’, ‘0’ ,‘0’ ,‘0’ ,‘0’ ,‘0’ ,‘1’},

…

}

You can complete the above two-dimensional maze array definition from the following Figure 1.




<strong>1 1 1 1 1 1 1 1 1 1 1 1   </strong>

<strong>1 0 0 0 1 0 0 0 0 0 0 1   </strong>Maze Entrance        <strong>0</strong><strong> 0 1 0 1 0 1 1 1 1 0 1   </strong>point        <strong>1 1 1 0 1 0 0 0 0 1 0 1        </strong>Maze Exit

<strong>1 0 0 0 0 1 1 1 0 1 0 </strong><strong>0</strong><strong>   1 1 1 1 0 1 0 1 0 1 0 1   1 0 0 1 0 1 0 1 0 1 0 1   1 1 0 1 0 1 0 1 0 1 0 1   </strong>

<strong>1 0 0 0 0 0 0 0 0 1 0 1   </strong>

<strong>1 1 1 1 1 1 0 1 1 1 0 1   1 0 0 0 0 0 0 1 0 0 0 1   1 1 1 1 1 1 1 1 1 1 1 1 </strong>







<em>Figure 1. Sample maze layout for Assignment #2.</em>




<strong>Sample output:</strong>




If you run your program in interactive mode, one move at a time, then the output sequence shown below is reasonable for the example maze shown in Figure 1:




…

1 1 1 1 1 1 1 1 1 1 1 1

1 X 0 0 1 0 0 0 0 0 0 1

X X 1 0 1 0 1 1 1 1 0 1

1 1 1 0 1 0 0 0 0 1 0 1

1 0 0 0 0 1 1 1 0 1 0 0

1 1 1 1 0 1 0 1 0 1 0 1

1 0 0 1 0 1 0 1 0 1 0 1

1 1 0 1 0 1 0 1 0 1 0 1

1 0 0 0 0 0 0 0 0 1 0 1

1 1 1 1 1 1 0 1 1 1 0 1

1 0 0 0 0 0 0 1 0 0 0 1

1 1 1 1 1 1 1 1 1 1 1 1




Hit return to see next move




1 1 1 1 1 1 1 1 1 1 1 1

1 X X 0 1 0 0 0 0 0 0 1

X X 1 0 1 0 1 1 1 1 0 1

1 1 1 0 1 0 0 0 0 1 0 1

1 0 0 0 0 1 1 1 0 1 0 0

1 1 1 1 0 1 0 1 0 1 0 1

1 0 0 1 0 1 0 1 0 1 0 1

1 1 0 1 0 1 0 1 0 1 0 1

1 0 0 0 0 0 0 0 0 1 0 1

1 1 1 1 1 1 0 1 1 1 0 1

1 0 0 0 0 0 0 1 0 0 0 1

1 1 1 1 1 1 1 1 1 1 1 1




Hit return to see next move

…




However, for generating the output from the program for submitting for marks, simply output the <strong>final pathway</strong> or failure to solve the maze (e.g. Entrance, but no Exit).  This is shown below in Figure 2

for a successful maze traversal, using the strategy of touching one’s right hand to the wall to the right; note that this solution is not unique – other correct solutions can be determined using various strategies:







111111111111

1XXX1XXXXXX1

XX1X1X1111X1

111X1XXXX1X1

1XXXX111X1XX

1111X1X1X1X1

1XX1X1X1X1X1

11X1X1X1X1X1

1XXXXXXXX1X1

111111X111X1 1XXXXXX1XXX1

111111111111




<em>Figure 2. Final maze traversal for sample shown in Figure </em>