<details>
<summary><h1>Standard Operating Procedure (SOP) for pom.xml</h1></summary>

## Comprehensive Step-by-Step Installation & Configuration Guide


| Author   | Created on | Version  | Internal-Reviewer | L0-Reviewer  | L1-Reviewer | L2-Reviewer  |
|----------|------------|----------|-------------------|--------------|-------------|--------------|
| Shubham  | 14-04-25   | version 1| Komal Jaiswal     | Gaurav Singla| Rahul Gupta | Mahesh Kumar |

### 1. Purpose
This document provides a standardized procedure for installing  <code>pom.xml</code> file in Maven-based Java projects.

### 2. Scope
This SOP defines the process for generating and installing a Maven pom.xml to manage project dependencies and build metadata. It ensures consistent local artifact installation for reuse across multiple Java-based applications.

### 3. Prerequisites
#### 3.1 Software Requirements
- Java JDK (8 or later)
- Apache Maven (3.6.0+)
 

### 4. Installation Steps
##### Step 1: Update System Packages
  ```sh
  sudo apt update && sudo apt upgrade -y  # For Debian/Ubuntu
  ```
##### Step 2: Install Java 
  ```sh
  sudo apt install openjdk-11-jdk
  ```
##### Step 3: Install Maven  
  ```sh
  sudo apt install maven -y
  ```
##### Step 3: Create Pom.xml file   
   ```sh
   mvn archetype:generate -DgroupId=com.yourcompany -DartifactId=your-project -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
   ```

### 4. Examples
```sh
mvn archetype:generate   -DgroupId=com.opstree.microservice   -DartifactId=salary   -Dversion=0.1.0-RELEASE   -Dpackage=com.opstree.microservice.salary   -DarchetypeArtifactId=maven-archetype-quickstart   -DinteractiveMode=false
```
| Flag | Meaning |
|------|---------|
| `-DgroupId` | Base package / organization name (com.opstree.microservice) |
| `-DartifactId` | Project/module name (salary) |
| `-Dversion` | Project version (0.1.0-RELEASE) |
| `-Dpackage` | Java package name for generated classes (com.opstree.microservice.salary) |
| `-DarchetypeArtifactId` | Template used to generate project (maven-archetype-quickstart gives a basic Java setup) |
| `-DinteractiveMode=false` | Skips the interactive prompt and runs immediately |

### 5. Result
After running the command:

- You'll get a folder named `salary`
- Inside that folder, you'll have:
  - A `pom.xml` with your details
  - Source code structure:
    ```
    salary/
    ├── pom.xml
    └── src
        ├── main
        │   └── java
        │       └── com/opstree/microservice/salary/App.java
        └── test
            └── java
                └── com/opstree/microservice/salary/AppTest.java
    ```
 ### 6. Contacts
| Name | Email Address |
|------|---------------|
| Shubham Prasad | [shubham.prasad.snaatak@mygurukulam.co](mailto:shubham.prasad.snaatak@mygurukulam.co) |

### 7. References
| Links | Descriptions |
|-------|--------------|
| [DigitalOcean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-18-04) | Intro & Installation of Gunicorn |
</details>
