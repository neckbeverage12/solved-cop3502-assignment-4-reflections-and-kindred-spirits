Download Link: https://assignmentchef.com/product/solved-cop3502-assignment-4-reflections-and-kindred-spirits
<br>
This program is designed to get you thinking recursively with binary trees. Rather than solving one big problem, you will code up solutions to three smaller problems, each of which will rely on recursion to some degree.

This time around, I’m not giving you a slew of function definitions that essentially pre-define the structure of your program. Accordingly, this assignment will challenge you to think creatively, both in terms of how to solve the problems, as well as how to make appropriate use of helper functions as you plan out how to structure your code – especially with the <em>kindredSpirits()</em> function. This will be fun.

<strong>Attachments</strong>

KindredSpirits.h, testcase{01-16}.c, output{01-16}.c, and test-all.sh

<strong>Deliverables</strong>

KindredSpirits.c

(<strong><em>Note!</em></strong> Capitalization of your filename matters!)

<h1>1.      Overview, Part 1 of 2: Reflections</h1>

Given two binary trees, we say that one is a reflection of the other if they are symmetric in terms of both their structure and their node values. For example, the following trees are reflections of one another:

<strong><em>Figure 1: </em></strong><em>Two trees that are reflections of one another.</em>

The following trees are <em>not</em> reflections of one another, because although they are symmetric images of one another <em>structurally</em>, they are not symmetric in terms of their <em>values</em>:

<strong><em>Figure 2: </em></strong><em>Two structurally symmetric trees that are not reflections of one another because they are lack symmetry with respect to their node values.</em>

Because the following binary trees are not structurally symmetric (and therefore they also cannot be symmetric in terms of the values contained in each node), they are not reflections of one another:

<strong><em>Figure 3: </em></strong><em>Structurally asymmetric trees cannot be reflections of one another.</em>

The following binary trees are reflections of one another:

<strong><em>Figure. 4: </em></strong><em>Two trees that are reflections of one another. They are perfect binary trees. They are also large and in charge.</em>

Recall that the tree above is a perfect binary tree. You might ask yourself, “Is it always the case that a perfect binary tree is a reflection of itself?” The answer is, “No!” Here’s a counterexample that shows that a perfect binary tree is not always a reflection of itself:

<strong><em>Figure 5: </em></strong><em>This perfect binary tree is not a reflection of itself. Despite its structural symmetry, it is not symmetric to itself with respect to its node values.</em>

Any binary tree with a single node is a reflection of itself. For example:

33              33

<strong><em>Figure 6: </em></strong><em>Two trees that are reflections of one another.</em>

However, it is <em>not</em> the case that all binary trees with a single node are reflections of one another. For example:

15              21

<strong><em>Figure 7: </em></strong><em>Two trees that are not reflections of one another, because they are not symmetric with respect to their values.</em>

Finally, note that the empty tree is a reflection of itself:

<strong><em>Figure 8:</em></strong><em> Two trees (both empty) that are reflections of one another.</em>

<em>This example is serene and beautiful, and brings with it an overwhelming sense that everything is going to be okay.</em>

<h1>2.      Overview, Part 2 of 2: Kindred Spirits</h1>

We say that two binary trees are <em>kindred spirits</em> if the preorder traversal of one of the trees corresponds to the postorder traversal of the other tree. For example, the following trees are kindred spirits:

<strong><em>Figure 9:</em></strong><em> These trees are kindred spirits. The preorder traversal of the tree on the left is 23, 12, 5, 18, 71, 56, which corresponds to the postorder traversal of the tree on the right.</em>

Note that the trees above are still kindred spirits even if we swap their order:

<strong><em>Figure 10:</em></strong><em> These trees from Figure 9 are still kindred spirits, despite the fact that the preorder traversal of the tree on the right now matches the postorder traversal of the tree on the left, instead of the other way around.</em>

<h1>3.      Binary Tree Node Struct (KindredSpirits.h)</h1>

You must use the node struct we have specified in KindredSpirits.h without any modifications. You will have to #include the header file in your KindredSpirits.c source file like so:

#include “KindredSpirits.h”

