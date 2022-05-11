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
