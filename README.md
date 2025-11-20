# Jenkins–Maven–SonarQube–Nexus CI/CD Pipeline  
## vProfile Project – Complete DevOps Implementation

This repository contains a fully automated CI/CD pipeline for the **vProfile Application** using Jenkins, Maven, SonarQube, Checkstyle, Nexus Repository Manager, and Slack notifications.

---

## 📌 CI/CD Pipeline Diagram (Text Format)

GitHub → Fetch Code → Build (Maven) → Unit Tests → Checkstyle →
SonarQube Analysis → Quality Gate → Upload to Nexus → Slack Notification

![CI/CD Pipeline Diagram](diagram.png)


---

## 🚀 Overview

This project demonstrates industry-standard DevOps practices:

- Automated Code Fetch  
- Maven Build & Packaging  
- Unit Testing  
- Static Code Analysis (Checkstyle)  
- SonarQube Scanning + Quality Gates  
- Artifact Upload to Nexus  
- Slack Notifications  
- Fully automated **Jenkins Declarative Pipeline**

---

## 🔄 Pipeline Workflow

### **1. Fetch Code**
Clones the repository (main branch) from GitHub.

### **2. Build**

mvn install -DskipTests

- Generates the `.war` file  
- Archives artifacts inside Jenkins

### **3. Unit Testing**

mvn test

Executes JUnit test cases.

### **4. Checkstyle Analysis**
Runs the Maven Checkstyle plugin and produces:

checkstyle-result.xml


### **5. SonarQube Scan**
The pipeline sends:
- Java source code  
- Compiled binaries  
- JUnit Reports  
- JaCoCo Coverage  
- Checkstyle Violations  

### **6. Quality Gate Check**
- Jenkins waits for SonarQube results  
- Build **fails** if Quality Gate fails  

### **7. Nexus Upload**
Artifact uploaded:

target/vprofile-v2.war

Uploaded to repository:


vprofile-repo


### **8. Slack Notification**
Final status sent to Slack with:
- Build number  
- Job name  
- Build URL  

---

## 📂 Jenkinsfile Stage Summary


Fetch Code
→ Build
→ Unit Test
→ Checkstyle
→ Sonar Analysis
→ Quality Gate
→ Upload Artifact
→ Slack Alerts


---

## 🔧 Technologies Used

| Tool / Technology | Purpose |
|-------------------|---------|
| Jenkins | CI/CD Orchestration |
| Maven 3.9 | Build & Dependency Management |
| JDK 17 | Java Compilation |
| Checkstyle | Code Formatting |
| SonarQube | Code Quality |
| Nexus 3 | Artifact Repository |
| Slack | Notifications |
| GitHub | Version Control |

---

## 🛠️ Pre-Requisites

### **Jenkins Setup**
- Maven → `Maven3.9`  
- JDK → `JDK17`  
- Sonar Scanner → `sonar6.2`  
- Sonar Server → `sonarserver`  
- Credentials:
  - `nexuslogin`  
  - Slack Token  

### **Nexus**
Create a hosted repository:

vprofile-repo


### **SonarQube**
- Project Key: `vprofile`  
- Quality Gate configured  
- JaCoCo, JUnit, Checkstyle enabled  

---

## 📦 Generated Artifact

target/vprofile-v2.war


Version format:


<BUILD_ID>-<BUILD_TIMESTAMP>
e.g., 23-20241115_112030


---

## 🧪 Running the Pipeline

1. Create a Jenkins Pipeline job  
2. Select **Pipeline script from SCM**  
3. Provide repository URL  
4. Build  
5. Jenkins executes all stages automatically  

---

## 🙌 Contribution

Feel free to contribute by adding:

- Docker Build/Push  
- AWS Deployment  
- Kubernetes Deployment  
- Terraform Automation  

Pull Requests are welcome!

---


