<h1>JQ Intro Documentation</h1>

<h2>Table of Contents</h2>
<ul>
  <li><a href="#what-is-jq">What is jq</a></li>
  <li><a href="#why-use-jq">Why Use jq</a></li>
  <li><a href="#key-features-of-jq">Features of jq</a></li>
  <li><a href="#Conclusion">Conclusion</a></li>
  <li><a href="#Contacts">Contacts</a></li>
  <li><a href="#References">References</a></li>
</ul>

<h2 id="what-is-jq">What is jq</h2>
<p>
jq is a stream-oriented JSON processor that takes JSON input, applies transformations (defined by a filter), and produces JSON (or other formats) as output.
</p>
<ul>
  <li><b>Written in C</b>: Fast and efficient.</li>
  <li><b>Available on most platforms</b>: Linux, macOS, and Windows (via WSL or native builds).</li>
  <li><b>Open-source</b>: Licensed under the MIT license.</li>
</ul>

<h2 id="why-use-jq">Why Use jq</h2>
<p>
JSON (JavaScript Object Notation) is a widely used data format for APIs, configuration files, and data storage. However, parsing and manipulating JSON from the command line or scripts can be cumbersome without the right tools.
</p>
<p>
<b>jq</b> is a lightweight, powerful, and flexible command-line JSON processor that allows you to:
</p>
<ul>
  <li>Filter, transform, and extract data from JSON structures easily.</li>
  <li>Format and prettify JSON for better readability.</li>
  <li>Perform complex operations like sorting, mapping, and reducing JSON data.</li>
  <li>Integrate seamlessly with shell scripts, APIs, and other command-line tools (e.g., curl).</li>
</ul>

<h2 id="key-features-of-jq">Key Features of jq</h2>

<h3>1. Simple Filtering</h3>
<pre><code class="language-sh">
echo '{"name": "Alice", "age": 30}' | jq '.name'
# Output: "Alice"
</code></pre>

<h3>2. Advanced Queries</h3>
<pre><code class="language-sh">
echo '{"user": {"name": "Bob", "age": 25}}' | jq '.user.name'
# Output: "Bob"
</code></pre>

<h3>3. Pipelining</h3>
<pre><code class="language-sh">
echo '[{"id": 1}, {"id": 2}]' | jq '.[] | .id'
# Output: 1 and 2 (one per line)
</code></pre>

<h3>4. Array & Object Manipulation</h3>
<p>Slice arrays:</p>
<pre><code class="language-sh">
echo '[1, 2, 3, 4]' | jq '.[1:3]'
# Output: [2, 3]
</code></pre>
<p>Map & Transform:</p>
<pre><code class="language-sh">
echo '[1, 2, 3]' | jq 'map(. * 2)'
# Output: [2, 4, 6]
</code></pre>

<h3>5. Conditional Logic</h3>
<pre><code class="language-sh">
echo '{"age": 20}' | jq 'if .age >= 18 then "Adult" else "Minor" end'
# Output: "Adult"
</code></pre>

<h3>6. String & Math Operations</h3>
<p>String interpolation:</p>
<pre><code class="language-sh">
echo '{"name": "Charlie"}' | jq '"Hello, \(.name)!"'
# Output: "Hello, Charlie!"
</code></pre>
<p>Math calculations:</p>
<pre><code class="language-sh">
echo '{"x": 5, "y": 3}' | jq '.x + .y'
# Output: 8
</code></pre>

<h3>7. Format Conversion</h3>
<pre><code class="language-sh">
echo '[{"name": "Alice"}, {"name": "Bob"}]' | jq -r '.[] | .name'
# Output: Alice\nBob
</code></pre>

<h3>8. Error Handling</h3>
<pre><code class="language-sh">
echo '{"a": 1}' | jq '.b // "default"'
# Output: "default"
</code></pre>

<h3>9. Custom Functions</h3>
<pre><code class="language-sh">
echo '10' | jq 'def double: . * 2; double'
# Output: 20
</code></pre>

<h3> Conclusion</h3>
<p>
In this in-depth article, we covered some of the basic capabilities that <code>jq</code> provides for processing and manipulating JSON via the command line.
</p>

<h3> Contacts</h3>
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Email Address</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Shubham Prasad</td>
      <td><a href="mailto:shubham.prasad.snaatak@mygurukulam.co">shubham.prasad.snaatak@mygurukulam.co</a></td>
    </tr>
  </tbody>
</table>

<h3>References</h3>
<table>
  <thead>
    <tr>
      <th>Links</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="https://maven.apache.org/what-is-maven.html">DigitalOcean Tutorial</a></td>
      <td>Intro & Installation of POM</td>
    </tr>
  </tbody>
</table>

