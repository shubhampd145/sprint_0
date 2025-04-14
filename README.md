<div align="center">
  <h1>Kernel Parameter Management with sysctl</h1>
  <h3>Ubuntu System Tuning for Performance and Security</h3>
</div>

<h2>📜 Purpose</h2>
<p>This Standard Operating Procedure (SOP) describes the proper procedures for viewing, applying, and persisting kernel parameter changes using <code>sysctl</code> on Ubuntu systems for performance optimization and security hardening.</p>

<h2>🌐 Scope</h2>
<p>Applies to all Ubuntu Linux systems where kernel parameter tuning is required.</p>

<h2>🔑 Prerequisites</h2>
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

<h2>💡 Example Parameters</h2>
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

<div class="warning">
<strong>⚠️ Warning:</strong> Improper kernel parameter changes can affect system stability. Always test changes in a non-production environment first.
</div>
