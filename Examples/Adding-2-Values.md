<a href="/Examples/Main.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Examples/Hello-World.md">Next &gt;</a>
<hr>
As a first, simple example, the following code snippet will add the current cell's value to the next cell: Each time the loop is executed, the current cell is decremented, the data pointer moves to the right, that next cell is incremented, and the data pointer moves left again. This sequence is repeated until the starting cell is 0.
<pre>[-&gt;+&lt;]</pre>
This can be incorporated into a simple addition program as follows:
<pre>
++         Cell c0 = 2
&gt; +++++    Cell c1 = 5<br>
[          Start your loops with your cell pointer on the loop counter (c1 in our case)
&lt; +        Add 1 to c0
&gt; -        Subtract 1 from c1
]          End your loops with the cell pointer on the loop counter<br>
           At this point our program has added 5 to 2 leaving 7 in c0 and 0 in c1
           but we cannot output this value to the terminal since it is not ASCII encoded.<br>
           To display the ASCII character "7" we must add 48 to the value 7.
           We use a loop to compute 48 = 6 * 8.<br>
++++ ++++  c1 = 8 and this will be our loop counter again
[
&lt; +++ +++  Add 6 to c0
&gt; -        Subtract 1 from c1
]
&lt; .        Print out c0 which has the value 55 which translates to "7"!
</pre>
Code without comments:
<pre>++&gt;+++++[&lt;+&gt;-]++++++++[&lt;++++++&gt;-]&lt;.</pre>
