
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
