# 🤖 Vector Chatbot with Memory

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Sayandip05/vector_chatbot/blob/main/VECTOR_CHATBOT.ipynb)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A smart chatbot that **remembers your conversations** using vector embeddings and ChromaDB! 🧠✨

## 🎯 What Does This Do?

Imagine talking to a chatbot that actually **remembers** what you told it before - your name, preferences, previous questions - just like talking to a real person! This project makes that happen.

### Simple Example:
```
You: My name is Sarah
Bot: Nice to meet you, Sarah!

[Later...]
You: What's my name?
Bot: Your name is Sarah!
```

## ✨ Key Features

- **🧠 Memory System** - Remembers all your conversations
- **🔍 Smart Search** - Finds relevant past conversations instantly
- **💬 Natural Chat** - Uses AI to give helpful responses
- **📊 Context Aware** - Uses past messages to give better answers
- **🚀 Easy to Use** - Just run in Google Colab, no setup needed!

## 🛠️ How It Works

1. **You send a message** → "I love Python programming"
2. **Bot converts to vectors** → Turns your message into numbers
3. **Stores in database** → Saves it in ChromaDB memory
4. **Retrieves context** → When you ask something, it finds related memories
5. **Generates response** → Uses AI model + memories to reply smartly

### Example Flow:
```
User: "I'm learning machine learning"
Bot: "That's great! ML is fascinating!"

[Next day...]
User: "Can you help me with coding?"
Bot: "Sure! Since you're learning ML, I'll use Python examples!" ✨
```

## 🚀 Quick Start

### Option 1: Google Colab (Easiest!)
1. Click the **"Open in Colab"** badge above
2. Run all cells (Runtime → Run all)
3. Start chatting!

### Option 2: Local Setup
```bash
# Clone the repository
git clone https://github.com/Sayandip05/vector_chatbot.git
cd vector_chatbot

# Install dependencies
pip install chromadb sentence-transformers transformers accelerate einops torch

# Open the notebook
jupyter notebook VECTOR_CHATBOT.ipynb
```

## 💡 Usage Examples

### Basic Chat
```python
# Initialize the bot
bot = Chatbot()

# Have a conversation
response = bot.chat("Hi! My name is Alex")
print(response)  # "Nice to meet you, Alex!"

response = bot.chat("What's my name?")
print(response)  # "Your name is Alex!"
```

### Search Past Conversations
```python
# Search your conversation history
results = bot.search_memory("Python", top_k=3)
for result in results:
    print(f"{result['role']}: {result['content']}")
```

### Interactive Chat
```python
# Start an interactive chat session
chat_with_bot()
```

## 📚 What You'll Learn

- 🔢 **Vector Embeddings** - How to turn text into numbers
- 💾 **Vector Databases** - How ChromaDB stores and retrieves data
- 🤖 **AI Chat Models** - Using Hugging Face transformers
- 🧠 **Memory Systems** - Building chatbots that remember
- 🔍 **Semantic Search** - Finding similar conversations

## 🏗️ Project Structure

```
vector_chatbot/
│
├── VECTOR_CHATBOT.ipynb    # Main notebook with complete code
├── README.md               # This file
├── LICENSE                 # MIT License
└── .gitignore             # Git ignore file
```

## 🧩 Components

### 1. **Embedding Handler**
Converts your text into vector embeddings using `sentence-transformers`.

### 2. **Memory Manager**
Stores and retrieves conversations using ChromaDB vector database.

### 3. **Chatbot**
The main AI that uses `Qwen2.5-0.5B-Instruct` model to generate responses.

## 🎮 Commands

When chatting with the bot:

- **Just type** - Regular conversation
- **`search: <query>`** - Search past conversations
- **`count`** - Show total memories stored
- **`exit`** - Stop chatting

## 🔧 Configuration

You can customize these settings in the notebook:

```python
CHAT_MODEL = "Qwen/Qwen2.5-0.5B-Instruct"  # AI model
EMBED_MODEL = "all-MiniLM-L6-v2"            # Embedding model
MAX_NEW_TOKENS = 256                        # Response length
TEMPERATURE = 0.7                           # Creativity (0-1)
TOP_K_RETRIEVAL = 6                         # Memories to retrieve
```

## 📊 Example Output

```
🎯 CHATBOT STARTED!
============================================================
Commands:
  • Just type to chat
  • 'search: <query>' - Search memory
  • 'count' - Show total memories
  • 'exit' - Stop chatting
============================================================

You: Hi! My favorite color is blue
Assistant: That's nice! Blue is a calming color.

You: What's my favorite color?
Assistant: Your favorite color is blue!

You: search: color
🔍 Searching for: 'color'

[1] user (similarity: 0.123)
    Time: 2025-01-15 10:30:45
    Content: My favorite color is blue

[2] assistant (similarity: 0.234)
    Time: 2025-01-15 10:30:46
    Content: That's nice! Blue is a calming color.

You: count
📊 Total memories: 4
```

## 🤔 How Does Memory Work?

Think of it like this:

1. **🗣️ You say something** → "I like pizza"
2. **🔢 Converts to numbers** → [0.23, 0.45, 0.67, ...]
3. **💾 Stores in database** → Saved with timestamp and metadata
4. **🔍 Later, you ask** → "What food do I like?"
5. **🎯 Searches similar** → Finds "I like pizza" (similar vectors)
6. **💬 Responds smartly** → "You like pizza!"

## 🌟 Use Cases

- **Personal Assistant** - Remembers your preferences
- **Customer Support** - Recalls previous issues
- **Learning Companion** - Tracks what you're studying
- **Journaling Bot** - Remembers your daily entries
- **Task Manager** - Keeps context of your projects

## 🛡️ Privacy Note

All conversations are stored **locally** in your environment:
- In Colab: Stored in `/content/memory_db/` (temporary)
- Locally: Stored in your project folder
- No data is sent to external servers (except AI model API calls)

## 🐛 Troubleshooting

**Problem:** "CUDA out of memory"
```python
# Use CPU instead
CHAT_MODEL = "Qwen/Qwen2.5-0.5B-Instruct"  # Smaller model
```

**Problem:** "Module not found"
```bash
pip install chromadb sentence-transformers transformers
```

**Problem:** Slow responses
- Use a smaller model
- Reduce `MAX_NEW_TOKENS`
- Reduce `TOP_K_RETRIEVAL`

## 📖 Learn More

- [ChromaDB Documentation](https://docs.trychroma.com/)
- [Sentence Transformers](https://www.sbert.net/)
- [Hugging Face Transformers](https://huggingface.co/docs/transformers)
- [Vector Embeddings Explained](https://www.pinecone.io/learn/vector-embeddings/)

## 🤝 Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **ChromaDB** - For the vector database
- **Hugging Face** - For the AI models
- **Sentence Transformers** - For embeddings
- **Qwen Team** - For the chat model

## 📧 Contact

Have questions? Found a bug? Want to share your project?

- Create an [Issue](https://github.com/Sayandip05/vector_chatbot/issues)
- Star ⭐ the repo if you find it useful!

---

<div align="center">

**Made with ❤️ by [Sayandip05](https://github.com/Sayandip05)**

⭐ Star this repo if you found it helpful!

</div>
