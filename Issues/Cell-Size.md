<a href="/Issues/Main.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Issues/Array-Size.md">Next &gt;</a>
<hr>
In the classic distribution, the cells are of 8-bit size (cells are bytes), and this is still the most common size. However, to read non-textual data, a brainfuck program may need to distinguish an end-of-file condition from any possible byte value; thus 16-bit cells have also been used. Some implementations have used 32-bit cells, 64-bit cells, or bignum cells with theoretically unlimited range, but programs that use this extra range are likely to be slow, since storing the value <code>&nscr;</code> into a cell requires <code>&Oscr;(&nscr;)</code> time as a cell's value may only be changed by incrementing and decrementing.
<br>
In all these variants, the <code>,</code> and <code>.</code> commands still read and write data in bytes. In most of them, the cells wrap around, i.e. incrementing a cell which holds its maximal value (with the + command) will bring it to its minimal value and vice versa. The exceptions are implementations which are distant from the underlying hardware, implementations that use bignums, and implementations that try to enforce portability.
<br>
It is usually easy to write brainfuck programs that do not ever cause integer wraparound or overflow, and therefore don't depend on cell size. Generally this means avoiding increment of <code>+255</code> (unsigned 8-bit wraparound), or avoiding overstepping the boundaries of <code>[-128, +127]</code> (signed 8-bit wraparound) (since there are no comparison operators, a program cannot distinguish between a signed and unsigned two's complement fixed-bit-size cell and negativeness of numbers is a matter of interpretation). For more details on integer wraparound, see the Integer overflow article.
