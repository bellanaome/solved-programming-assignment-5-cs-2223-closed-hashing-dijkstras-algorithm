Download Link: https://assignmentchef.com/product/solved-programming-assignment-5-cs-2223-closed-hashing-dijkstras-algorithm
<br>
<ol>

 <li>(5 Points) Read a file and hash the words:</li>

</ol>

Read a text file (Raven.txt from Canvas) and hash the words using the suggested hash function from <em>Levitin</em>, page 269:

<em>h </em>← 0; <strong>for </strong><em>i </em>← 0 <strong>to </strong><em>s </em>− 1 <strong>do </strong><em>h </em>← (<em>h </em>∗ <em>C </em>+ <em>ord</em>(<em>c<sub>i</sub></em>)) mod <em>m</em>,

where:

<em>h </em>is the computed hash value, <em>s </em>is the length of the word being hashed, <em>c<sub>i </sub></em>is the <em>i<sup>th </sup></em>character of the word,

<em>ord</em>(<em>c</em>) is the numerical value of character <em>c </em>in the alphabet in use, <em>C </em>is a constant larger than every <em>ord</em>(<em>c<sub>i</sub></em>), and <em>m </em>is the modulus defining the size of our hash table.

We will take <em>ord</em>(<em>c</em>) to be the ASCII value of the characters in each word. Thus, <em>ord</em>(<em>c</em>) ∈ {39<em>,</em>65<em>,</em>66<em>,…,</em>90<em>,</em>97<em>,</em>98<em>,…</em>122} for <em>c </em>∈ {<sup>0</sup><em>,A,B,…,Z,a,b,…,z</em>}, respectively<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>. All other characters are discarded; we define words as unbroken sequences (strings!) of consecutive alphabetic characters, both upper and lower case, plus apostrophes, in the lines read for the file. (In C++, the function <strong>int</strong>(letter) returns the ASCII value of character ‘letter’.)

For our “Raven” text file, we will take <em>C </em>= 123 and <em>m </em>= 1000. These represent parameters that can be changed to alter the shape and composition of our resulting hash table. For now, we will use these values for the sake of consistency. You are free to experiment with changing these parameters on your own, of course!

<ol start="2">

 <li>(10 Points) Create a Hash Table using Closed Hashing (Open Addressing):

  <ol>

   <li>Build a hash table of size 1000, i.e. entries from 000 to 999, from the hash values computed in Part 1 above. Load them into the table in the order they occur in the file, <em>discarding duplicates</em>. Our table will be far from full–you needn’t worry about re-sizing it–we will examine the effects of its load factor in Part 3 below.</li>

   <li>Display the table, starting with table entry 0, in lines of the form:</li>

  </ol></li>

</ol>

Hash Address, Hashed Word, Hash Value of Word

(Remember, the Hash Address will not match the Hash Value when the resolution of a collision forces a word to be cascaded down the table. Also, remember that the table should be thought of as a circular list so that a word which cascades past the bottom end of the table gets wrapped to the top in looking for an open place in the table.)

Note: Your program may perform Parts 1 &amp; 2 simultaneously, if you wish.

<ol start="3">

 <li>(20 Points) Explore the Hash Table:</li>

</ol>

Add to your code routines that answer these questions. Some answers may not be unique. You may resolve these issues by presenting either <em>any </em>correct answer or <em>all </em>correct answers.

<ol>

 <li>How many non-empty addresses are there in the table? What does that make the load factor, <em>α</em>, for our table?</li>

 <li>What is the longest empty area in the table, and where is it?</li>

 <li>What is the longest (largest) cluster in the table, and where is it?</li>

 <li>What hash address results from the greatest number of distinct words, and how many words have that address?</li>

 <li>What word is placed in the table farthest from its actual hash address, and how far away is it from its actual hash address?</li>

</ol>

<ol start="4">

 <li>(25 Points) Implement Dijkstra’s Algorithm with weighted graphs like this:</li>

</ol>

Your code should read a text file and then ask for input from the console for start and destination nodes and use Dijkstra’s algorithm to find the “length” of the shortest path between them. It should also display the sequence of nodes that constitute this shortest path.

You can assume the associated graph, read from a text file, is connected and that the input file is consistent. (The main diagonal will consist exclusively of zeroes, there will be no negative edges, etc.)

10

0 50 7 10 0 0 0 0 0 0 50 0 30 0 3 0 99 0 0 0

7 30 0 6 27 15 0 0 0 0 10 0 6 0 0 11 0 0 4 0

0  3          27        0          0          12        120     105     0          0 0     0          15        11        12        0          0          119     5          0

0    99    0     0    120     0       0       2       0      67

0     0     0     0    105   119     2       0     122    66

0     0     0     4      0       5       0     122     0     190

0     0     0     0      0       0      67     66    190     0

<a href="#_ftnref1" name="_ftn1">[1]</a> That apostrophe will introduce a couple of artifacts given our text file. Working with ‘real’ data gets messy. See if you can find the artifacts, but consider them unique words. 1