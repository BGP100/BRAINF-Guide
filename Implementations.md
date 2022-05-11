<a href="/Issues/Endofline-Behavior.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="File.md">Next &gt;</a>
<hr>
Although it is trivial to make a naive brainfuck interpreter, writing an optimizing compiler or interpreter becomes more of a challenge and amusement much like writing programs in brainfuck itself is: to produce reasonably fast results, the compiler needs to piece together the fragmentary instructions forced by the language. Possible optimizations range from simple run-length peephole optimizations on repeated commands and common loop patterns like <code>[-]</code>, to more complicated ones like dead code elimination and constant folding.
<br>
In addition to optimization, other types of unusual brainfuck interpreters have also been written. Several brainfuck compilers have been made smaller than 200 bytes – one is only 100 bytes in x86 machine code.
