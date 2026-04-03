# 🚀 MSI Packaging Demo using WiX

This project demonstrates how to create a Windows Installer (`.msi`) from scratch using the WiX Toolset.

It is a beginner-friendly, hands-on demo to understand how application packaging works in real-world enterprise environments.

---

## 🎯 Objective

- Understand MSI packaging workflow  
- Learn how WiX Toolset works  
- Build an installer using command line tools  
- Explore EXE vs MSI vs MST concepts  

---

## 📦 Project Structure
Demoapp/
│
├── src/ # Source files (application + WiX config)
├── build/ # Generated installer files
├── README.md

text

---

## 📁 Source Files (src/)

### 🔹 app.bat
```bat
@echo off
echo Demo App Running...
pause
👉 Represents the application being packaged inside the MSI

🔹 readme.txt
text
Hello from ISC Demo App
👉 Example file included in the installer

🔹 demo.wxs
Main WiX configuration file.
👉 Defines:

Installation directory

Files to install

Desktop shortcut

Registry entry

⚙️ Build Output (build/)
File	Description
DemoApp.msi	Final installer
cab1.cab	Compressed application files
DemoApp.wixpdb	Debug/build info
🔄 How It Works (Backend Flow)
text
demo.wxs
   ↓ (candle.exe)
demo.wixobj
   ↓ (light.exe)
DemoApp.msi
🧠 Key Concepts
🔹 EXE vs MSI vs MST
Type	Description
EXE	Standard installer (user-driven)
MSI	Structured installer (enterprise deployment)
MST	Transform file (customizes MSI without changing original)
👉 EXE = Install | MSI = Deploy | MST = Customize

🔨 Build Instructions
Step 1: Navigate to project

bash
cd <your-project-folder>
Step 2: Compile WiX source

powershell
& "C:\Program Files (x86)\WiX Toolset v3.14\bin\candle.exe" src\demo.wxs
Step 3: Generate MSI

powershell
& "C:\Program Files (x86)\WiX Toolset v3.14\bin\light.exe" demo.wixobj -o build\DemoApp.msi
📦 Install the Application
cmd
msiexec /i build\DemoApp.msi /qb
✅ Expected Result
After installation:

Files copied to C:\Program Files\ISCDemoApp

Desktop shortcut created

Registry entry added under HKCU\Software\DemoISC

💡 Why This Matters
This is the foundation of:

Application Packaging (L1 / L2 roles)

SCCM / Intune deployments

Enterprise software distribution

🎬 Demo Video
(LinkedIn demo video shows full workflow)

🚀 Next Step
👉 Part 2: Creating an MST (Transform) using Orca to customize the installer without modifying the original MSI