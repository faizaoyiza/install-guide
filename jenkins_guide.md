# ⚙️ Jenkins CI/CD Project

This project demonstrates the installation, setup, and usage of **Jenkins** for Continuous Integration and Continuous Delivery (CI/CD). It includes installation guides, Freestyle Jobs, and Pipeline automation examples.

---

## 📌 What You’ll Learn
- The concepts of **Continuous Integration (CI)** and **Continuous Delivery (CD)**
- How to install Jenkins on **Ubuntu** and **Windows**
- How to create and manage **Freestyle Jobs**
- How to build and run a **Jenkins Pipeline (Jenkinsfile)**
- How Jenkins integrates into DevOps workflows

---

## 🔹 1. Understanding CI/CD & Jenkins

### What is CI/CD?
- **Continuous Integration (CI):** Developers frequently merge code to the main branch. Jenkins automatically builds and tests the code, catching issues early.
- **Continuous Delivery (CD):** Code is always in a deployable state, ensuring faster and more reliable releases.
- **Continuous Deployment:** Fully automated deployment into production once tests pass.

### Why CI/CD?
- Early bug detection  
- Faster feedback loops  
- Consistency across environments  
- Improved team collaboration  

### Where Jenkins Fits In
Jenkins is the automation server that **orchestrates the CI/CD pipeline**, integrating with Git, Docker, Kubernetes, AWS, and many other tools.

## 📂 Project Structure
```bash
jenkins-project/
├── Jenkinsfile              # Pipeline definition
├── docker-compose.yml       # Optional Jenkins setup in Docker
├── jobs/                    # Example job configs
├── scripts/                 # Shell/automation scripts
└── README.md                # Documentation
---

## 🔹 2. Jenkins Installation

### Ubuntu/Debian
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Java (required by Jenkins)
sudo apt install openjdk-11-jdk -y
java -version

# Add Jenkins repository
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

# Install Jenkins
sudo apt update
sudo apt install jenkins -y

# Start and enable Jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins

# Check status
systemctl status jenkins
```

Access Jenkins: [http://your-server-ip:8080](http://your-server-ip:8080)  

Unlock Jenkins:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```


---

# ⚙️ Jenkins Installation & Setup Guide (Windows)

## 🔧 Step 1: Install Java (Required)

Jenkins requires Java (JDK or JRE 11+). You can use OpenJDK:

1. Download OpenJDK: [https://jdk.java.net/](https://jdk.java.net/)
2. Install or extract it (e.g., to `C:\Program Files\Java\jdk-21`)
3. Set environment variable `JAVA_HOME`:
   - System Properties → Environment Variables → Add `JAVA_HOME`
   - Value: `C:\Program Files\Java\jdk-21`
4. Add `JAVA_HOME\bin` to your system `Path`
5. Verify with:

   ```bash
   java -version
   ```

---
<img width="820" alt="Image" src="https://github.com/user-attachments/assets/b579efbf-f4bd-411c-9495-381a8bff1530" />
## 📥 Step 2: Download Jenkins

1. Go to [https://www.jenkins.io/download/](https://www.jenkins.io/download/)
2. Select **Windows** and download the installer (`jenkins.msi`) or WAR file.

---

## 🖥️ Step 3: Install Jenkins (Windows Installer Method)

1. Run the downloaded `jenkins.msi` file
2. Follow the installation steps (accept defaults or change port as needed)
3. After installation, Jenkins runs as a **Windows service**

---

## 🚀 Step 4: Initial Setup

1. Open Jenkins in your browser:

   ```http
   http://localhost:8080
   ```

   > If you used a different port, replace `8080` accordingly.

2. Retrieve the admin password from:

   ```
   C:\Program Files\Jenkins\secrets\initialAdminPassword
   ```

3. Paste it into the setup screen
4. Choose “Install suggested plugins”
5. Create an admin user and finish setup

---

## 🔧 Common Jenkins Commands (for WAR file method)
<img width="856" alt="Image" src="https://github.com/user-attachments/assets/89604875-462a-4808-923a-a7501a658756" />
If you're running from the WAR file:

```bash
java -jar jenkins.war
```

Optional custom port:

```bash
java -jar jenkins.war --httpPort=9191
```

Then open:

```
http://localhost:9191
```

---

## 🛑 Stopping Jenkins (WAR method)

Simply stop the terminal session running Jenkins, or press `Ctrl+C`.

---

## ✅ Jenkins Is Ready!

- Jenkins Dashboard: `http://localhost:8080`
- Create and manage jobs from the web UI
- Install additional plugins as needed
<img width="944" alt="Image" src="https://github.com/user-attachments/assets/a5cbcc68-e16a-47aa-a59a-45cc20c6f0d9" />
## 🔹 3. Creating a Freestyle Job

1. In Jenkins Dashboard → Click **New Item** → Select **Freestyle Project**.
2. Add project name (e.g., *Hello Jenkins*).
3. Under **Source Code Management**, connect to a GitHub repo (optional).
4. Under **Build Steps**, add:
   ```bash
   echo "Hello Jenkins!"
   ```
5. Save and run the job.

✅ You should see a successful build in the console output.

---

## 🔹 4. Jenkins Pipelines (Jenkinsfile)

Pipelines define CI/CD as code.

### Example Jenkinsfile
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the app...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to server...'
            }
        }
    }
}
```

Steps:
1. Create a new **Pipeline Job** in Jenkins.
2. Point it to a repo containing this `Jenkinsfile`.
3. Run the job → Jenkins executes Build → Test → Deploy.

---

## 🔹 5. Integrations & Next Steps
- Integrate with **GitHub Webhooks** to trigger builds on commits.
- Use **Docker** to build/push images in pipelines.
- Deploy apps to **Kubernetes** or **AWS**.
- Add monitoring and alerts for Jenkins jobs.

---
