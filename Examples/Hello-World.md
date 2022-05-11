<a href="/Examples/Adding-2-Values.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Examples/ROT13.md">Next &gt;</a>
<hr>
The following program prints "Hello World!" and a newline to the screen:
<pre>
++++++++               Set Cell #0 to 8
[
    &gt;++++               Add 4 to Cell #1; this will always set Cell #1 to 4
    [                   as the cell will be cleared by the loop
        &gt;++             Add 2 to Cell #2
        &gt;+++            Add 3 to Cell #3
        &gt;+++            Add 3 to Cell #4
        &gt;+              Add 1 to Cell #5
        &lt;&lt;&lt;&lt;-           Decrement the loop counter in Cell #1
    ]                   Loop until Cell #1 is zero; number of iterations is 4
    &gt;+                  Add 1 to Cell #2
    &gt;+                  Add 1 to Cell #3
    &gt;-                  Subtract 1 from Cell #4
    &gt;&gt;+                 Add 1 to Cell #6
    [&lt;]                 Move back to the first zero cell you find; this will
                        be Cell #1 which was cleared by the previous loop
    &lt;-                  Decrement the loop Counter in Cell #0
]                       Loop until Cell #0 is zero; number of iterations is 8

                             The result of this is:
                             Cell no :   0   1   2   3   4   5   6
                             Contents:   0   0  72 104  88  32   8
                             Pointer :   ^

&gt;&gt;.                     Cell #2 has value 72 which is 'H'
&gt;---.                   Subtract 3 from Cell #3 to get 101 which is 'e'
+++++++..+++.           Likewise for 'llo' from Cell #3
&gt;&gt;.                     Cell #5 is 32 for the space
&lt;-.                     Subtract 1 from Cell #4 for 87 to give a 'W'
&lt;.                      Cell #3 was set to 'o' from the end of 'Hello'
+++.------.--------.    Cell #3 for 'rl' and 'd'
&gt;&gt;+.                    Add 1 to Cell #5 gives us an exclamation point
&gt;++.                    And finally a newline from Cell #6
</pre>
Code without comments:
<pre>++++++++[&gt;++++[&gt;++&gt;+++&gt;+++&gt;+&lt;&lt;&lt;&lt;-]&gt;+&gt;+&gt;-&gt;&gt;+[&lt;]&lt;-]&gt;&gt;.&gt;---.+++++++..+++.&gt;&gt;.&lt;-.&lt;.+++.------.--------.&gt;&gt;+.&gt;++.</pre>
