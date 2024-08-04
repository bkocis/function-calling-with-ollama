# Ollama Chat Application

This Python application demonstrates how to use the Ollama library to create a chat interface with additional functionalities like weather retrieval and number comparison.

## Features

- Interactive chat with an AI model (llama3.1:8b-instruct-fp16)
- Function calling capabilities
- Weather information retrieval
- Number comparison

## Prerequisites

- Python 3.x
- `ollama` library
- `requests` library

## Installation

1. Clone this repository or download the script.
2. Install the required libraries:

```
pip install ollama requests
```

## Usage

Run the script using Python:

```
python ollama_chat.py
```

The application will start an interactive chat session. You can ask questions or use the following functionalities:

- Get current weather for a city
- Compare two numbers

To exit the application, type 'quit'.

## Functions

### `get_current_weather(city)`

Retrieves the current temperature for a specified city using the wttr.in API.

### `what_is_bigger(n, m)`

Compares two numbers and returns which one is bigger or if they are the same.

### `chat_with_ollama(user_question)`

Sends a user question to the Ollama model and handles function calls if applicable.

### `chat_with_ollama_no_functions(user_question)`

Sends a user question to the Ollama model without function calling capabilities.

## Function Calling

This application implements function calling, a feature that allows the AI model to invoke specific functions based on the user's input. Here's how it works:

1. The `chat_with_ollama()` function sends the user's question to the Ollama model along with a list of available tools (functions).

2. If the model determines that a function call is necessary to answer the user's question, it returns a `tool_calls` object in its response.

3. The main loop checks for the presence of `tool_calls` in the model's response.

4. If `tool_calls` are present, the application iterates through them and executes the corresponding functions with the provided arguments.

5. The results of these function calls are then printed to the user.

6. If no `tool_calls` are present or if the arguments are invalid, the application falls back to using the model's direct response.

This approach allows the AI to leverage external data sources (like weather information) or perform specific computations (like number comparison) when needed, enhancing its ability to provide accurate and relevant responses.

## Main Loop

The `main()` function runs an infinite loop that:

1. Prompts the user for input
2. Sends the input to the Ollama model
3. Processes any function calls returned by the model
4. Displays the result or the model's response

## Note

This application requires an active internet connection to communicate with the Ollama API and retrieve weather information.
