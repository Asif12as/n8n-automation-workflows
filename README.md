# n8n-automation-workflows
it demonstrates initiative and real-world automation expertise

# 🤖 n8n Automation Workflows
### 📰 Automated Social Media Posts
![Automated Social Media Posts](.automatedPOSTSonsSOCIALMEDIA.JPG)

### 🎥 Automated Shorts Generator
![Automated Shorts Generator](.automatedSHORTS.JPG)

### 💳 Transactional Banking Fraud Detector
![Transactional Banking Fraud Detector](.automated_bankingTRANSACTIONAL_fraud_.JPG)

### 🔍 Real-Time Google Search Agent
![Real-Time Google Search Agent](.realtimeGOOGLE_SEARCH_AGENT.JPG)


# Social Media's Shorts Automation with AI-Generated Content

## 🧠 Goal:
To fully automate the creation and publication of Instagram Shorts using AI-driven story generation, image synthesis, sound effect generation, video compilation, and auto-posting.

## 🧩 Breakdown of Workflow & Technologies Used

### ✅ 1. Generate Stories
- **Schedule Trigger**
  - Starts the workflow daily or at custom intervals.

- **OpenAI Chat Model + Tools Agent (Ideas Agent & Scenes Agent)**
  - Generates engaging video ideas and scenes using GPT models.
  - Adds memory and context via agent setup for multi-turn logic.

- **Structured Output Parser**
  - Parses and formats AI-generated content (JSON/YAML structure).

- **Split Out / Limit Nodes**
  - Splits generated story blocks and limits the number for further processing.

### ✅ 2. Generate Images
- **Image Prompts Agent (Chat Model)**
  - Generates creative, detailed prompts for image generation.

- **Text to Image API Node**
  - Uses models like Stable Diffusion or DALLE via HTTP request for image synthesis.

- **Wait & Get Images Nodes**
  - Waits for generation completion.
  - Fetches generated images via API.

### ✅ 3. Generate Videos
- **Image to Video Node**
  - Converts static AI-generated images into animated clips (using tools like RunwayML or Kaiber via API).

- **Wait Node & Cut Videos Node**
  - Ensures sequential operations and trims videos to fit short format.

### ✅ 4. Generate Sound Effects
- **Text to Sound Effects API**
  - Sends prompts like "jungle ambiance" or "tech intro" to generate matching background sounds.

- **Wait & Get Sound Effects Nodes**
  - Ensures sound effect retrieval before video merging.

### ✅ 5. Create Video
- **Merge Node**
  - Combines generated images, video clips, and audio.

- **Aggregate & Combine Video Nodes**
  - Merges all content layers and finalizes video for posting.

### ✅ 6. Publish
- **POST to Instagram API (Publish to Instagram Node)**
  - Automatically uploads the final video as an Instagram Short (via Meta Graph API or third-party auto-posting services).

## 💼 Skills Demonstrated in This Workflow:
- 🧠 AI Prompt Engineering with GPT agents for storytelling and image prompting
- 🎨 Generative AI: Text-to-image and text-to-audio generation using APIs (like DALL·E, Stable Diffusion, ElevenLabs)
- 📽️ Media Processing: Combining multimedia assets (images, sound, video)
- 🔄 Workflow Automation: Scheduling, branching logic, merging, and waiting
- 🌐 API Integration: OpenAI, Instagram Graph API, Image/Video/Sound services
- 🔁 Full-stack Automation: From content generation → video production → social media publishing

# AI-Powered Stock Query ChatBot Using Tools and Memory in n8n

