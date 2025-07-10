# AI-Agents Using ReAct Pattern (Local)

This repository contains two simple AI Agents implemented using the **ReAct pattern** in Python. The objective of this project is to explore how agents can think, observe and act until it finds a solution. Since this project is done locally there are no **external environment** such as APIs, Tools, and Cloud depencies used.

## ReAct Pattern Overview
Both agents follow the ReAct loop:

### Thought -> Action -> Observation -> (repeat) -> Final Answer

This approach helps visualize how the agent reasons through natural language inputs and provides transparent, step-by-step traceability of its decisions.

### 1. Tag Suggestion Agent
This agent classifies short natural language field observations (e.g., maintenance reports) into predefined tags based on keyword triggers. This project is inspired by a real-world WizyVision use case (e.g., Prime Energy) which helps categorize field incidents like rust, leaks, or abnormal noise.

### Input 
```txt
"Rusted valve found near compressor 2"
```

### Output
```txt
["Corrosion","Valve","Compressor Zone"]
```
### 2. Water Meter Transcription Agent
This agent extraacts structured readings from free-text meter logs. It parses transcriptions like "Unit 19A reads 30 cubic meter" and converts them into a structed JSON format.

### Input
```txt
"Unit 19A reads cubic meter, 19B is 5 cubic meter, 19C reads 8 cubic meter."
```

### Output
```
[
  {
    "unit": "19A",
    "reading": 30
  },
  {
    "unit": "19B",
    "reading": 5
  },
  {
    "unit": "19C",
    "reading": 8
  }
]
```

### Author
Lester Dave C. Ablat

ablatles@gmail.com
