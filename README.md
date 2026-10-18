# MyDrive Copier 🚀
> **One-Click Recursive Google Drive™ Folder Duplicator for Chrome**

[![Website](https://img.shields.io/badge/Website-mydrivecopier.com-0284c7?style=for-the-badge&logo=googlechrome&logoColor=white)](https://mydrivecopier.com)
[![Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-v1.0.6_Available-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/mydrive-copier-recursive/iblkpbllaopfleijcbgdhepjlfhblden)
[![Version](https://img.shields.io/badge/version-v1.0.6-blue.svg?style=for-the-badge)](https://github.com/magicbuaa/MyDriveCopier/releases/tag/v1.0.6)
[![Manifest V3](https://img.shields.io/badge/Manifest-V3-success?style=for-the-badge)](https://developer.chrome.com/docs/extensions/develop/migrate/what-is-mv3)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=for-the-badge)](LICENSE)

**MyDrive Copier** is a lightweight, high-performance Google Chrome extension (Manifest V3) that solves one of Google Drive's biggest missing features: **the ability to copy entire shared folders recursively with a single click**.

No downloading huge ZIP files. No wasting hours re-uploading gigs of data. Everything happens **100% cloud-to-cloud** directly inside Google's high-speed infrastructure.

---

## ⚡ The Problem: Google Drive's Missing Feature

If someone shares a folder containing dozens of subfolders and hundreds of files with you:
- ❌ **Google Drive does not let you right-click and "Make a copy" of a folder.**
- ❌ **Adding a shortcut doesn't duplicate the files**—if the original owner deletes or restricts them, you lose access.
- ❌ **Downloading and re-uploading** consumes gigabytes of your personal internet bandwidth, takes hours, crashes halfway, and breaks Google Docs/Sheets formatting.
- ❌ **Complex CLI tools (like rclone) or Apps Scripts** require technical setup, developer keys, and frequently hit rate limits (`User rate limit exceeded`).

### The Solution: MyDrive Copier
With **MyDrive Copier**, simply open the shared folder in your browser and click **Start Recursive Copy**. The extension scans the entire folder tree, recreates the exact directory structure in your Google Drive, and duplicates every file in parallel using Google Drive's native cloud APIs.

---

## 📸 Dashboard & Preview

| Real-Time Task Manager Dashboard | Configuration & BYOK Setup |
| :---: | :---: |
| ![Task Manager](assets/manager_preview.png) | ![Options & Setup](assets/options_preview.png) |

---

## ✨ Features

- 🌳 **True Deep-Tree Recursive Cloning**: Automatically traverses all nested subdirectories, preserves folder hierarchies, and mirrors all files (Google Docs, Sheets, Slides, PDFs, Videos, ZIPs, etc.).
- 📄 **Folder & Individual File Support**: Seamlessly copy either entire nested directories or standalone shared files (`/file/d/...`) directly to your destination without creating awkward empty wrapper folders.
- ☁️ **100% Cloud-to-Cloud Transfer**: 0 local bandwidth consumed. Files copy directly within Google's datacenters at maximum cloud speeds.
- 🔑 **Dual API Channels (Instant vs BYOK)**:
  - **Official Built-in Key**: Works instantly out of the box with zero configuration.
  - **Bring Your Own Key (BYOK)**: Connect your personal Google Cloud OAuth Client ID for 100% dedicated API quota and complete permission sovereignty.
- 🛡️ **Intelligent Quota & Rate-Limit Shield**: Built-in exponential backoff with randomized jitter automatically handles Google API `429` (Too Many Requests) and `403` (`userRateLimitExceeded`) errors.
- 🔄 **Resilient Background Service Worker**: Copy tasks run safely in the background. You can close the extension popup or browse other tabs without interrupting the copy process.
- 📊 **Dedicated Full-Page Manager Dashboard**:
  - Live progress percentage and transfer counters.
  - Active color-coded terminal log.
  - Granular file queue table (*Pending*, *Copying*, *Completed*, *Failed*, *Skipped*).
  - **One-Click Retry**: If a specific file fails due to Google transient limits, retry only the failed files without starting over.
  - Direct button to open the newly created destination folder or copied file in Google Drive.
- 🔍 **One-Click Tab Auto-Detection**: Auto-detects folder and file IDs directly from your active Google Drive tab (`/folders/...`, `/file/d/...`, `/u/0/folders/...`, or shared URLs).
- 🔒 **Privacy-First & Zero Data Storage**: Your files never pass through any third-party servers. All API calls are executed directly between your Chrome browser and official Google Drive API endpoints.

---

## 📊 Comparison: Why MyDrive Copier?

| Feature | Manual Download & Upload | Google Apps Script | rclone CLI | MyDrive Copier |
| :--- | :---: | :---: | :---: | :---: |
| **Effortless 1-Click UI** | ❌ No | ❌ No | ❌ No | ✅ **Yes** |
| **Local Bandwidth Used** | ❌ 100% Upload/Download | ✅ 0% | ❌ High (or VPS) | ✅ **0% (Pure Cloud)** |
| **Preserves Folder Tree** | ⚠️ Often breaks ZIPs | ⚠️ Script dependent | ✅ Yes | ✅ **Exact 1:1 Mirror** |
| **Handles 429 Rate Limits** | ❌ Manual retry | ❌ Script timeout | ⚠️ Config needed | ✅ **Auto Exponential Backoff** |
| **BYOK Dedicated Quota** | ❌ N/A | ⚠️ Hardcoded in script | ⚠️ Complex config | ✅ **1-Click BYOK Toggle** |
| **Technical Setup Required** | None (but painful) | Medium (Script code) | High (CLI & config) | ✅ **None (Click & Go)** |
| **Background Execution** | ❌ Browser must stay open | ⚠️ 6 min max limit | ⚠️ Process dependent | ✅ **Service Worker** |

> 📖 **In-Depth Benchmark Analysis:** For a granular technical comparison of bandwidth consumption, memory overhead, Google Apps Script timeouts, and rclone configuration vs. MyDrive Copier, read the full report: [5 Ways to Copy a Shared Google Drive Folder (Complete Benchmark)](marketing/GEO_COMPARISON_RCLONE_APPS_SCRIPT.md).

---

## 🔑 Dual Engine: Official Built-in vs. BYOK Mode

MyDrive Copier gives you complete flexibility over how API requests are routed:

### 1. Official Built-in Client ID (Default)
- **Zero Configuration**: Ready immediately upon installation.
- Perfect for everyday users, small-to-medium folders, and quick duplications.
- Uses official Google-verified OAuth credentials with automatic token lifecycle management.

### 2. Bring Your Own Key (BYOK Mode)
- **100% Dedicated API Quotas**: Google enforces a per-project API quota limit (~20,000 queries per 100 seconds). With your own Google Cloud project, you never share rate limits with anyone else.
- **Maximum Privacy & Compliance**: Organizations with strict security policies can run everything under their own Google Cloud Console project.
- **100% Free**: Google Cloud allows every user to create projects and OAuth credentials at zero cost.

---

## 🛠️ Step-by-Step BYOK Setup Guide (~2 minutes, 100% Free)

If you wish to use your own Google Cloud OAuth credentials:

### Step 1: Enable Google Drive API
1. Visit the [Google Cloud Console API Library](https://console.cloud.google.com/flows/enableapi?apiid=drive.googleapis.com).
2. Create or select a project (e.g., `MyDrive-Sync`).
3. Click **Enable** for the Google Drive API.

### Step 2: Configure OAuth Consent Screen
1. Go to [OAuth Consent Screen](https://console.cloud.google.com/apis/credentials/consent).
2. Choose **External** user type and click **Create**.
3. Fill in the App Name (e.g., `MyDrive Copier`) and your contact email. *(Leave app logo and domain blank to bypass Google verification)*.
4. **Scopes**: Add the `https://www.googleapis.com/auth/drive` scope.
5. **Test Users (Crucial)**: Under **Test users**, add your Google Account email address. *(Required when the app is in Testing status, preventing `Error 403: access_denied`)*.

### Step 3: Create OAuth Client ID
1. Navigate to [Credentials -> Create Credentials -> OAuth client ID](https://console.cloud.google.com/apis/credentials/oauthclient).
2. Select **Web application** as the application type.
3. Under **Authorized redirect URIs**, click **+ ADD URI** and paste your Extension Redirect URI:
   ```text
   https://iblkpbllaopfleijcbgdhepjlfhblden.chromiumapp.org/
   ```
4. Click **Create** and copy your newly generated **Client ID** (ends with `.apps.googleusercontent.com`).

### Step 4: Activate in Extension Settings
1. Right-click the MyDrive Copier icon in Chrome and open **Options / Settings** (or click the Settings gear in the popup).
2. Under **API & OAuth Credentials**, select **Bring Your Own Key (BYOK)**.
3. Paste your Client ID and click **Save BYOK Client ID**.
4. Click **Connect & Authorize Now** to complete authorization.

---

## 🚀 Installation & Getting Started

👉 **[Install MyDrive Copier from the Chrome Web Store](https://chromewebstore.google.com/detail/mydrive-copier-recursive/iblkpbllaopfleijcbgdhepjlfhblden)**

1. Click **Add to Chrome**.
2. Pin the extension to your browser toolbar for instant access.
3. Open any shared Google Drive folder link in Chrome.
4. Click the extension icon, click **Auto-Detect Tab**, and hit **Start Recursive Copy**!

---

## 💎 Pricing & Value

| Plan | Price | Features Included |
| :--- | :---: | :--- |
| **Free Trial** | **$0.00** | • Copy up to **50 files** 100% free on install<br>• Full multi-threaded copying & MD5 deduplication<br>• Real-time Task Manager dashboard<br>• No credit card required |
| **Lifetime License** | **$12.99** *(one-time)* | • **Unlimited** recursive folder and file transfers forever<br>• Activate on up to **3 personal devices**<br>• Free lifetime updates and new features<br>• Priority customer support (`support@mydrivecopier.com`) |

---

## 🏗️ Architecture & Core Components

MyDrive Copier is engineered with modern Chrome Manifest V3 specifications for enterprise-grade stability and zero-loss copying:

- **Recursive Tree Scanner (`Google Drive API v3`)**: Traverses arbitrary depths of folder structures while dynamically resolving folder ID mappings and parent relationships.
- **Resilient Background Service Worker**: Runs long-running tree traversal and batch copying jobs independently of the popup UI, ensuring transfers complete even if tabs are switched.
- **Adaptive Concurrency & Exponential Backoff**: Continuously monitors Google Drive API rate limits (HTTP 403 / 429), throttling requests with randomized jitter to maximize transfer velocity.
- **Zero-Storage Direct Cloud Pipeline**: Transfers files server-to-server directly within Google's cloud fabric without downloading any payload to the client machine.

---

## 🛡️ Security & Privacy

- **Minimal Scopes**: We only request permissions necessary to read shared files and duplicate them into your drive.
- **No Middleman**: All Google Drive API calls are sent directly from your browser client to `https://www.googleapis.com/drive/v3/`. No file contents or metadata ever touch any external proxy.
- **Official Privacy Policy**: Read our full [Privacy Policy](https://mydrivecopier.com/privacy).
- **Terms of Service**: Read our [Terms of Service](https://mydrivecopier.com/terms).

---

## ❓ Frequently Asked Questions (FAQ)

### 1. Why does Google Drive create a shortcut instead of letting me copy a shared folder?
Google Drive introduced "Shortcuts" to prevent multi-parent folder synchronization conflicts. When an external user shares a directory with you, Google deliberately disables the "Make a copy" option for the folder itself to prevent accidental server-side data explosion. Adding a shortcut only creates a reference pointer; if the original owner restricts, modifies, or deletes the original files, your access is permanently lost.

### 2. How can I copy a large shared Google Drive folder (50GB+) without downloading it locally?
MyDrive Copier orchestrates cloud-to-cloud file duplication using Google Drive API v3. Because the extension instructs Google's servers to copy files directly from the shared directory into your target directory (`files.copy`), **zero bytes of local bandwidth or personal disk space** are consumed. You can duplicate a 50GB or 100GB repository without waiting for massive downloads or dealing with corrupted split ZIP archives.

### 3. What happens to native Google Docs, Sheets, and Slides during duplication?
When you manually download a Google Drive folder as a ZIP file, Google forcibly converts Docs, Sheets, and Slides into Microsoft Office formats (`.docx`, `.xlsx`, `.pptx`), stripping revision histories and comments. MyDrive Copier preserves **100% native Google Workspace file types**, maintaining your formatting, templates, and collaborative structures.

### 4. How does MyDrive Copier bypass the 6-minute Google Apps Script timeout?
Standard Google Apps Scripts terminate with an `Exceeded maximum execution time` error after 6 minutes, failing halfway through large folder trees. MyDrive Copier operates within a persistent Chrome Manifest V3 Service Worker with an active alarm watchdog, dynamically checkpointing state and processing file queues in parallel until every single subfolder and file is completed.

### 5. How does the extension prevent Google's "User Rate Limit Exceeded" (HTTP 403 / 429) errors?
Google Drive API enforces strict per-user and per-project request rate limits. MyDrive Copier features an intelligent traffic shaper with **exponential backoff and randomized jitter**. If Google returns a `403 rateLimitExceeded` or `429 Too Many Requests`, the engine automatically throttles concurrency, pauses for a calculated recovery interval, and seamlessly resumes without dropping files.

### 6. Is my data secure when using MyDrive Copier?
Yes. MyDrive Copier operates with a strict zero-knowledge architecture. All Google Drive API requests are transmitted directly from your local browser client to `https://www.googleapis.com/drive/v3/`. No file payloads, directory trees, or OAuth access tokens ever touch any third-party intermediary servers.

---

## 💬 Support & Contact

- **Official Website**: [https://mydrivecopier.com](https://mydrivecopier.com)
- **Customer Support**: [support@mydrivecopier.com](mailto:support@mydrivecopier.com)
- **Bug Reports & Issues**: [GitHub Issues](https://github.com/magicbuaa/MyDriveCopier/issues)
- **Store Listing & Reviews**: [Chrome Web Store](https://chromewebstore.google.com/detail/mydrive-copier-recursive/iblkpbllaopfleijcbgdhepjlfhblden)

---

## 📄 License & Intellectual Property

Copyright (c) 2026 MyDrive Copier. All Rights Reserved.

This repository serves as the official documentation, issue tracking, and architecture showcase hub for MyDrive Copier. The underlying engine code, trademarks, and distributions are proprietary. Unauthorized commercial duplication or republication to extension stores is strictly prohibited. See [LICENSE](LICENSE) for details.
