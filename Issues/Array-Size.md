<a href="/Issues/Cell-Size.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Issues/Endofline-Code.md">Next &gt;</a>
<hr>
In the classic distribution, the array has 30,000 cells, and the pointer begins at the leftmost cell. Even more cells are needed to store things like the millionth Fibonacci number, and the easiest way to make the language Turing complete is to make the array unlimited on the right.
<br>
A few implementations extend the array to the left as well; this is an uncommon feature, and therefore portable brainfuck programs do not depend on it.
<br>
When the pointer moves outside the bounds of the array, some implementations will give an error message, some will try to extend the array dynamically, some will not notice and will produce undefined behavior, and a few will move the pointer to the opposite end of the array. Some tradeoffs are involved: expanding the array dynamically to the right is the most user-friendly approach and is good for memory-hungry programs, but it carries a speed penalty. If a fixed-size array is used it is helpful to make it very large, or better yet let the user set the size. Giving an error message for bounds violations is very useful for debugging but even that carries a speed penalty unless it can be handled by the operating system's memory protections.
