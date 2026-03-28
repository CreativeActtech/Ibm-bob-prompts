
# Set up a local Granite4:350m-h Ollama Agent w/ a Calculator Tool

## Prompt:


```
Create a local AI agent project using Ollama with the `granite4:350m-h` model. The agent should be able to use a calculator tool to perform mathematical calculations. Implement a simple agent loop that decides when to call the calculator based on user prompts.

```

ollama-calculator-agent/
├── .venv/                         # Python virtual environment
├── src/
│   ├── init.py
│   ├── agent.py                   # Main agent loop and logic
│   ├── tools/
│   │   ├── init.py
│   │   └── calculator.py          # Calculator tool implementation
│   └── utils/
│       ├── init.py
│       └── prompt_templates.py    # Agent prompts and system messages
├── scripts/
│   └── run_agent.py               # Entry point to run the agent
├── requirements.txt               # ollama, python-dotenv, maybe requests
├── .env.example                   # Environment variables (e.g., OLLAMA_HOST)
├── .gitignore
└── README.md                      # Complete setup instructions

```

### Requirements:

1. **Model Setup**:
   - Pull the `granite4:350m-h` model using `ollama pull granite4:350m-h`.
   - Ensure Ollama server is running (default http://localhost:11434).

2. **Agent Design**:
   - The agent should take user input (text) and determine whether a calculation is needed.
   - Use a system prompt that instructs the model to respond with a JSON object containing `"tool"` (if tool is needed) or `"answer"` (if direct answer). For calculator, the tool call format: `{"tool": "calculator", "expression": "2+2"}`.
   - If the model requests the calculator, the agent executes the tool and sends the result back to the model for a final answer.
   - Implement a simple loop to handle multiple tool calls if necessary.

3. **Calculator Tool**:
   - Implement a safe calculator that evaluates mathematical expressions (e.g., using `eval` with restricted globals, or a safer library like `asteval` or `simpleeval`).
   - Include error handling for invalid expressions.
   - Support basic arithmetic and functions (+, -, *, /, **, sqrt, etc.).

4. **Environment**:
   - Use a `.env` file for configuration (e.g., OLLAMA_HOST, MODEL_NAME).
   - Include a `requirements.txt` with `ollama`, `python-dotenv`, and optionally `simpleeval` or `asteval` for safe evaluation.

5. **Run Script**:
   - Provide a command-line script that accepts a user prompt and prints the agent’s response.
   - Example: `python scripts/run_agent.py "What is 123 * 456?"`
   - Optionally, include an interactive mode that loops until user exits.

6. **Documentation**:
   - In `README.md`, include:
     - Installation steps (Ollama, Python venv, dependencies).
     - Model pulling.
     - Running the agent with examples.
     - Explanation of how the agent decides to use the calculator.

7. **Best Practices**:
   - Use proper error handling.
   - Keep the agent stateless (each query independent) unless interactive mode is added.
   - Log tool usage for debugging.

Make all files ready for version control and include comments in code.
```

```