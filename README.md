# 🤖 AI Customer Support Agent with RAG & Inventory Automation
An enterprise-grade Customer Support Assistant built using **n8n** and **LangChain**. This workflow leverages **Retrieval-Augmented Generation (RAG)** via a custom vector API endpoint alongside relational databases to handle policy queries, log e-commerce orders, and dynamically update inventory management systems without hardcoded branching logic.

---

## 💼 Portfolio / Resume Quick-Summary
> *Professional snapshot of this build for recruiters and hiring managers:*

* **Customer Support Agent with RAG** | *n8n • Google Gemini • LangChain • Custom Vector APIs • Google Sheets* (2026)
  * Designed and implemented an autonomous Customer Support Assistant using **n8n**, leveraging **Retrieval-Augmented Generation (RAG)** to dynamically resolve policy, FAQ, and operational queries.
  * Integrated a custom vector API endpoint to perform semantic retrieval from external knowledge bases, minimizing model hallucinations and ensuring highly accurate data delivery.
  * Developed automated data pipelines connecting **Google Gemini (LLM)** and **Google Sheets** to orchestrate real-time transaction handling, order placement, and live inventory updates.
  * Engineered a conversation-state architecture with window-buffer memory and pacing triggers to deliver seamless, multi-turn customer experiences.

---

## 🚀 Features
- **Retrieval-Augmented Generation (RAG):** Connects to a dedicated vector store API endpoint to fetch contextually relevant internal policies and documentation before answering user queries.
- **Dynamic Order Placement:** Automatically parses customer details from chat conversations to append new order rows to backend databases.
- **Two-Way Inventory Control:** Allows the agent to both read active stock levels and update quantities post-purchase.
- **Paced Interaction Safeguards:** Utilizes a `Wait` node structure to queue incoming messages, preventing API rate-limit exhaustion and ensuring optimal processing times.
- **State-Aware Conversations:** Retains conversational history through an optimized memory window block, making multi-turn order configurations natural and smooth.

## 🛠️ Architecture & Nodes Used
As shown on the n8n canvas:
1. **When chat message received:** The conversational front-end trigger capturing user messages.
2. **Wait Node:** Acts as a buffer to pace executions and manage incoming API payloads gracefully.
3. **AI Agent (LangChain):** The brain that parses prompt logic, tracks thoughts, and selects tools.
4. **Google Gemini Chat Model:** Advanced language intelligence handling logical execution and text formatting.
5. **Simple Memory:** Tracks session data across chat interactions to preserve contextual state.
6. **Connected Semantic Sub-Tools (The Agent's Hands):**
   - `Update Inventory` (Google Sheets): Modifies stock quantities dynamically when an order changes.
   - `Place Order` (Google Sheets): Appends newly finalized buyer orders.
   - `Get Inventory` (Google Sheets): Evaluates current stock numbers to guide the agent's availability responses.
   - `Get Policies From Rag` (HTTP Request/POST): Performs an automated API fetch to a vector database to fetch compliance, FAQ, and store regulations.

## 📋 Prerequisites
To deploy this project, you will need authorized credentials for:
- An active **n8n instance** (Self-hosted or Cloud)
- **Google AI Studio API Key** (for Gemini)
- **Google Cloud Console Project** with Google Sheets API enabled (via OAuth2)
- Endpoint access to your **RAG Vector API Service**

## 📦 Installation & Setup
1. Clone this repository or download the workflow JSON file.
2. In your n8n dashboard, select **New Workflow** -> **Import from File** and upload the configuration.
3. Open the credential manager for each respective node and authenticate your accounts:
   - Google Gemini API
   - Google Sheets OAuth2 API
   - Your custom RAG endpoint headers (inside the HTTP Request sub-tool)
4. Toggle the workflow to **Active** to start handling automated support interactions.
