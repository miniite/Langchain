# ChatModel
In LangChain, Chat Models refer to interfaces for interacting with chat-based language models, like OpenAI’s ChatGPT (gpt-4, gpt-3.5), Anthropic’s Claude, or other models that support message-style inputs and outputs.

## What exactly is ChatModel?
Chat Models are a wrapper around language models (LLMs) that are ***designed to interact via structured chat messages instead of plain text***. 

These models expect and return a list of messages (e.g., from a user, assistant, or system), **mimicking how chatbots work**.

LangChain abstracts this into a unified interface so you can:

* Work with various chat-based LLMs

* Pass structured message history

* Use chat-specific features like roles (system, user, assistant)

## Why Use Chat Models in LangChain? (Short & Simple)

Chat models let you build smart, memory-aware conversations with AI. 

***Unlike plain LLMs, they understand chat history, roles, and can act like real assistants.***

---

| Use Case              | Why Chat Models?                                  |
| --------------------- | ------------------------------------------------- |
| Customer Support      | Remembers past questions for smooth conversations |
| AI Tutor              | Adjusts replies based on learning progress        |
| Personal Assistant    | Keeps user preferences, tasks, and context        |
| Document Q\&A         | Handles follow-up questions naturally             |
| Game NPCs             | Feels alive by remembering previous player chats  |


## Key Components
1. ChatMessage: 

    * Represents a message with a specific role.

    * Roles: SystemMessage, HumanMessage, AIMessage, or generic ChatMessage(role, content).

2. ChatModel Interface:

    * Extends the base BaseLanguageModel.

    * Accepts a list of messages and returns a single message response.

3. Popular Implementations:

    * ChatOpenAI: For OpenAI's chat models (like GPT-3.5, GPT-4).

    * ChatAnthropic: For Claude.

    * ChatGooglePalm, ChatCohere, etc.

<br>
<br>

## The Main Code elements to create a Basic ChatModel

> model= *ChatModelName()*  
> result = model.**invoke(** *input* **)**

- `ChatModelName()` creates an instance of the chat model.
- `.invoke()` sends input (a prompt or messages) and returns a response.
- Here `model` and ` result` are just variable names
---

<br>
<br>

### Example 1: Creates a Basic ChatModel

```python
# Import Statements
from dotenv import load_env
from langchain_openai import ChatOpenAI 

# Load enivronment variables from .env
load_env()

# Create a ChatOpenAI model 
model = ChatOpenAI()

# Invoke the model with a message 
result = model. invoke("What is 81 divided by 9")
print("Full result: ")
print(result)
print("Content only:")
print(result.content)
```
### 1. ChatMesage