Note that the capitalization of KindredSpirits.c matters! Filenames are case sensitive in Linux, and that is of course the operating system we’ll be using to test your code.

The node struct is defined in KindredSpirits.h as follows:

typedef struct node

{    int data;

struct node *left, *right; } node;

If you’re using Code::Blocks, you will need to add the KindredSpirits.h header file to your project. See the instructions in Section 8, “Compilation and Testing (Code::Blocks).”

<h1>4.      Test Cases and the test-all.sh Script</h1>

As always, I’ve included several test cases, which show some ways in which I might test your code. These test cases are not comprehensive. You should also create your own test cases if you want to test your code comprehensively.

I’ve included a script, test-all.sh, that will compile and run all test cases for you. You can run it on Eustis by placing it in a directory with KindredSpirits.c and KindredSpirits.h and typing:

bash test-all.sh

<h1>5.      Output</h1>

The functions you write for this assignment should not produce any output. If your functions cause anything to print to the screen, it might interfere with our test case evaluation. Be sure to disable or remove any printf() statements you have in your code before submitting this assignment.

<h1>6.      Function Requirements</h1>

You have a lot of leeway with how to approach this assignment. There are only five required functions, and you may write helper functions as you see fit. For the kindredSpirits() function, you will likely need quite a few helper functions, and a good measure of creative thinking and/or cleverness.

Function descriptions for this assignment are included on the following page. Please do not include a main() function in your submission.

int isReflection(node *a, node *b);

<strong>Description:</strong> A function to determine whether the trees rooted at <em>a</em> and <em>b</em> are reflections of one another, according to the definition of “reflection” given above. This must be implemented recursively.

<strong>Returns:</strong> 1 if the trees are reflections of one another, 0 otherwise.

node *makeReflection(node *root);

<strong>Description:</strong> A function that creates a new tree, which is a reflection of the tree rooted at <em>root</em>. This function must create an entirely new tree in memory. As your function creates a new tree, it must <em>not </em>destroy or alter the structure or values in the tree that was passed to it as a parameter. Tampering with the tree rooted at <em>root </em>will cause test case failure.

<strong>Returns:</strong> A pointer to the root of the new tree. (This implies, of course, that all the nodes in the new tree must be dynamically allocated.)

int kindredSpirits(node *a, node *b);

<strong>Description:</strong> A function that determines whether the trees rooted at <em>a</em> and <em>b</em> are kindred spirits. (See definition of “kindred spirits” above.) The function must not destroy or alter the trees in any way. Tampering with these trees will cause test case failure.

<strong>Special Restrictions:</strong> To be eligible for credit, the worst-case runtime of this function cannot exceed O(<em>n</em>), where <em>n </em>is the number of nodes in the larger of the two trees being compared. This function must also be able to handle arbitrarily large trees. (So, do not write a function that has a limit as to how many nodes it can handle.) You may write helper functions as needed.

<strong>Returns:</strong> 1 if the trees are kindred spirits, 0 otherwise.

double difficultyRating(void);

<strong>Returns:</strong> A double indicating how difficult you found this assignment on a scale of 1.0 (ridiculously easy) through 5.0 (insanely difficult).

double hoursSpent(void);

<strong>Returns:</strong> An estimate (greater than zero) of the number of hours you spent on this assignment.

<em>The remaining pages of this document contain compilation instructions for Linux/Mac (pg. 7) and Windows (pg. 8), further restrictions and guidelines for your program (see pgs. 8 and 9), and grading criteria (pg. 9).</em>

<h1>7.      Compilation and Testing (Linux/Mac Command Line)</h1>

To compile multiple source files (.c files) at the command line:

gcc KindredSpirits.c testcase01.c

By default, this will produce an executable file called a.out, which you can run by typing:

./a.out

If you want to name the executable file something else, use:

gcc KindredSpirits.c testcase01.c -o KindredSpirits.exe

…and then run the program using:

./KindredSpirits.exe

Running the program could potentially dump a lot of output to the screen. If you want to redirect your output to a text file in Linux, it’s easy. Just run the program using the following command, which will create a file called whatever.txt that contains the output from your program:

