Download Link: https://assignmentchef.com/product/solved-cs146-project-2-maximum-subarray
<br>
In this project we will consider the Maximum Subarray (or Largest Sum Contiguous Subarray) problem discussed in class and presented in our textbook in section 4.1 and lecture 4. You have to implement, optimize and analyze three different algorithms that solve the same problem.

Problem Motivation: Suppose you are a freelancer and that you plan to work at a Mykonos resort for some part of the n-day summer season next year. Unfortunately, there isn’t enough work for you to  be paid every day and you need to cover your own expenses (but you want to go). Fortunately, you know in advance that if you are at the resort on the ith day of the season, you’ll make pi euros where pi could be negative (if expenses are more than earnings) or positive (if expenses are less than earnings). To maximize your earning you should choose carefully which day you arrive and which day you leave; the days you work should be consecutive and you don’t need to work all season. For example, if n = 8 and p1 = −9 , p2 = 10 , p3 = −8 , p4 = 10 , p5 = 5 , p6 = −4 , p7 = −2 , p8 = 5 then if you worked from day 2 to day 5, you would earn 10 − 8 + 10 + 5 = 17 euros in total. Assume the resort pays your air tickets.

Facts: When all numbers are positive, then all days are the answer, but when all numbers are negative; no days are selected and the total is 0. Your result should always be 0 or a positive number. Hint: use  arrays. The output is the maximum sum, as well as the arriving and departing day.

<ol>

 <li>The first algorithm is a brute force O(n<sup>2</sup>) algorithm that considers all possible pairs of arriving and departing dates. The outer loop picks the beginning element, the inner loop finds the maximum possible sum with the first element picked by outer loop and compares this maximum with the overall</li>

 <li>The second algorithm is a divide and conquer O(n lg n) algorithm. The basic idea follows:</li>

</ol>

<em>Algorithm D&amp;C (pseudocode)</em>

Use a Divide and Conquer approach. The idea follows

<ul>

 <li>Divide the given array in two halves</li>

 <li>Return the maximum of the following three</li>

</ul>

….<strong>a) </strong>Maximum subarray sum in left half (Make a recursive call)

….<strong>b) </strong>Maximum subarray sum in right half (Make a recursive call) ….<strong>c) </strong>Maximum subarray sum such that the subarray crosses the midpoint For 2c) we can easily find the crossing sum as follows: simply combine the left part and the right part.

1

Basically, that method finds the maximum sum starting from mid point and ending at some point on left of mid, then finds the maximum sum starting from mid + 1 and ending with sum point on right of mid + 1 and adding them together.

<ol>

 <li>The third algorithm is a (dynamic programming) O(n) algorithm, known as Kadane’s Algorithm. The basic idea is that you keep only positive contiguous summations that we compute by adding one element each time, kept in maxTemp, and at the end keep the best, and save in maxSum. In the next pseudocode, also the arrive and depart index are computed.</li>

</ol>

<strong>Kadane’s Algorithm:</strong>

returns depart -1 if sum is &lt;0 Test cases:

<ol>

 <li>Consider the tests that are given in <strong>maxSumtest.txt</strong><sup>1</sup>use them for the JUnits. The file has one test case per line (10 cases each with 100 entries).</li>

</ol>

A line corresponding to the examples in the above file would be of the form

[array], sum, arrive, depart

<ol start="2">

 <li>You can try other simple examples as these two with an array size of 8</li>

</ol>

<ul>

 <li>-3 4 -1 -2 1 5 -3 7 2 6</li>

 <li>-4 -5 -6 -7 -8 -9 -10 0 0 -1</li>

</ul>

Additionally, you should test it for various small and different cases.

<ol start="3">

 <li>For doing the experimental analysis of the running time, plot the running times as a function of the input size. Run each of your algorithms on random input arrays of size n=100, 200, 500,1000, 2000, 5000, 10000, (for each size/algorithm run 10 times and take average). The first algorithm (a) may be very slow, therefore go up to 1000 only. Remember to have positive and negative numbers.</li>

</ol>

1

http://web.engr.oregonstate.edu/~glencora/cs325/mstest.txt

2 For example, for i = 1 to 10 create a random array a[] n (size) elements start clock

run maxSubarrayAlgorithm(a) stop clock

add to elapsed time

return (elapsed time/10)

Note: Do not include the time to generate the random arrays.

Help with <a href="https://www.geeksforgeeks.org/java-util-random-class-java/">pseudo-random number generation</a>:

//Set seed value as 20, so that every time you get the same sequence of random numbers Random r=new Random();

r.setSeed(20);

Compare the output file with attached see next:

either use nextDouble(): double d = random.nextDouble(); int j = (int)(d*arr.length); Or nextInt()

Plots for running time

<ul>

 <li>Plot the running times as a function of input size for each algorithm in a single plot. Label your plot (axes, title, etc.).</li>

 <li>Include an additional plot of the running times on a log-log axis. See here for an explanation: <u>http://en.wikipedia.org/wiki/Log-log_graph</u>. Note that if the slope of a line in a log log plot is m, then the line is of the form O(x<sup>m</sup>) on a linear plot. Check this video: <u>http://www.khanacademy.org/math/algebra/logarithms/v/logarithmic-scale</u></li>

</ul>

<strong>Programming Standards (check posted rubric):</strong>

<ul>

 <li>Your header comment must describe what your program does.</li>

 <li>You must include a comment explaining the purpose of every variable or named constant you use in your program.</li>

 <li>You must use meaningful identifier names that suggest the meaning or purpose of the constant, variable, function, etc.</li>

 <li>Precede every major block of your code with a comment explaining its purpose. You don’t have to describe how it works unless you do something tricky.</li>

 <li>You must use indentation and blank lines to make control structures more readable. <strong>Deliverables:</strong></li>

 <li>Your main grade will be based on (a) how well your tests cover your own code, (b) how well your code does on your tests (create for all non-trivial methods), and (c) how well your code does on my tests (which you have to add to your test file). For JUnit tests check canvas.</li>

 <li>Use cs146S21.&lt;lastname&gt;.project2 as your package, and Test classes should be your main java file, along with your JUnit java tests.</li>

 <li>What to submit to canvas (Steps):

  <ul>

   <li>Export your project on eclipse with your entire project (source code).</li>

   <li>Create a zip file named <strong>zip </strong>that includes the exported zip file + pdf report</li>

   <li>upload the last zip file to canvas.</li>

  </ul></li>

 <li>All projects need to compile. If your program does not compile you will receive 0 points on this project.</li>

 <li>Do not use any fancy libraries. We should be able to compile it under standard installs. Include a readme file on how to compile the project.</li>

</ul>