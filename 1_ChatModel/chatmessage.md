## Different Chat Message Types in LangChain

LangChain provides these built-in message classes from `langchain_core.messages`:

## 1. SystemMessage

Sets the behavior, tone, or personality of the assistant.

```python
from langchain_core.messages import SystemMessage

SystemMessage(content="You are a helpful math tutor.")
```

**Purpose**:

- To set the behavior, personality, or rules for the entire conversation or AI assistant.

- This message usually comes first in a chat to give the model context about how to respond.

**When to use**:

- When you want to control tone, style, or instructions globally.

- Example: “You are a friendly tutor.”, “Answer as a Shakespearean poet.”

- To add constraints or guidelines, like "Keep answers short" or "Never reveal you are an AI."

**Real-life use case**:

- An AI customer support bot starts with:

- `SystemMessage("You are a patient and helpful customer support agent.")`

<br>





## 2. HumanMessage

Represents a message from the user (you).

```python
from langchain_core.messages import HumanMessage

HumanMessage(content="Can you explain recursion?")
```


**Purpose**:

* Represents a message from the human user interacting with the assistant.

* Usually the user’s questions, commands, or statements.

**When to use**:

* Every time the user inputs something new in the chat.

* When simulating or replaying chat history, each human turn is a `HumanMessage`.

**Real-life use case**:

* User types:

* `HumanMessage("What’s the weather like today?")`

<br>




## 3. AIMessage

Represents a response from the AI (optional when simulating past conversation).

```python
from langchain_core.messages import AIMessage

AIMessage(content="Sure! Recursion is when a function calls itself.")
```

**Purpose**:

* Represents the assistant’s previous responses.

* Used mostly when you want to pass the conversation history to the model so it can respond coherently with context.

**When to use**:

* When maintaining and replaying conversation history in multi-turn chats.

* For simulating previous assistant responses, so the model "remembers" past outputs.

**Real-life use case**:

* After user asks a question, AI replies:

* `AIMessage("The weather today is sunny with a high of 75°F.")`

* Then the next user input and AI response build on this history.


<br>




## 4. ChatMessage

A generic message where you can set any custom role.

```python
from langchain_core.messages import ChatMessage

ChatMessage(role="coach", content="Keep going, you're doing great!")
```

**Purpose**:

* A generic message type that lets you specify any custom role beyond just `system`, `human`, or `assistant`.

* Useful for specialized workflows or extended roles.

**When to use**:

* When you want to create custom roles like `"coach"`, `"mentor"`, `"moderator"`, `"translator"`, etc.

* When building complex multi-role conversations or agent systems.

**Real-life use case**:

* In a collaborative AI tool, you might have:

* `ChatMessage(role="translator", content="Translate this to French.")`

* Or in a game, roles like `"npc"` (non-player character) or `"player"`.


---

<br>

### Example: Using Multiple Message Types


```python
from langchain_openai import ChatOpenAI
from langchain_core.messages import SystemMessage, HumanMessage, AIMessage

chat = ChatOpenAI()

messages = [
    SystemMessage(content="You are a friendly assistant."),
    HumanMessage(content="What's the capital of France?"),
    AIMessage(content="The capital of France is Paris."),
    HumanMessage(content="And what about Germany?")
]

response = chat.invoke(messages)
print(response.content)
```
---
<br>


### Why Use Different Message Types?
---
<br>

| Message Type  | Purpose                                        |
| ------------- | ---------------------------------------------- |
| SystemMessage | Set rules or personality                       |
| HumanMessage  | Represents user input                          |
| AIMessage     | Simulate or refer to past AI responses         |
| ChatMessage   | Use custom roles like "coach", "teacher", etc. |

<br>
<br>

| Message Type      | When to Use                                  | Role in Conversation                             |
| ----------------- | -------------------------------------------- | ------------------------------------------------ |
| SystemMessage     | To set behavior, style, instructions upfront | AI system-level instructions (the “rules”)       |
| HumanMessage      | For all user inputs                          | User's side of the conversation                  |
| AIMessage         | To provide AI’s previous replies in history  | Assistant’s side, for context in multi-turn chat |
| ChatMessage       | When needing custom roles beyond default     | Flexible roles for complex or multi-role dialogs |

