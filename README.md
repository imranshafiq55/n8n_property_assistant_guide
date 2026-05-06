🏠 AI Property Assistant (n8n + Supabase)

An AI-powered real estate assistant that manages stateful conversations, intelligently queries property data, and provides contextual responses like weather updates using a workflow-based architecture.

🚀 Project Overview

This project demonstrates a smart automation system built using n8n as the workflow engine and Supabase as the database layer.
The assistant is designed to handle real-world, fragmented user conversations while maintaining context throughout the session.

Unlike traditional chatbots, this system remembers user preferences and dynamically adapts queries in real time.

⚙️ Core Features
🧠 Stateful Conversations using n8n Static Data (no external memory DB required)
🏡 Dynamic Property Search with Supabase filtering
🌦️ Weather API Integration based on user intent
⚡ Smart Caching Layer to reduce redundant database calls
🔄 AI-Powered Routing between tools (DB search vs Weather API)
📊 Handles structured extraction of user preferences (city, budget, property type, etc.)
🗄️ Database Schema (Supabase)

The system uses a properties table with fields like:

property_type
price
city
state
availability
bedrooms
amenities
🧩 How It Works
User sends a message
AI extracts key entities and updates workflow state
System checks if required fields (like property_type) are available
Based on intent:
Queries Supabase for property listings
OR calls Weather API for contextual info
Results are returned in a conversational format
💡 Key Innovation

The assistant maintains conversation memory without a traditional database memory layer, using n8n static workflow data and structured JSON state management.

📦 Tech Stack
n8n (Workflow Automation)
Supabase (Database)
AI Agent (Intent & Entity Extraction)
Weather API
Custom Caching Logic
📌 Status

🚧 In Development / Prototype Phase
Focus: Improving real-world AI workflow reliability and performance

👨‍💻 Author

Imran Shafique
