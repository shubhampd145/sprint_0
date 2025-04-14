<div align="left">
  
  <h3>Software Application</h3>
</div>

<table border="1" cellpadding="5" cellspacing="0">
  <thead>
    <tr>
      <th>Author</th>
      <th>Created on</th>
      <th>Version</th>
      <th>Last updated by</th>
      <th>Last edited on</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Shubham</td>
      <td>14-04-25</td>
      <td>version 1</td>
      <td>14-4-25</td>
      <td>14-4-25</td>
    </tr>
  </tbody>
</table>

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

<h2> Procedures</h2>

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

<h2>Common Security-Hardening Parameters</h2>

<h3>Network Security Performance Parameters</h3>
<table border="1" cellpadding="5" cellspacing="0">
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

<h3>Security Tuning Parameters</h3>
<table border="1" cellpadding="5" cellspacing="0">
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
      <td>Prevents packet forwarding</td>
    </tr>
    <tr>
      <td>accept_redirects = 0</td>
      <td>Disable ICMP redirects</td>
      <td>Secure servers</td>
      <td>Prevent MitM attacks</td>
    </tr>
    <tr>
      <td>tcp_syncookies = 1</td>
      <td>Enable SYN flood protection</td>
      <td>Public web/API server</td>
      <td>Mitigates DoS</td>
    </tr>
    <tr>
      <td>accept_source_route = 0</td>
      <td>Block source-routed packets</td>
      <td>Any cloud server</td>
      <td>Prevent spoofing</td>
    </tr>
    <tr>
      <td>log_martians = 1</td>
      <td>Log suspicious packets</td>
      <td>Security hardening</td>

      <h3>Contact Information</h3>
<table border="1" cellpadding="5" cellspacing="0">
  <thead>
    <tr>
      <th>Name</th>
      <th>Email address</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Shubham</td>
      <td><a href="shubham.prasad.snaatak@mygurukulam.co">shubham.prasad.snaatak@mygurukulam.co</a></td>
    </tr>
  </tbody>
</table>

