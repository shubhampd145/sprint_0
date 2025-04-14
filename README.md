<div align="center">
  <h1>Kernel Parameter Management with sysctl</h1>
  <h3>Ubuntu System Tuning for Performance and Security</h3>
</div>

<h2> Purpose</h2>
<p>This Standard Operating Procedure (SOP) describes the proper procedures for viewing, applying, and persisting kernel parameter changes using <code>sysctl</code> on Ubuntu systems for performance optimization and security hardening.</p>

<h2> Scope</h2>
<p>Applies to all Ubuntu Linux systems where kernel parameter tuning is required.</p>

<h2> Prerequisites</h2>
<ul>
  <li><code>Administrative/sudo privileges</code></li>
  <li>Basic command line proficiency</li>
  <li>Understanding of kernel parameters and their implications</li>
</ul>

<h2>⚙️ Procedures</h2>

<h3>1. Viewing Current Kernel Parameters</h3>

<h4>View all current parameters:</h4>
<div class="highlight highlight-source-shell">
<pre>sudo sysctl -a</pre>
</div>

<h4>View specific parameter:</h4>
<div class="highlight highlight-source-shell">
<pre>sudo sysctl &lt;parameter.name&gt;
# Example:
sudo sysctl vm.swappiness</pre>
</div>

<h3>2. Temporarily Modifying Parameters (applies until reboot)</h3>

<h4>Set a single parameter:</h4>
<div class="highlight highlight-source-shell">
<pre>sudo sysctl -w &lt;parameter.name&gt;=&lt;value&gt;
# Example:
sudo sysctl -w vm.swappiness=10</pre>
</div>

<h4>Verify the change took effect:</h4>
<div class="highlight highlight-source-shell">
<pre>cat /proc/sys/vm/&lt;parameter.name&gt;
   or 
sysctl &lt;parameter.name&gt;</pre>
</div>

<h3>3. Permanently Modifying Parameters (persists across reboots)</h3>

<ol>
  <li>Open the sysctl configuration file:
    <div class="highlight highlight-source-shell">
    <pre>sudo nano /etc/sysctl.conf</pre>
    </div>
  </li>
  
  <li>Add or modify parameters at the end of the file:
    <div class="highlight highlight-source-shell">
    <pre># Example parameter
vm.swappiness=100</pre>
    </div>
  </li>
  
  <li>Save and close the file (<kbd>Ctrl+O</kbd>, <kbd>Enter</kbd>, <kbd>Ctrl+X</kbd> in nano)</li>
  
  <li>Apply changes without rebooting:
    <div class="highlight highlight-source-shell">
    <pre>sudo sysctl -p</pre>
    </div>
  </li>
</ol>

<h2>Example Parameters</h2>
<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
    <th>Recommended Value</th>
  </tr>
  <tr>
    <td><code>vm.swappiness</code></td>
    <td>Controls tendency to swap memory</td>
    <td>10-60 (lower reduces swapping)</td>
  </tr>
  <tr>
    <td><code>net.ipv4.tcp_syncookies</code></td>
    <td>SYN flood protection</td>
    <td>1 (enabled)</td>
  </tr>
</table>

<h2>Performance and Security Tuning</h2>

<h3>Increase TCP Buffer Sizes</h3>
<pre>
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
</pre>

<h3>TCP Window Scaling and Timestamps</h3>
<pre>
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_window_scaling = 1
</pre>

<h3>Increase Connection Backlog Queue</h3>
<pre>
net.core.somaxconn = 4096
net.ipv4.tcp_max_syn_backlog = 4096
</pre>

<h3>Enable TCP Fast Open</h3>
<pre>
net.ipv4.tcp_fastopen = 3
</pre>

<h3>Reduce TIME_WAIT Duration</h3>
<pre>
net.ipv4.tcp_fin_timeout = 15
</pre>

<h2>Memory and Swappiness</h2>
<pre>
# Reduce swapping tendency (0-100, lower = less swap)
vm.swappiness = 10

# Increase available file handles
fs.file-max = 2097152

# Cache pressure (higher = more likely to reclaim cache)
vm.vfs_cache_pressure = 50
</pre>

<h3>Performance Tuning Use Cases</h3>
<table border="1">
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Real-World Use Case</th>
      <th>Why Tune It?</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>vm.swappiness = 10</td>
      <td>Apps needing RAM (e.g., DB, Java app)</td>
      <td>Avoid slow swap</td>
      <td>Faster performance</td>
    </tr>
    <tr>
      <td>fs.file-max = 2097152</td>
      <td>High-concurrency apps (e.g., Nginx, Node.js)</td>
      <td>Prevent FD exhaustion</td>
      <td>Stable under load</td>
    </tr>
    <tr>
      <td>vm.vfs_cache_pressure = 50</td>
      <td>Frequent file access (e.g., web apps, configs)</td>
      <td>Keep file cache longer</td>
      <td>Faster disk performance</td>
    </tr>
  </tbody>
</table>

<h2>Common Security-Hardening Parameters</h2>

<h3>Network Security</h3>
<pre>
# Disable IP forwarding (unless router/gateway)
net.ipv4.ip_forward = 0

# Disable ICMP redirects
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0

# Enable SYN flood protection
net.ipv4.tcp_syncookies = 1

# Disable source routing
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0

# Log suspicious packets
net.ipv4.conf.all.log_martians = 1
</pre>

<h3>Kernel Protections</h3>
<pre>
# Restrict kernel pointer access
kernel.kptr_restrict = 2

# Disable unprivileged user namespaces (if not needed)
kernel.unprivileged_userns_clone = 0

# Enable strict ASLR (Address Space Layout Randomization)
kernel.randomize_va_space = 2
</pre>

<h3>Security Use Case Summary</h3>
<table border="1">
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Description</th>
      <th>Use Case</th>
      <th>Why Set It</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>net.ipv4.ip_forward = 0</td>
      <td>Disable IP routing</td>
      <td>Web server or DB server</td>
      <td>Prevents

