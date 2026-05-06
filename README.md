# 🏠 AI Property Assistant (n8n + Supabase)

An AI-powered real estate assistant built using **n8n workflows** and **Supabase**, designed to handle stateful conversations, intelligent property search, and dynamic tool routing (weather + database queries).

---

## 🚀 Overview

This project demonstrates a **workflow-based AI system** that goes beyond simple chatbots by maintaining context, updating user preferences in real time, and executing intelligent actions based on user intent.

Instead of relying on traditional memory systems, it uses **n8n static workflow data** to persist state across the conversation.

---

## ⚙️ Features

- 🧠 Stateful conversation handling using `getWorkflowStaticData`
- 🏡 Dynamic property search with Supabase
- 🌦️ Weather API integration for contextual queries
- 🔄 AI-powered routing between tools (DB vs Weather)
- ⚡ City-based caching for performance optimization
- 📊 Structured extraction of user preferences (city, budget, property type, etc.)
- 💬 Conversational response formatting for end users

---

## 🗄️ Database Schema (Supabase)

Table: `properties`

| Column Name    | Data Type     | Description                          |
|----------------|--------------|--------------------------------------|
| id             | UUID / Int    | Primary Key                          |
| property_type  | String        | Apartment, Villa, Studio (Required)  |
| price          | Numeric       | Listing price                        |
| city           | String        | City location                        |
| state          | String        | State / Province                     |
| availability   | Boolean       | Available for sale/lease            |
| bedrooms       | Integer       | Number of rooms                     |
| amenities      | Text[]        | Property features                   |

---

## 🧩 Workflow Logic

### 1. Input Processing
- User message is sent to AI agent
- Entities (city, budget, property type) are extracted
- JSON state is updated using static workflow data

### 2. State Management
- Conversation state is stored in `getWorkflowStaticData`
- Ensures memory across multiple user messages

### 3. Decision Engine
- If `property_type + city` exist → trigger Supabase search
- If weather intent detected → call Weather API
- Otherwise → request missing information

### 4. Data Retrieval
- Query Supabase using dynamic filters:
  - price range
  - city
  - property type
  - bedrooms

### 5. Response Generation
- Top 3 results are formatted into a natural conversational response

---

## ⚡ Advanced Features

### 🔁 Tool Routing (AI Agent)
The AI acts as a router:
- Property queries → Supabase
- Weather queries → Weather API

### ⚡ Caching Layer
- Results cached by city name
- Prevents repeated DB queries for same location
- Improves performance and response time

---

## 🧪 Test Scenario (Fragmented Lead)

| Step | User Input | System Behavior |
|------|-----------|-----------------|
| 1 | "I'm looking for an Apartment" | Sets `property_type` |
| 2 | "I want to live in New York" | Sets `city`, triggers search |
| 3 | "What’s the weather there?" | Calls Weather API (keeps state) |
| 4 | "Budget is 2000–4000" | Updates price range, refines results |
| 5 | "Show me Studios instead" | Updates property type, re-triggers search |

---

## 📦 Tech Stack

- n8n (Workflow Automation)
- Supabase (Database)
- OpenAI / AI Agent (Intent Extraction)
- Weather API
- Custom Caching Logic

---

## 📌 Project Status

🚧 Prototype / In Development  
Focused on building real-world AI workflow automation systems.

---

## 👨‍💻 Author

**Imran Shafique**  

---
