<a href="/Example/Hello-World.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Resources.md">Next &gt;</a>
<hr>
This program enciphers its input with the ROT13 cipher. To do this, it must map characters A-M (ASCII 65-77) to N-Z (78-90), and vice versa. Also it must map a-m (97-109) to n-z (110-122) and vice versa. It must map all other characters to themselves; it reads characters one at a time and outputs their enciphered equivalents until it reads an EOF (here assumed to be represented as either -1 or "no change"), at which point the program terminates.
<br>
The basic approach used is as follows. Calling the input character x, divide x-1 by 32, keeping quotient and remainder. Unless the quotient is 2 or 3, just output x, having kept a copy of it during the division. If the quotient is 2 or 3, divide the remainder ((x-1) modulo 32) by 13; if the quotient here is 0, output x+13; if 1, output x-13; if 2, output x.
<br>
Regarding the division algorithm, when dividing y by z to get a quotient q and remainder r, there is an outer loop which sets q and r first to the quotient and remainder of 1/z, then to those of 2/z, and so on; after it has executed y times, this outer loop terminates, leaving q and r set to the quotient and remainder of y/z. (The dividend y is used as a diminishing counter that controls how many times this loop is executed.) Within the loop, there is code to increment r and decrement y, which is usually sufficient; however, every zth time through the outer loop, it is necessary to zero r and increment q. This is done with a diminishing counter set to the divisor z; each time through the outer loop, this counter is decremented, and when it reaches zero, it is refilled by moving the value from r back into it.
<pre>
-,+[                         Read first character and start outer character reading loop
    -[                       Skip forward if character is 0
        &gt;&gt;++++[&gt;++++++++&lt;-]  Set up divisor (32) for division loop
                             (MEMORY LAYOUT: dividend copy remainder divisor quotient zero zero)
        &lt;+&lt;-[                Set up dividend (x minus 1) and enter division loop
            &gt;+&gt;+&gt;-[&gt;&gt;&gt;]      Increase copy and remainder / reduce divisor / Normal case: skip forward
            &lt;[[&gt;+&lt;-]&gt;+&gt;]     Special case: move remainder back to divisor and increase quotient
            &lt;&lt;&lt;&lt;&lt;-           Decrement dividend
        ]                    End division loop
    ]&gt;&gt;&gt;[-]+                 End skip loop; zero former divisor and reuse space for a flag
    &gt;--[-[&lt;-&gt;+++[-]]]&lt;[      Zero that flag unless quotient was 2 or 3; zero quotient; check flag
        ++++++++++++&lt;[       If flag then set up divisor (13) for second division loop
                             (MEMORY LAYOUT: zero copy dividend divisor remainder quotient zero zero)
            &gt;-[&gt;+&gt;&gt;]         Reduce divisor; Normal case: increase remainder
            &gt;[+[&lt;+&gt;-]&gt;+&gt;&gt;]   Special case: increase remainder / move it back to divisor / increase quotient
            &lt;&lt;&lt;&lt;&lt;-           Decrease dividend
        ]                    End division loop
        &gt;&gt;[&lt;+&gt;-]             Add remainder back to divisor to get a useful 13
        &gt;[                   Skip forward if quotient was 0
            -[               Decrement quotient and skip forward if quotient was 1
                -&lt;&lt;[-]&gt;&gt;     Zero quotient and divisor if quotient was 2
            ]&lt;&lt;[&lt;&lt;-&gt;&gt;-]&gt;&gt;    Zero divisor and subtract 13 from copy if quotient was 1
        ]&lt;&lt;[&lt;&lt;+&gt;&gt;-]          Zero divisor and add 13 to copy if quotient was 0
    ]                        End outer skip loop (jump to here if ((character minus 1)/32) was not 2 or 3)
    &lt;[-]                     Clear remainder from first division if second division was skipped
    &lt;.[-]                    Output ROT13ed character from copy and clear it
    &lt;-,+                     Read next character
]                            End character reading loop
</pre>
Code without comments:
<pre>-,+[-[&gt;&gt;++++[&gt;++++++++&lt;-]&lt;+&lt;-[&gt;+&gt;+&gt;-[&gt;&gt;&gt;]&lt;[[&gt;+&lt;-]&gt;+&gt;]&lt;&lt;&lt;&lt;&lt;-]]&gt;&gt;&gt;[-]+&gt;--[-[&lt;-&gt;+++[-]]]&lt;[++++++++++++&lt;[&gt;-[&gt;+&gt;&gt;]&gt;[+[&lt;+&gt;-]&gt;+&gt;&gt;]&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;[&lt;+&gt;-&gt;[-[-&lt;&lt;[-]&gt;&gt;]&lt;&lt;[&lt;&lt;-&gt;&gt;-]&gt;&gt;]&lt;&lt;[&lt;&lt;+&gt;&gt;-]]&lt;[-]&lt;.[-]&lt;-,+]</pre>