## 🧠 Goal:
Answer user queries (like Tesla's stock price) via chat by combining LLM reasoning with real-time data fetching (SerpAPI), memory handling, and optional calculation.

## 🧩 Workflow Analysis & Technologies

### ✅ 1. Trigger – When Chat Message Received
- Waits for user input like:
  - "Hi, what is Tesla price today?"

### ✅ 2. AI Agent Node – Tools Agent Setup
- A powerful Tools Agent connects:
  - Chat model (OpenAI GPT)
  - Memory (contextual memory handling)
  - SerpAPI for real-time web search
  - Calculator tool (for numeric reasoning if needed)

### ✅ 3. Memory Node – Simple Memory
- Retrieves relevant past data or stores context for multi-turn interaction.

### ✅ 4. OpenAI Chat Model
- Interprets the input and decides what tools to invoke.
- In this case, deduced the need to check stock price and used SerpAPI.

### ✅ 5. SerpAPI Node
- Sends a real-time search query to get live stock price info.
- Retrieves accurate stock price ($343.82 in this example).

### ✅ 6. Calculator (Optional Tool)
- Can be used if the query includes operations (e.g., "What is 5% of Tesla's stock price?").

## 💼 Skills Demonstrated:
- 🤖 LLM Agent Orchestration with external tool execution based on reasoning
- 🧠 Tool-Use via Agents: OpenAI + SerpAPI + Calculator
- 💬 Conversational AI Design using n8n and LLMs
- 🗂️ Contextual Memory Management for multi-turn chats
- 🌍 Real-time Data Integration (SerpAPI, Web Scraping APIs)

# AI-Driven Inspirational Post Generator for Telegram Using n8n

## 🧠 Goal:
Automatically send beautifully crafted quote posts with images to Telegram at scheduled times, combining quote APIs and image APIs with editing tools.

## 🧩 Workflow Analysis & Technologies

### ✅ 1. Schedule Trigger
- Triggers the whole workflow periodically (daily/hourly).
- Ensures consistent posting without manual intervention.

### ✅ 2. HTTP Request1 – Quote API
- GET https://zenquotes.io/api/...
- Fetches a random motivational quote.

### ✅ 3. Code Nodes
- Likely extract or format the quote text or author:
  - Code1: Parses and formats quote data.
  - Code2: May build the prompt for the image or prepare data for next request.

### ✅ HTTP Request2 – Image API (Pexels)
- GET https://api.pexels.com/v1/...
- Gets a relevant image (like nature, background) based on the quote or a keyword.

### ✅ HTTP Request3
- Possibly another image or metadata fetch (backup or fallback).

### ✅ Edit Image1 – Multi-Step Editing
- Combines quote + image into a visually appealing format.
- Adds quote text overlay, adjusts font, styling, etc.

### ✅ Telegram Node
- Posts the final inspirational quote image to a Telegram channel using sendPhoto.

### ⚠️ Issue Noted:
The Telegram node shows a red warning icon. Possible causes:
- Missing bot token
- Incorrect chat ID
- Image input issue
(You can debug it by checking execution logs or node settings.)

## 💼 Skills Demonstrated:
- 🕓 Scheduled Automation for social media
- 📜 API Integration (ZenQuotes + Pexels)
- 🧠 Data Parsing & Prompt Engineering
- 🖼️ Image Composition & Text Overlay
- 📲 Telegram Bot Integration
- 🔁 End-to-End Automation Workflow using n8n

# n8n Fraud Detection & Alerting System

## 🧠 Goal:
Automatically detect suspicious transactions via a webhook, and based on defined rules:
- Alert stakeholders via email
- Or trigger further actions for manual review or escalation

## 🧩 Workflow Structure & Node Breakdown

### ✅ 1. Webhook Trigger
- Type: POST
- Entry point for incoming transaction data from a financial app or payment system.

### ✅ 2. Switch Node – "Rules"
- Acts as a decision tree.
- Based on conditions (like amount > X, or foreign location):
  - Case 0 → High severity → Send Email
  - Case 2 → Medium or Low severity → Forward to Edit Fields for further tagging

### ✅ 3. Send Email Node
- Sends immediate fraud alert to relevant personnel.
- Content likely includes transaction details (user, amount, location, timestamp).

### ✅ 4. Edit Fields Node
- Likely used for:
  - Tagging the transaction
  - Modifying payload
  - Adding flags (e.g., status: "Needs Review")
- Could be linked to DB/API for further processing.

## 💼 Skills Demonstrated:
- 🔐 Webhook Integration for real-time event handling
- 🧠 Conditional Logic using Switch node
- 📧 Automated Alerting via email
- 🛠️ Data Transformation for flexible routing
- 🔁 Rule-Based Workflow Design — great for fintech or compliance use cases
