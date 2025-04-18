# jq Documentation: Introduction

## What is jq?

`jq` is a **stream-oriented** JSON processor that takes JSON input, applies transformations (defined by a *filter*), and produces JSON (or other formats) as output.

- **Written in C**: Fast and efficient and has zero runtime dependencies.
- **Available on most platforms**: Linux, macOS, and Windows (via WSL or native builds)
- **Open-source**: Licensed under the MIT license
  
## Why Use jq?

JSON (JavaScript Object Notation) is a widely used data format for APIs, configuration files, and data storage. However, parsing and manipulating JSON from the command line or scripts can be cumbersome without the right tools.

**jq** is a lightweight, powerful, and flexible command-line JSON processor that allows you to:

- **Filter, transform, and extract** data from JSON structures easily
- **Format and prettify** JSON for better readability
- **Perform complex operations** like sorting, mapping, and reducing JSON data
- **Integrate seamlessly** with shell scripts, APIs, and other command-line tools (e.g., `curl`)


## Key Features of jq

### 1. Simple Filtering
Extract specific fields from JSON:
```sh
echo '{"name": "Alice", "age": 30}' | jq '.name'
# Output: "Alice"
<div class="jq-documentation">

<h1>Key Features of jq</h1>

<section class="feature">
<h2>1. Powerful Filtering</h2>

<div class="example">
<h3>Dot notation for field access:</h3>
<pre><code class="language-sh">echo '{"user": {"name": "Alice"}}' | jq '.user.name'
# Output: "Alice"</code></pre>
</div>

<div class="example">
<h3>Array/object traversal:</h3>
<pre><code class="language-sh">echo '[{"id": 1}, {"id": 2}]' | jq '.[].id'
# Output: 1 and 2 (streamed)</code></pre>
</div>
</section>

<section class="feature">
<h2>2. Pipelining & Transformation</h2>

<div class="example">
<h3>Chain operations like Unix tools:</h3>
<pre><code class="language-sh">echo '[1, 2, 3]' | jq 'map(. * 2) | add'
# Output: 12 (sum of doubled values)</code></pre>
</div>

<div class="example">
<h3>Modify JSON structure on the fly:</h3>
<pre><code class="language-sh">echo '{"x": 5}' | jq '{x: .x, y: (.x * 2)}'
# Output: {"x":5, "y":10}</code></pre>
</div>
</section>

<section class="feature">
<h2>3. Conditional Logic & Functions</h2>

<div class="example">
<h3>if-then-else support:</h3>
<pre><code class="language-sh">echo '{"age": 20}' | jq 'if .age >= 18 then "Adult" else "Minor" end'
# Output: "Adult"</code></pre>
</div>

<div class="example">
<h3>Custom functions:</h3>
<pre><code class="language-sh">echo '5' | jq 'def triple: . * 3; triple'
# Output: 15</code></pre>
</div>
</section>

<section class="feature">
<h2>4. Format Conversion</h2>

<div class="example">
<h3>JSON ↔ Text/CSV:</h3>
<pre><code class="language-sh">echo '[{"name": "Alice"}, {"name": "Bob"}]' | jq -r '.[].name'
# Output: Alice\nBob (raw text)</code></pre>
</div>

<div class="example">
<h3>Pretty-printing:</h3>
<pre><code class="language-sh">echo '{"x":1}' | jq
# Output: {
#   "x": 1
# }</code></pre>
</div>
</section>

<section class="feature">
<h2>5. Error Handling</h2>

<div class="example">
<h3>Default values for missing fields:</h3>
<pre><code class="language-sh">echo '{"a": 1}' | jq '.b // "default"'
# Output: "default"</code></pre>
</div>

<p class="note">Skip malformed JSON with <code>-e</code> (exit code on errors).</p>
</section>

<section class="feature">
<h2>6. Advanced Operations</h2>

<table class="operations">
  <thead>
    <tr>
      <th>Feature</th>
      <th>Example</th>
      <th>Use Case</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Sorting</strong></td>
      <td><code>jq 'sort_by(.age)'</code></td>
      <td>Sort JSON arrays</td>
    </tr>
    <tr>
      <td><strong>Math Ops</strong></td>
      <td><code>jq '.x + .y'</code></td>
      <td>Calculations on JSON fields</td>
    </tr>
    <tr>
      <td><strong>Regex</strong></td>
      <td><code>jq 'match("(foo)")'</code></td>
      <td>Pattern matching in strings</td>
    </tr>
    <tr>
      <td><strong>Flattening</strong></td>
      <td><code>jq 'flatten'</code></td>
      <td>Simplify nested structures</td>
    </tr>
  </tbody>
</table>
</section>

<section class="feature">
<h2>7. Integration-Friendly</h2>

<div class="example">
<h3>Works with APIs (curl/httpie):</h3>
<pre><code class="language-sh">curl https://api.example.com/data | jq '.results[0]'</code></pre>
</div>

<div class="example">
<h3>Embeds in shell scripts:</h3>
<pre><code class="language-sh">count=$(jq '.items | length' data.json)</code></pre>
</div>
</section>

<section class="installation">
<h2>Installation</h2>

<pre><code class="language-sh"># Linux (Debian/Ubuntu)
sudo apt install jq

# macOS (Homebrew)
brew install jq

# Windows (Chocolatey)
choco install jq</code></pre>
</section>

</div>
