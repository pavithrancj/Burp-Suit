# 🔐  Burp Suite Security Assessment 
This report summarizes two separate penetration testing labs performed using **Burp Suite**:
- **Web Application Security Testing**
- **Mobile Application Security Assessment**

---

## 🧪 1. Web Application Exploitation 

### 🎯 Objectives
- Use Burp Suite as a web proxy.
- Discover and exploit vulnerabilities in a web application.
- Perform privilege escalation through command injection.

### 🛠 Tools Used
- **Burp Suite**
- **Kali Linux VM** 
- **Lab VM Provided by my college** 

### 📌 Key Steps

#### 🔹 Network Discovery
- Identified both VMs and confirmed HTTP access to the target VM.

#### 🔹 Content Enumeration
- Used `dirb` to find `admin.php`.

#### 🔹 Burp Proxy Configuration
- Configured Firefox to route traffic through Burp for interception.
- Intercepted login attempts and redirected them to `admin.php`.

#### 🔹 Command Injection via Burp Repeater
- Modified HTTP requests to test for OS command injection.
- Confirmed execution by injecting shell commands via the request URL.

#### 🔹 Reverse Shell Execution
- Hosted `php-reverse-shell.php` using Python HTTP server on Kali.
- Injected command to download the script on the target machine.
- Gained reverse shell via Netcat listener.

#### ✅ Outcome
- Successful reverse shell gained through command injection on the web server.


## 📄 Full Lab Reports

- 🔗 [Full Web Application Burp Lab Report](https://github.com/pavithrancj/Burp-Suit/blob/main/Burp%20Suit_Web%20Exploit.pdf)
---

## 📱 2. Mobile Application Security Assessment

### 🎯 Objectives
- Intercept mobile traffic using Burp Suite via MITM.
- Handle HTTPS interception by installing Burp’s CA certificate.
- Understand how Android handles SSL/TLS connections.

### 🛠 Tools Used
- **Burp Suite (Community Edition)**
- **Windows 11 VM (via VMware Fusion)**
- **Android Emulator (Genymotion or Android x86)**
- **Kali Linux (for Burp and HTTP server)**

### 📌 Key Steps

#### 🔹 Burp Setup & Proxy Configuration
- Installed Burp and created a temporary project.
- Set up Burp proxy listener on host machine (port 8080).
- Configured Android emulator Wi-Fi to use Burp’s proxy manually.

#### 🔹 HTTP Interception
- Accessed `http://hackazon.samsclass.info` via the Android browser.
- Viewed HTTP traffic in Burp under "HTTP History".

#### 🔹 HTTPS Interception Setup
- Installed Chrome on Android for better certificate handling.
- Attempted to access `https://samsclass.info` and triggered SSL warning.

#### 🔹 CA Certificate Installation
- Exported Burp's CA certificate in DER format (`portswigger.cer`).
- Transferred and installed certificate in Android's trusted credentials.
- Set device PIN to allow certificate installation.

#### 🔹 HTTPS Interception Validation
- Reloaded `https://samsclass.info` and verified full interception in Burp.
- Viewed HTTPS traffic successfully within Burp Suite.

#### 🔹 Bypass Proxy (Post-Test)
- Reset Android emulator’s Wi-Fi settings to disable Burp proxy for normal use.

#### ✅ Outcome
- Successfully intercepted both HTTP and HTTPS mobile traffic.
- Demonstrated SSL interception and certificate trust manipulation on Android.

---


## 📄 Full Lab Reports


- 🔗 [Full Mobile Application Burp Lab Report](https://github.com/pavithrancj/Burp-Suit/blob/main/Burp%20Suit_Mobile%20Application.pdf)
