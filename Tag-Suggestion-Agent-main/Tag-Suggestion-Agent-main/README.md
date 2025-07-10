# Tag Suggestion Agent Using ReAct Pattern 
In this project I trained a local tag suggestion agent using the ReAct (Reason + Action) pattern 

# React Pattern Overview
The core idea of ReAct is to simulate a loop of:
 1. Thought -> The agent considers what to do next.
 2. Action -> The agent performs an action based on its thought.
 3. Observation -> The agent observes the result of the action.
This loop repeast until a Final Answer is reached.

Example: Simple Tagging Agent

Since this project is purely local I did not utilize Cloud and APIs for training the agent instead, I defined a dictionary for keywords that the agent can use. Since AI agents can utilize "external environments" such as website, blogs, and articles to support its decision making, the defined dictionary will act as an external environment for the agent.

# Here is the simple dictionary I used for this project
```
tag_library = {
    "rusted" : "Corrosion",
    "corroded" : "Corrosion",
    "valve" : "Valve",
    "pipe" : "Pipeline",
    "compressor" : "Compressor Zone",
    "leak" : "Leakage",
    "noise" : "Abnormal Sound",
    "vibration" : "Vibration",
}
```
# AI Agent code   
```
    def tag_agent(description):
    tags = set()
    words = description.lower().split()

    for word in words:
        print(f"Thought: Is '{word}' a keyword?")
        if word in tag_library:
            tag = tag_library[word]
            print(f"Action: Found match for '{word}' in tag library: '{tag}'")
            print(f"Observation: Adding '{tag}' to the first tag list")
            tags.add(tag)
        else:
            print(f"Observation: No match for '{word}' in tag library")

    print(f"Final Answer:", list(tags))
    return list(tags)
```
# Test the Agent 
Using the test_agent to run a unit test, here we will just input a short description of a problem for the AI Agent
Here are some sample test cases for the agent
"There is a rusted pipe near the compressor"
"The valve is making a strange noise"
"We detected a leak and excessive vibration"
"A corroded valve needs to be replaced"

```
test_agent("Rusted valve found near compressor 2")
```
# Output
```
Thought: Is 'rusted' a keyword?
Action: Found match for 'rusted' in tag library: 'Corrosion'
Observation: Adding 'Corrosion' to the first tag list
Thought: Is 'valve' a keyword?
Action: Found match for 'valve' in tag library: 'Valve'
Observation: Adding 'Valve' to the first tag list
Thought: Is 'found' a keyword?
Observation: No match for 'found' in tag library
Thought: Is 'near' a keyword?
Observation: No match for 'near' in tag library
Thought: Is 'compressor' a keyword?
Action: Found match for 'compressor' in tag library: 'Compressor Zone'
Observation: Adding 'Compressor Zone' to the first tag list
Thought: Is '2' a keyword?
Observation: No match for '2' in tag library
Final Answer: ['Compressor Zone', 'Valve', 'Corrosion']

```
