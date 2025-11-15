# Jenkins-Maven-Sonar-Nexus-Pipeline-Vprofile-Project
Jenkins-Maven-Sonar-Nexus-Pipeline – vProfile Project

This repository contains a complete CI/CD pipeline implementation for the vProfile Application using Jenkins, Maven, SonarQube, Checkstyle, Nexus Repository Manager, and Slack Notifications.

✅ SVG CI/CD Pipeline Diagram
<svg width="900" height="600" xmlns="http://www.w3.org/2000/svg">

  <!-- Title -->
  <text x="300" y="40" font-size="26" font-weight="bold" fill="#333">
    CI/CD Pipeline – vProfile Project
  </text>

  <!-- Box Style -->
  <style>
    .box {
      fill: #f5f5f5;
      stroke: #333;
      stroke-width: 2;
      rx: 12;
      ry: 12;
    }
    .label {
      font-size: 18px;
      font-family: Arial, sans-serif;
      fill: #333;
      font-weight: bold;
    }
  </style>

  <!-- Step 1: GitHub -->
  <rect x="330" y="80" width="240" height="60" class="box"/>
  <text x="360" y="120" class="label">Fetch Code (GitHub)</text>

  <!-- Arrow -->
  <line x1="450" y1="140" x2="450" y2="170" stroke="#333" stroke-width="2"/>
  <polygon points="450,170 445,160 455,160" fill="#333"/>

  <!-- Step 2: Build -->
  <rect x="330" y="170" width="240" height="60" class="box"/>
  <text x="390" y="210" class="label">Build (Maven)</text>

  <!-- Arrow -->
  <line x1="450" y1="230" x2="450" y2="260" stroke="#333" stroke-width="2"/>
  <polygon points="450,260 445,250 455,250" fill="#333"/>

  <!-- Step 3: Unit Test -->
  <rect x="330" y="260" width="240" height="60" class="box"/>
  <text x="390" y="300" class="label">Unit Tests</text>

  <!-- Arrow -->
  <line x1="450" y1="320" x2="450" y2="350" stroke="#333" stroke-width="2"/>
  <polygon points="450,350 445,340 455,340" fill="#333"/>

  <!-- Step 4: Checkstyle -->
  <rect x="330" y="350" width="240" height="60" class="box"/>
  <text x="375" y="390" class="label">Checkstyle Analysis</text>

  <!-- Arrow -->
  <line x1="450" y1="410" x2="450" y2="440" stroke="#333" stroke-width="2"/>
  <polygon points="450,440 445,430 455,430" fill="#333"/>

  <!-- Step 5: SonarQube -->
  <rect x="330" y="440" width="240" height="60" class="box"/>
  <text x="365" y="480" class="label">SonarQube Analysis</text>

  <!-- Arrow -->
  <line x1="450" y1="500" x2="450" y2="530" stroke="#333" stroke-width="2"/>
  <polygon points="450,530 445,520 455,520" fill="#333"/>

  <!-- Step 6: Quality Gate -->
  <rect x="330" y="530" width="240" height="60" class="box"/>
  <text x="380" y="570" class="label">Quality Gate</text>


  <!-- Right Path: Nexus Upload -->
  <line x1="570" y1="560" x2="650" y2="560" stroke="#333" stroke-width="2"/>
  <polygon points="650,560 640,555 640,565" fill="#333"/>

  <rect x="650" y="520" width="230" height="80" class="box"/>
  <text x="700" y="565" class="label">Upload to Nexus</text>

  <!-- Left Path: Slack -->
  <line x1="330" y1="560" x2="250" y2="560" stroke="#333" stroke-width="2"/>
  <polygon points="250,560 260,555 260,565" fill="#333"/>

  <rect x="20" y="520" width="230" height="80" class="box"/>
  <text x="70" y="565" class="label">Slack Notification</text>

</svg>


The project demonstrates industry-standard DevOps practices, including:

Automated Code Fetch

Compilation & Packaging

Unit Testing

Static Code Analysis (Checkstyle)

SonarQube Scan + Quality Gate

Artifact Upload to Nexus

Slack Notifications

This pipeline is fully automated using a Jenkins Declarative Pipeline.

🚀 Pipeline Workflow

The Jenkins pipeline executes the following sequence:

Fetch Code

Clones the repository from GitHub (main branch).

Build Stage

Executes mvn install -DskipTests

Generates .war package

Archives artifacts inside Jenkins

Unit Testing

Executes mvn test

Ensures code functionality & JUnit validation

Checkstyle Analysis

Runs Maven Checkstyle plugin

Ensures code formatting & quality standards

Generates checkstyle-result.xml

SonarQube Code Analysis

Uses sonar-scanner

Sends following data to SonarQube:

Source code

Java binaries

JUnit reports

JaCoCo coverage

Checkstyle violations

Quality Gate Validation

Pipeline pauses until SonarQube completes analysis

Fails the pipeline if the Quality Gate is not met

Upload Artifact to Nexus

WAR file uploaded to hosted repository vprofile-repo

Uses Nexus3 Artifact Uploader plugin

Slack Notifications

Sends success/failure message to Slack channel

Includes build number, job name, build URL

📂 Jenkinsfile Summary

pipeline {
  Fetch Code → Build → Unit Test → Checkstyle → Sonar Analysis → Quality Gate → Upload Artifact → Slack Alerts
}

🔧 Technologies Used
Tool / Technology	Purpose
Jenkins	CI/CD Orchestration
Maven 3.9	Build & Dependency Management
JDK 17	Java Compilation
Checkstyle	Static Code Formatting Checks
SonarQube	Code Quality, Bugs, Vulnerabilities
Nexus 3	Artifact Repository (.war uploads)
Slack	Build Notifications
GitHub	Version Control
🛠️ Pre-Requisites

Before running this pipeline, ensure:

In Jenkins

Maven tool configured as: Maven3.9

JDK configured as: JDK17

Sonar Scanner installed as: sonar6.2

SonarQube server configured with name: sonarserver

Credentials created:

nexuslogin → Username/Password for Nexus

Slack token (in Slack plugin config)

In Nexus

Hosted Maven repository created:

Name: vprofile-repo

In SonarQube

Project created with key: vprofile

Quality Gate configured

JaCoCo, JUnit, Checkstyle rules enforced

📦 Generated Artifact

The Jenkins pipeline uploads the following file to Nexus:

target/vprofile-v2.war

Versioning format:
<BUILD_ID>-<BUILD_TIMESTAMP>

Example:
23-20241115_112030

📸 Pipeline Diagram
GitHub → Fetch Code → Build → Unit Test → Checkstyle → Sonar Scan → Quality Gate → Upload to Nexus → Slack Notification

🧪 Running the Pipeline

Create a Jenkins Pipeline job

Point it to this repository URL

Select "Pipeline script from SCM"

Run the build

Jenkins will automatically execute all stages end-to-end.

🙌 Contribution

Feel free to fork this repository and enhance the pipeline:

Add Docker Build/Push

Add AWS Deployment

Add Kubernetes Deployment

Add Terraform automation

Pull Requests are welcome!
