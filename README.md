# Multi-Agent Travel Planner

This is a multi-agent system built with LangGraph and LangChain that researches and plans personalized travel itineraries.

## How It Works
The system runs on a stateful graph that coordinates two distinct agents:
* **Researcher Agent:** Uses custom Python tools to check local weather and look up travel options based on the user's budget.
* **Planner Agent:** Takes the raw research data and drafts a structured, day-by-day itinerary.

## Key Features
* **Multi-Agent Architecture:** Built with LangGraph, using a `TravelState` TypedDict to manage the state passed between nodes.
* **Custom Tools:** Agents have access to two custom functions wrapped as tools (`get_weather_info` and `search_travel_options`).
* **Memory & Human-in-the-Loop (HITL):** Uses `InMemorySaver` to maintain conversational memory. The graph pauses execution using LangGraph's `interrupt()` API to ask for human approval or feedback before finalizing the itinerary.
* **Core Function & Tests:** A single `execute_workflow` function handles graph initialization, user requests, and the HITL resume logic. The notebook includes 5 distinct test cases demonstrating the workflow.

## How to Run
1. Open the `.ipynb` file in Google Colab.
2. Add your OpenAI API key to the Colab Secrets with the name `OPENAI_API_KEY` (Required).
3. *(Optional)* Add your LangSmith API key to the Colab Secrets with the name `LANGSMITH_API_KEY` to enable tracing.
4. Run all cells sequentially.