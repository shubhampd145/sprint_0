<details>
 <summary><h1>Standard Operating Procedure (SOP) For SYSCTL</h1></summary>


<div align="left">
  <h2>Documentation Of Managing Kernel Parameters with sysctl for Performance or Security Tuning</h2>
</div>

| Author   | Created on | Version  | Internal-Reviewer | L0-Reviewer  | L1-Reviewer | L2-Reviewer  |
|----------|------------|----------|-------------------|--------------|-------------|--------------|
| Shubham  | 14-04-25   | version 1| Komal Jaiswal     | Gaurav Singla| Rahul Gupta | Mahesh Kumar |

## 1. Purpose
This Standard Operating Procedure (SOP) describes the proper procedures for `viewing`, `applying`, and `persisting` kernel parameter changes using `sysctl` on Ubuntu systems for performance optimization and security hardening.

## 2. Scope
Applies to all Ubuntu Linux systems where kernel parameter tuning is required.

## Prerequisites
- Administrative/sudo privileges
- Basic command line proficiency
- Understanding of kernel parameters and their implications

## 3. Procedures

### 1. Viewing Current Kernel Parameters

#### View all current parameters:
```bash
sudo sysctl -a
```

#### View specific parameter:
```bash
sudo sysctl <parameter.name>
# Example:
sudo sysctl vm.swappiness
```

### 2. Temporarily Modifying Parameters (applies until reboot)

#### Set a single parameter:
```bash
sudo sysctl -w <parameter.name>=<value>
# Example:
sudo sysctl -w vm.swappiness=10
```

#### Verify the change took effect:
```bash
cat /proc/sys/vm/<parameter.name>
   or 
sysctl <parameter.name>
```

### 3. Permanently Modifying Parameters (persists across reboots)

1. Open the sysctl configuration file:
   ```bash
   sudo nano /etc/sysctl.conf
   ```
  
2. Add or modify parameters at the end of the file:
   ```bash
   # Example parameter
   vm.swappiness=100
   ```
  
3. Save and close the file (Ctrl+O, Enter, Ctrl+X in nano)
  
4. Apply changes without rebooting:
   ```bash
   sudo sysctl -p
   ```

## 4. Example Parameters
| Parameter | Description | Recommended Value |
|-----------|-------------|-------------------|
| `vm.swappiness` | Controls tendency to swap memory | 10-60 (lower reduces swapping) |
| `net.ipv4.tcp_syncookies` | SYN flood protection | 1 (enabled) |

## 5. Common Security-Hardening Parameters

### Performance Parameters
| Parameter | Real-World Use Case | Why Tune It? | Result |
|-----------|---------------------|--------------|--------|
| vm.swappiness = 10 | Apps needing RAM (e.g., DB, Java app) | Avoid slow swap | Faster performance |
| fs.file-max = 2097152 | High-concurrency apps (e.g., Nginx, Node.js) | Prevent FD exhaustion | Stable under load |
| vm.vfs_cache_pressure = 50 | Frequent file access (e.g., web apps, configs) | Keep file cache longer | Faster disk performance |

### Security Tuning Parameters
| Parameter | Description | Use Case | Why Set It |
|-----------|-------------|----------|------------|
| net.ipv4.ip_forward = 0 | Disable IP routing | Web server or DB server | Prevents packet forwarding |
| accept_redirects = 0 | Disable ICMP redirects | Secure servers | Prevent MitM attacks |
| tcp_syncookies = 1 | Enable SYN flood protection | Public web/API server | Mitigates DoS |
| accept_source_route = 0 | Block source-routed packets | Any cloud server | Prevent spoofing |
| log_martians = 1 | Log suspicious packets | Security hardening | Improved monitoring |



## 6. Contacts
| Name | Email Address |
|------|---------------|
| Shubham Prasad | [shubham.prasad.snaatak@mygurukulam.co](mailto:shubham.prasad.snaatak@mygurukulam.co) |

</details>
