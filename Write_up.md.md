# 🌳 DeepThought OS | Daily Reflection Tree

**A Deterministic, Psychological Reflection Agent** *Built for the DeepThought (DT) Fellowship Assignment (Knowledge Engineer / Business Analyst)*

---

## 📖 Overview

This repository contains **The Daily Reflection Tree**, an interactive, data-driven web application designed to guide employees through an end-of-day reflection. 

Unlike standard chatbots, this agent operates **without any LLM at runtime**. It is a 100% deterministic state machine powered entirely by a structured data ontology (CSV). It translates complex organizational psychology into a seamless, conversational User Interface.

### Core Psychological Axes
The logic tree maps user inputs across three psychological dimensions:
1. **Axis 1: Locus of Control** (Rotter) – Internal (Agency) vs. External (Victimhood)
2. **Axis 2: Orientation** (Organ/Campbell) – Contribution (Citizenship) vs. Entitlement
3. **Axis 3: Radius of Concern** (Maslow/Batson) – Self-Centric vs. Altrocentric

---

## ✨ Key Features

* **Zero-Hallucination Architecture:** The logic is completely decoupled from the UI. Every question, decision, and insight is hard-mapped in the data file.
* **Universal Data Parser:** The UI dynamically loads and reads `.csv`, `.tsv`, `.json`, or `.yaml` files on the client side using PapaParse and js-yaml.
* **Premium "In-Stream" UI:** Built with Tailwind CSS, the interface features a calming, frictionless conversational flow with intelligent auto-scrolling and clean state management.
* **Serverless Deployment:** Hosted as a Static Single Page Application (SPA).

---

## 🚀 How to Run the Agent

Because this project is built as a Static SPA, it requires no backend server, no Python environment, and no API keys. 

### Option A: Live Production Link (Recommended)
You can experience the fully deployed agent here:
👉 **[Insert your AWS S3 / GitHub Pages Link Here]**
*(Note: The live deployment automatically fetches the reflection tree CSV in the background.)*

### Option B: Run Locally
If you prefer to test the agent locally:
1. Clone this repository to your machine.
2. Double-click `index.html` to open it in any modern web browser.
3.A **"Load Ontology"** screen will automatically appear.
4. Click **Choose Data File** and upload the `reflection-tree-final.csv` (or `.json` / `.tsv`) file included in this repository.
5. The UI will instantly parse the logic and begin the session.

---

## 🧠 How to Read the Tree (Data Structure)

The "brain" of this agent lives entirely inside `reflection-tree-final.csv`. It acts as a deterministic state machine. To audit the logic, simply open the CSV file. Each row represents a node, guided by these core columns:

* **`id` & `parentId`:** The unique identifiers that link the conversation history.
* **`type`:** Defines the node's behavior:
  * `question`: Pauses the engine and waits for user input.
  * `decision`: An invisible logic gate that routes the user based on their previous answer.
  * `reflection`: A psychological insight delivered to the user.
  * `bridge`: A transition node funneling the user to the next psychological axis.
* **`options`:** Contains the choices separated by `|`. For decision nodes, it contains the routing logic (e.g., `answer=Productive|Mixed:A1_Q_AGENCY_HIGH`).
* **`target`:** Used to jump across branches (e.g., forcing multiple reflection nodes to merge into a single, unified bridge).
* **`signal`:** Tracks the psychological tally (e.g., `axis1:internal`). The system accumulates these silently to calculate the final dominant persona.

---

## 📂 Repository Structure

```text
├── reflection-tree.tsv                   # The core logic engine / data ontology
├── reflectos.html                        # The Static SPA / Conversational UI Hosted using AWS S3
├── tree_diagram.svg                      # 1:1 Visual architecture diagram
├── write-up.md                           # Explanation of design & psychology
└── /transcripts                          # Markdown files showing example persona sessions
    ├── persona-1-transcript.md           # Example:  victim/entitled/self-centric
    └── persona-2-transcript.md           # Example:  victor/contributing/altrocentric
