<a href="Design.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;
<a href="Issues/Main.md">Next &gt;</a>
<hr>
The eight language commands each consist of a single character:
<table class="ws-table-all notranslate">
  <tr>
    <th>Command</th>
    <th>Meaning</th>
  </tr>
  <tr>
    <td><code>&gt;</code></td>
    <td>Increment the data pointer (to point to the next cell to the right).</td>
  </tr>
  <tr>
    <td><code>&lt;</code></td>
    <td>Decrement the data pointer (to point to the next cell to the left).</td>
  </tr>
  <tr>
    <td><code>+</code></td>
    <td>Increment (increase by one) the byte at the data pointer.</td>
  </tr>
  <tr>
    <td><code>-</code></td>
    <td>Decrement (decrease by one) the byte at the data pointer.</td>
  </tr>
  <tr>
    <td><code>.</code></td>
    <td>Output the byte at the data pointer.</td>
  </tr>
  <tr>
    <td><code>,</code></td>
    <td>Accept one byte of input, storing its value in the byte at the data pointer.</td>
  </tr>
  <tr>
    <td><code>[</code></td>
    <td>If the byte at the data pointer is zero, then instead of moving the instruction pointer <b>forward</b> to the next command, jump it forward to the command after the <b>matching</b> <code>[</code> command.</td>
  </tr>
  <tr>
    <td><code>]</code></td>
    <td>If the byte at the data pointer is nonzero, then instead of moving the instruction pointer <b>back</b> to the next command, jump it forward to the command after the <b>matching</b> <code>]</code> command.</td>
  </tr>
</table>
(Alternatively, the <code>]</code> command may instead be translated as an unconditional jump to the corresponding <code>[</code> command, or vice versa; programs will behave the same but will run more slowly, due to unnecessary double searching.)
<br>
<code>[</code> and <code>]</code> match as parentheses usually do: each <code>[</code> matches exactly one <code>]</code> and vice versa, the <code>[</code> comes first, and there can be no unmatched <code>[</code> or <code>]</code> between the two.
<hr>
Brainfuck programs can be translated into C using the following substitutions, assuming ptr is of type char* and has been initialized to point to an array of zeroed bytes:
<table class="ws-table-all notranslate">
  <tr>
    <th>Command</th>
    <th>C equivalent</th>
  </tr>
  <tr>
    <td><code>&gt;</code></td>
    <td><code>++ptr;</code></td>
  </tr>
  <tr>
    <td><code>&lt;</code></td>
    <td><code>--ptr;</code></td>
  </tr>
  <tr>
    <td><code>+</code></td>
    <td><code>++*ptr;</code></td>
  </tr>
  <tr>
    <td><code>-</code></td>
    <td><code>--*ptr;</code></td>
  </tr>
  <tr>
    <td><code>.</code></td>
    <td><code>putchar(*ptr);</code></td>
  </tr>
  <tr>
    <td><code>,</code></td>
    <td><code>*ptr = getchar();</code></td>
  </tr>
  <tr>
    <td><code>[</code></td>
    <td><code>while (*ptr) {</code></td>
  </tr>
  <tr>
    <td><code>]</code></td>
    <td><code>}</code></td>
  </tr>
</table>
