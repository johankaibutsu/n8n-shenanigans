---

# Notion Knowledge Base AI Assistant with n8n

Turn your Notion database into an intelligent, conversational AI assistant. This n8n workflow provides a public-facing chat interface that allows users to ask questions in natural language and get answers sourced directly from your Notion knowledge base.

## ✨ Demo

### n8n Workflow



https://github.com/user-attachments/assets/ae8bcd4b-ab3f-4f3e-9906-eab8fc1375cd

### Full chat interface



https://github.com/user-attachments/assets/2251eed5-2618-4ec1-8619-ee8f05c0555b



## 🚀 Key Features

-   **Conversational Interface:** A public, shareable "chat-in-a-box" that acts as the front-end for your knowledge base.
-   **Powered by a LangChain Agent:** The AI brain of the operation. It intelligently uses tools to answer questions instead of just guessing.
-   **Dynamic Notion Tools:**
    -   **Search Database:** The agent can query your entire Notion database by keyword or tags to find relevant pages.
    -   **Read Page Content:** Once a relevant page is found, the agent can read its content to extract the specific answer.
-   **Context-Aware Memory:** The assistant remembers the last few messages, allowing for follow-up questions and a more natural conversation flow.
-   **Easily Customizable:** Swap out the AI model (works with Google Gemini, OpenAI, OpenRouter, etc.), adjust the prompts, or add new tools with ease.

## ⚙️ How It Works

The workflow operates like an intelligent router for information:

1.  **Chat Trigger:** The workflow starts when a user sends a message through the public chat webhook.
2.  **Fetch Database Schema:** It first retrieves the structure of your Notion database, including the available tags, to provide this context to the AI.
3.  **AI Agent Activation:** The user's question, chat history, and the available Notion tools are passed to the AI Agent (powered by Google Gemini in this template).
4.  **Tool Selection:** The agent analyzes the user's request and decides the best course of action:
    -   If the user asks "What do we know about 'laptops'?", the agent will use the **Search notion database** tool with "laptops" as the keyword.
    -   If the search tool returns a relevant page ID, the agent might then use the **Search inside database record** tool to read the page's content.
    -   If the question is conversational (e.g., "Thank you!"), it might answer directly from its base knowledge.
5.  **Synthesize and Respond:** The agent takes the information gathered from the tools, synthesizes a final answer, and sends it back to the user in the chat interface.

## 🔧 Setup Instructions

Follow these steps to get your own AI assistant running in minutes.

### 1. Prerequisites

-   An **n8n instance** (Cloud or self-hosted).
-   A **Notion account** with a database ready to be used as a knowledge base.
-   A **Google AI (Gemini) API Key**. You can easily swap this for another provider like OpenAI or OpenRouter.

### 2. Import the n8n Workflow

1.  Download the `Notion knowledge base AI assistant.json` file from this repository.
2.  In your n8n canvas, go to **File > Import from File** and select the JSON file.

### 3. Configure Credentials

1.  In your n8n instance, go to the **Credentials** section.
2.  Create a **Notion credential** by following the on-screen instructions.
3.  Create a **Google Gemini (PaLM) API credential** by adding your API key.

### 4. Configure the Workflow Nodes

1.  **Get database details (Notion Node):**
    -   Select your Notion credential.
    -   In the **Database ID** field, choose your knowledge base database from the list.
    -   Database I used : [Notion](https://30dayaisprint.notion.site/7ea9697d4875441eb2621105337d232e?v=cff6ba4cb0d14613b143af6f96dab287)

2.  **Google Gemini Chat Model:**
    -   Select the Google Gemini credential you created.

3.  **Search notion database & Search inside database record (Tool Nodes):**
    -   Ensure your Notion credential is selected for both of these nodes.

### 6. Activate and Chat!

1.  Save the workflow.
2.  Activate it using the toggle at the top right of the screen.
3.  Go to the **When chat message received** trigger node. Click the **Webhook URLs > Production URL** to open your new AI assistant in a new tab.

Start asking questions related to the content in your Notion database!
