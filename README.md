# ✅ Task.fan — AI Browser Automation Agent

**Task.fan** is your AI assistant that lives in the browser’s sidepanel. It understands your intent, navigates websites, and executes tasks with a single command — all while explaining each action. Powered by ChatGPT, Gemini, and Anthropic Claude.

![ChatGPT Image Jun 9, 2025, 01_01_21 AM](https://github.com/user-attachments/assets/1b6570ef-c438-4dc2-95b5-13f1423cee4c)


---

## 🌐 Live Demo & Extension

📽️ [Watch Demo](https://github.com/normal-computing/fuji-web/assets/1001890/88a2fa12-31d9-4856-be67-27dcf9f1e634)  
🧩 [Download Extension (ZIP)](https://github.com/xaspx/taskfan/releases)

---

## 🚀 Features

- One-command task execution in your browser
- Full sidepanel AI interface
- Compatible with OpenAI, Gemini, and Claude
- Explains actions as it automates
- 100% local — no external logging or tracking

---

## 🧠 How It Works

1. Install the Chrome extension  
2. Connect your API key (OpenAI / Anthropic)  
3. Open the sidepanel and type your task  
4. Task.fan will act and explain what it's doing

---

## 🔧 Installation Guide

1. Download from [GitHub Releases](https://github.com/xaspx/taskfan/releases)
2. Unzip the file  
3. Navigate to `chrome://extensions/`  
4. Enable `Developer Mode`  
5. Click `Load unpacked` and select the unzipped folder

---

## 💡 API Key Setup

- [OpenAI API Key](https://platform.openai.com/account/api-keys)  
- [Anthropic API Key](https://console.anthropic.com/settings/keys)  

*Keys are stored locally in your browser.*

---

## 🛠️ Build from Source

```bash
git clone https://github.com/xaspx/taskfan.git
cd taskfan
npm install -g pnpm
pnpm install
pnpm dev       # For development
pnpm build     # To build production version
