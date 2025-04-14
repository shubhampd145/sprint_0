# sprint_0
<div align="center">
  <h1>Kernel Parameter Management with sysctl on Ubuntu</h1>
</div>

<h2>Purpose</h2>
<p>This SOP describes the proper procedures for viewing, applying, and persisting kernel parameter changes using sysctl on Ubuntu systems for performance optimization and security hardening.</p>

<h2>Scope</h2>
<p>Applies to all Ubuntu Linux systems where kernel parameter tuning is required.</p>

<h2>Prerequisites</h2>
<ul>
  <li>Administrative/sudo privileges</li>
  <li>Basic command line proficiency</li>
  <li>Understanding of kernel parameters and their implications</li>
</ul>

<h2>Procedures</h2>

<h3>1. Viewing Current Kernel Parameters</h3>

<h4>View all current parameters:</h4>
<pre><code>sudo sysctl -a</code></pre>

<h4>View specific parameter:</h4>
<pre><code>sudo sysctl &lt;parameter.name&gt;
# Example:
sudo sysctl net.ipv4.ip_forward</code></pre>

<h4>View parameters from /etc/sysctl.conf:</h4>
<pre><code>sudo sysctl -p</code></pre>

<h3>2. Temporarily Modifying Parameters (applies until reboot)</h3>

<h4>Set a single parameter:</h4>
<pre><code>sudo sysctl -w &lt;parameter.name&gt;=&lt;value&gt;
# Example:
sudo sysctl -w net.ipv4.tcp_syncookies=1</code></pre>

<h4>Verify the change took effect:</h4>
<pre><code>sudo sysctl &lt;parameter.name&gt;</code></pre>

<h3>3. Permanently Modifying Parameters (persists across reboots)</h3>

<ol>
  <li>Open the sysctl configuration file:
    <pre><code>sudo nano /etc/sysctl.conf</code></pre>
  </li>
  
  <li>Add or modify parameters at the end of the file:
    <pre># Example security hardening parameters
net.ipv4.tcp_syncookies = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1</pre>
  </li>
  
  <li>Save and close the file (Ctrl+O, Enter, Ctrl+X in nano)</li>
  
  <li>Apply changes without rebooting:
    <pre><code>sudo sysctl -p</code></pre>
  </li>
</ol>
