# LLM Completion vs. Chat

## LLM Methods Overview

### `llm.complete(prompt: str)` - single-turn
- Designed for single-turn completion tasks.
- Suitable for text generation, summarization, and Q&A tasks.

### `llm.chat(messages: List[ChatMessage])` - multi-turn
- Enables multi-turn chat-style interactions.
- Retains conversation history for context-aware responses.

## 🔍 Key Differences

| Feature          | `llm.chat()` | `llm.complete()` |
|-----------------|-------------|----------------|
| **Input**       | List of `ChatMessage` objects (conversation history) | Single `str` prompt |
| **Use Case**    | Chatbots, multi-turn conversations | Single-turn completions (e.g., summarization, text generation) |
| **Maintains Context?** | ✅ Yes | ❌ No |
| **Example Models** | `gpt-4-turbo`, `llama3-70b` | `text-davinci-003`, `llama3-8b` |

## 🚀 When to Use What?

- **Chatbot-style interactions** → Use `llm.chat()`
- **Text completion, summarization, Q&A** → Use `llm.complete()