./KindredSpirits.exe &gt; whatever.txt

Linux has a helpful command called diff for comparing the contents of two files, which is really helpful here since we’ve provided several sample output files. You can see whether your output matches ours exactly by typing, e.g.:

diff whatever.txt output01.txt

If the contents of whatever.txt and output01.txt are exactly the same, diff won’t have any output. It will just look like this:

<strong><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="e39086828d9099a3869690978a90">[email protected]</a>:~$</strong> diff whatever.txt output01.txt <strong><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="5a293f3b3429201a3f2f292e3329">[email protected]</a>:~$</strong> _

If the files differ, it will spit out some information about the lines that aren’t the same. For example:

<strong><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="b8cbddd9d6cbc2f8ddcdcbccd1cb">[email protected]</a>:~$</strong> diff whatever.txt output01.txt

1c1

&lt; fail whale &#x1f641;

—

&gt; Success!

<strong><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="f58690949b868fb5908086819c86">[email protected]</a>:~$</strong> _

<h1>8.      Compilation and Testing (Code::Blocks)</h1>

The key to getting your program to include a custom header file in Code::Blocks (or any IDE) is to create a project. Here are the step-by-step instructions for creating a project in Code::Blocks, importing KindredSpirits.h and the KindredSpirits.c file you’ve created (even if it’s just an empty file so far).

<ol>

 <li>Start Code::Blocks.</li>

 <li>Create a New Project (<em>File</em> → <em>New</em> → <em>Project</em>).</li>

 <li>Choose “Empty Project” and click “Go.”</li>

 <li>In the Project Wizard that opens, click “Next.”</li>

 <li>Input a title for your project (e.g., “KindredSpirits”).</li>

 <li>Pause to reflect on life a bit. Isn’t this amazing?</li>

 <li>Choose a folder (e.g., Desktop) where Code::Blocks can create a subdirectory for the project.</li>

 <li>Click “Finish.”</li>

</ol>

Now you need to import your files. You have two options:

<ol>

 <li>Drag your source and header files into Code::Blocks. Then right click the tab for <strong><u>each</u></strong> file and choose “Add file to active project.”</li>

</ol>

– <em>or</em> –

<ol start="2">

 <li>Go to <em>Project</em> → <em>Add Files</em>…. Then browse to the directory with the source and header files you want to import. Select the files from the list (using CTRL-click to select multiple files). Click “Open.” In the dialog box that pops up, click “OK.”</li>

</ol>

You should now be good to go. Try to build and run the project (F9). As a friendly reminder: Even if you develop your code with Code::Blocks on Windows, you ultimately have to transfer it to the Eustis server to compile and test it there. See the following page (Section 7, “Compilation and Testing (Linux/Mac Command Line)”) for instructions on command line compilation in Linux.

<h1>9.      Deliverables</h1>

Submit a single source file, named KindredSpirits.c, via Webcourses. The source file should contain definitions for all the required functions (listed above), as well as any auxiliary functions you need to make them work. Don’t forget to #include “KindredSpirits.h” in your source code. Your program should compile on Eustis with both of the following :

gcc -c KindredSpirits.c

gcc KindredSpirits.c testcase01.c

<h1>10.Special Restrictions</h1>

<ol>

 <li>As always, you must avoid the use of global variables, mid-function variable declarations, and system calls (such as system(“pause”)).</li>

 <li>Do not submit the h header file with your code. You should only submit KindredSpirits.c. We will use our own version of the header file when testing your program.</li>

 <li>Be sure you don’t write anything in c that conflicts with what’s given in KindredSpirits.h. Namely, do not try to define a node struct in KindredSpirits.c, since your source file will already be importing the definition of a node struct from KindredSpirits.h.</li>

 <li>Be sure to include your name and NID as a comment at the top of your source file.</li>

 <li>No shenanigans. For example, if you write a kindredSpirits() function that always returns 1, you might not receive any credit for the test cases that it happens to pass.</li>

 <li>Your c file <strong>must not</strong> include a main() function. If it does, your code will fail to compile during testing, and you will not receive credit for this assignment.</li>

</ol>