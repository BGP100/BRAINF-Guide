<a href="/Issues/Endofline-Code.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Implementations.md">Next &gt;</a>
<hr>
The behavior of the <code>,</code> command when an end-of-file condition has been encountered varies. Some implementations set the cell at the pointer to 0, some set it to the C constant EOF (in practice this is usually -1), some leave the cell's value unchanged. There is no real consensus; arguments for the three behaviors are as follows.
<br>
Setting the cell to 0 avoids the use of negative numbers, and makes it marginally more concise to write a loop that reads characters until EOF occurs. This is a language extension devised by Panu Kalliokoski.
<br>
Setting the cell to -1 allows EOF to be distinguished from any byte value (if the cells are larger than bytes), which is necessary for reading non-textual data; also, it is the behavior of the C translation of <code>,</code> given in Müller's readme file. However, it is not obvious that those C translations are to be taken as normative.
<br>
Leaving the cell's value unchanged is the behavior of Urban Müller's brainfuck compiler. This behavior can easily coexist with either of the others; for instance, a program that assumes EOF = 0 can set the cell to 0 before each <code>,</code> command, and will then work correctly on implementations that do either EOF = 0 or EOF = "no change". It is so easy to accommodate the "no change" behavior that any brainfuck programmer interested in portability should do so.
