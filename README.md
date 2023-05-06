Download Link: https://assignmentchef.com/product/solved-ece448-assignment-1-search
<br>
<h2>Part 1: Basic Pathfinding</h2>

<a name="part1"></a>Consider the problem of finding the shortest path from a given start state while eating one or more dots or “food pellets.” The image at the top of this page illustrates the simple scenario of a single dot, which in this case can be viewed as the unique goal state. The maze layout will be given to you in a simple text format, where ‘%’ stands for walls, ‘P’ for the starting position, and ‘.’ for the dot(s) (see <a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/bigMaze.txt">sample maze file</a>). All step costs are equal to one.

Implement the state representation, transition model, and goal test needed for solving the problem in the general case of multiple dots. For the state representation, besides your current position in the maze, is there anything else you need to keep track of? For the goal test, keep in mind that in the case of multiple dots, the Pacman does not necessarily have a unique ending position. Next, implement a unified top-level search routine that can work with all of the following search strategies, as covered in class and/or the textbook:

<ul>

 <li>Depth-first search</li>

 <li>Breadth-first search</li>

 <li>Greedy best-first search</li>

 <li>A* search</li>

</ul>

For this part of the assignment, use the Manhattan distance from the current position to the goal as the heuristic function for greedy and A* search.

Run each of the four search strategies on the following inputs:

<ul>

 <li><a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/mediumMaze.txt">Medium maze</a></li>

 <li><a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/bigMaze.txt">Big maze</a></li>

 <li><a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/openMaze.txt">Open maze</a></li>

</ul>

The provided code will generate a pretty picture of your solution. Your report should include

<ul>

 <li>The solution picture.</li>

 <li>The length of the path. <b>Include both the start and goal positions as part of your path and path length</b>.</li>

 <li>Number of nodes expanded by the search algorithm.</li>

</ul>

<h2>Part 2: Search with multiple dots</h2>

<a name="part2"></a>Now consider the harder problem of finding the shortest path through a maze while hitting multiple dots. Once again, the Pacman is initially at P, but now there is no single goal position. Instead, the goal is achieved whenever the Pacman manages to eat all the dots. Once again, we assume unit step costs.

As instructed in Part 1, your state representation, goal test, and transition model should already be adapted to deal with this scenario. The next challenge is to solve the following inputs using A* search using an admissible heuristic designed by you:

<a name="part2"></a>

<ul>

 <li><a name="part2"></a><a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/tinySearch.txt">Tiny search</a></li>

 <li><a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/smallSearch.txt">Small search</a></li>

 <li><a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/mediumSearch.txt">Medium search</a></li>

</ul>

You should be able to handle the tiny search using uninformed BFS. In fact, it is a good idea to try that first for debugging purposes, to make sure your representation works with multiple dots. However, to successfully handle all the inputs, it is crucial to come up with a good heuristic. For full credit, your heuristic should be <b>admissible</b> and should permit you to find the solution for the medium search in a reasonable amount of time. In your report, explain the heuristic you chose, and discuss why it is admissible and whether it leads to an optimal solution.

For each maze, your report should include (as for Part 1) the solution picture, the solution cost, and the number of nodes expanded in your search.<a name="extracredit"></a>

<h2><a name="extracredit"></a>Extra Credit Suggestion</h2>

<a name="extracredit"></a>

<a name="extracredit"></a>Sometimes, even with A* and a good heuristic, finding the optimal path through all the dots is hard. In these cases, we’d still like to find a reasonably good path, quickly. Write a suboptimal search algorithm that will do a good job on <a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/maps/bigDots.txt">this big maze</a>. Your algorithm could either be A* with a non-admissible heuristic, or something different altogether. In your report, discuss your approach and output the solution cost and number of expanded nodes. Note that the extra credit will be capped to 10% of what the assignment is worth.<a name="reference"></a>

<h2><a name="reference"></a>Provided Code Skeleton</h2>

<a name="reference"></a>

<a name="reference"></a>We have provided (<a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/web/mp1-code.tar"> tar file</a> or <a href="https://courses.engr.illinois.edu/cs440/sp2019/assignments/MP1/web/mp1-code.zip">zip file</a>) all the code to get you started on your MP, which means you will only have to write the search functions. <b>Do not modify provided code. You will only have to modify search.py.</b>

<h4>maze.py</h4>

<ul>

 <li>getStart() :- Returns a tuple of the starting position, (row, col)</li>

 <li>getObjectives() :- Returns a list of tuples that correspond to the dot positions, [(row1, col1), (row2, col2)]</li>

 <li>isValidMove(row, col) :- Returns the boolean <b>True</b> if the (row, col) position is valid. Returns <b>False</b> otherwise.</li>

 <li>getNeighbors(row, col) :- Given a position, returns the list of tuples that correspond to valid neighbor positions. This will return at most 4 neighbors, but may return less.</li>

</ul>

<h4>search.py</h4>

There are 4 methods to implement in this file, namely <b>bfs(maze), dfs(maze), greedy(maze),</b> and <b>astar(maze)</b>. (You may need to add another named search method if you implement an additional search method for extra credit.) Each of these functions takes in a maze instance, and should return both the path taken (as a list of tuples) and the number of states explored. The maze instance provided will already be instantiated, and the above methods will be accessible.

To understand how to run the MP, read the provided <b>README.md</b> or run <b>python3 mp1.py -h</b> into your terminal. The following command will display a maze and let you create a path manually using the arrow keys.

<blockquote>

 <b>python3 mp1.py –human maze.txt</b>

</blockquote>

The following command will run your astar search method on the maze.

<blockquote>

 <b>python3 mp1.py –method astar maze.txt</b>

</blockquote>

You can also save your output picture as a file in tga format. If your favorite document formatter doesn’t handle tga, tools such as gimp can convert it to other formats (e.g. jpg).