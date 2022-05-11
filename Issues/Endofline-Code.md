<a href="/Issues/Array-Size.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="/Issues/Endofline-Behavior.md">Next &gt;</a>
<hr>
Different operating systems (and sometimes different programming environments) use subtly different versions of ASCII. The most important difference is in the code used for the end of a line of text. MS-DOS and Microsoft Windows use a CRLF, i.e. a 13 followed by a 10, in most contexts. UNIX and its descendants (including Linux and macOS) and Amigas use just 10, and older Macs use just 13. It would be difficult if brainfuck programs had to be rewritten for different operating systems. However, a unified standard was easy to create. Urban Müller's compiler and his example programs use 10, on both input and output; so do a large majority of existing brainfuck programs; and 10 is also more convenient to use than CRLF. Thus, brainfuck implementations should make sure that brainfuck programs that assume newline = 10 will run properly; many do so, but some do not.
<br>
This assumption is also consistent with most of the world's sample code for C and other languages, in that they use "\n", or 10, for their newlines. On systems that use CRLF line endings, the C standard library transparently remaps "\n" to "\r\n" on output and "\r\n" to "\n" on input for streams not opened in binary mode.
