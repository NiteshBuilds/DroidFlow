# DroidFlow 🚀

**General-Purpose No-Code AI Automation Platform for Android**

## 📖 Overview
DroidFlow is an autonomous, web-based no-code platform that empowers non-technical users to build, visualize, and execute complex, multi-app Android automations. Users can construct workflows effortlessly using either a drag-and-drop visual canvas or by simply typing plain natural language prompts (e.g., *"Check WhatsApp for unread orders and log them into Google Sheets"*). 

Unlike fragile legacy macro apps or developer-only CLI tools, DroidFlow completely removes the coding barrier via AI compilation, while guaranteeing robust, long-term execution through self-healing visual AI targeting.

---

## ✨ Key Features
* **Natural Language-to-Workflow Compiler:** Instantly translates plain text prompts into an editable JSON node graph on the visual canvas.
* **Hybrid Screen Grounding (Dual Perception):** Executes actions using lightning-fast Android Accessibility XML parsing. Automatically falls back to a real-time Vision-Language Model (VLM) if the UI is unreadable or heavily customized.
* **Self-Healing Selectors:** If an app updates its layout or button IDs, the AI visual engine automatically relocates the target element, preventing broken workflows.
* **Human-in-the-Loop (HITL) Guardrails:** Automatically detects sensitive UI states (payments, 2FA/OTPs, destructive actions) and pauses execution until explicit user authorization is granted on the dashboard.
* **Manager-Executor Reasoning:** Utilizes multi-step planning and execution for complex, cross-app data threading and variable extraction.

---

## 🏗️ System Architecture & Tech Stack

### Application Layer (Frontend)
* **React & Next.js:** Web Dashboard and HITL Authorization UI.
* **xyflow (React Flow):** Visual drag-and-drop node graph canvas.

### Backend Services & Orchestration (Agentic Layer)
* **FastAPI (Python):** Core backend API, event bus, and user dashboard connection service.
* **LangChain & LangGraph:** Stateful multi-agent workflow engine and orchestrator.

### AI & Compilation Models
* **Gemini 2.5 Flash:** Acts as the Natural Language-to-Workflow Compiler.
* **Qwen-2.5-VL:** Vision-Language Model for UI element visual grounding and screen coordinate extraction.

### Target Execution (Edge Device Layer)
* **Python Execution Engine:** `droidflow` framework interfacing directly with the Android Accessibility API.
* **SQLite:** Local database for caching App Skills and system states.

---

## 🚀 Why DroidFlow? (Competitor Comparison)
* **vs. Tasker / MacroDroid:** Legacy tools are rule-based, rigid, and break instantly on UI updates. **DroidFlow** uses self-healing visual selectors.
* **vs. Appium / UIAutomator:** Standard testing frameworks are developer-only CLI tools requiring deep coding knowledge. **DroidFlow** uses plain English and a no-code visual canvas accessible to anyone.

---

## 🛠️ Installation & Local Setup

### Prerequisites
* Python 3.10+
* Node.js 18+
* Android device or emulator with Developer Options and USB Debugging enabled.


```bash
# Clone the repository
git clone [https://github.com/](https://github.com/)[Your-Team-Name]/DroidFlow.git
cd DroidFlow/backend

# Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate
# Install dependencies
pip install -r requirements.txt

# Set up your environment variables (Add API keys for Gemini/Qwen)
cp .env.example .env

# Run the FastAPI server
uvicorn main:app --reload

```
### 2. Frontend Setup (React/Next.js)

```bash
cd ../frontend

# Install dependencies
npm install

# Start the development server
npm run dev
```

### 3. Device Connection

Ensure your Android device is connected and recognized by adb:
```
adb devices
```
Launch the droidflow execution framework from your terminal to bridge the Accessibility Service with the web dashboard.

## 🛡️ Scalability & Robustness
* Containerized Deployment: The stateless FastAPI backend is Docker-ready and can be horizontally scaled via Kubernetes.

* API-Driven Heavy Compute: Vision model inference is offloaded to APIs (Qwen/Gemini), keeping the edge client extremely lightweight and moderately low on resource consumption.

* Failure Recovery: Built-in retry, fallback logic, and safe-stop mechanisms isolate task execution to prevent system-wide failures.
