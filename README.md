# A2UI Cloud Dashboard Agent

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=flat&logo=google-cloud&logoColor=white)](https://cloud.google.com/)


![Agent Development Kit 2.1.0](Agent%20Development%20Kit%202.1.0.png)

## Overview
This project is a cloud infrastructure assistant built using the Agent Development Kit (ADK) and A2UI. It queries cloud resource data and returns rich, interactive UI components directly in the ADK web interface, rather than standard plain text responses.

## App Topology

Based on the updated project structure, the application is organized as follows:

```text
a2ui_agent/
└── app/
    ├── agent.py         # Main agent definition and A2UI schema setup
    ├── resources.py     # Mock data and get_resources tool
    └── utilis.py        # A2UI rendering callback utility
```

*Note: Since all files are now located together in the `app` folder, you can use standard relative imports in your `agent.py` exactly as they were in the original codelab (e.g., `from .resources import get_resources` and `from .utilis import a2ui_callback`).*

## Instructions

### 1. Set Up Environment Variables
Configure your Google Cloud project and enable Vertex AI:

```bash
export GOOGLE_CLOUD_PROJECT="mydevproject-20260430"
export GOOGLE_CLOUD_LOCATION="global"
export GOOGLE_GENAI_USE_VERTEXAI="True"
```

### 2. Enable APIs
```bash
gcloud services enable aiplatform.googleapis.com
```

### 3. Install Dependencies
Install the required packages and update your path:
```bash
pip install -U google-adk a2ui-agent-sdk
export PATH="$HOME/.local/bin:$PATH"
```

### 4. Run the ADK Web Server
Navigate to the directory containing your `a2ui_agent` folder and run the following command to start the development UI:
```bash
adk web --port 8080 --allow_origins "*" --reload_agents
```

### 5. Test the Agent
Open the ADK Web UI in your browser (preview on Port 8080), select the agent, start a new session, and try the following prompts to see the rendered UI components:
* *"What's running in my project?"*
* *"Does anything need my attention?"*
* *"I need to deploy a new service."*
