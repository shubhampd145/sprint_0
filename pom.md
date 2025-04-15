<details>
<summary><h1>Standard Operating Procedure (SOP) for pom.xml</h1></summary>

## Comprehensive Step-by-Step Installation & Configuration Guide

### Document Control
| Document Title | SOP for pom.xml Setup |
|---------------|----------------------|
| Version       | 1.1                  |
| Created On    | 16-04-25       |
| Version       | v1          |
| Internal-Reviewer   | Komal Jaiswal      |
| L0-Reviewer     | Gaurav Singla                  |  
| L1-Reviewer    |    Rahul Gupta                 |
|L2-Reviewer      |        Mahesh Kumar           |

### 1. Purpose
This document provides a standardized procedure for installing  <code>pom.xml</code> file in Maven-based Java projects.

### 2. Scope
- Applicable to all Java projects using Apache Maven.
- Covers:
  - Initial setup
  - Dependency management
  - Build configurations
  - Best practices

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
</details>
