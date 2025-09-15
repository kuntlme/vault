---
aliases:
tags:
  - atom
  - coding
Reference Link: (insert link to book)
Page Number:
Topics:
  - AI
  - LLM
---
By the end of today, you'll be able to run open-source LLMs like **Mistral** or **LLaMA 3** on your laptop — no cloud, no API key, no GPU required.

## 🤔 What is Ollama?

Ollama is a command-line tool that makes it easy to run open-source LLMs (like Mistral, LLaMA 3, etc.) on your own machine.

- ✅ A simple CLI tool to run LLMs locally.
- 🐳 Think of it as “Docker for LLMs” — download a model once, and use it offline.
- 🤖 Supports models like **Mistral**, **LLaMA 3**, **Gamma**, **Code LLaMA**, etc.
- 🔒 Great for privacy, low-latency, and cost savings.

🌐 [https://ollama.com/](https://ollama.com)

## ⬇️ How to Install Ollama

### On Windows:
- Install WSL (Windows Subsystem for Linux):
  🌐 [https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install)

> 💡 WSL, or **Windows Subsystem for Linux**, is a feature of Windows that allows users to run a Linux environment directly on Windows without the need for a virtual machine or dual-booting.

Then install Ollama:

`curl -fsSL https://ollama.com/install.sh | sh`

---

### On Mac:
- 🍎 Run this command in Terminal:

`curl -fsSL https://ollama.com/install.sh | sh`

🎉 After install, type `ollama run mistral` to try your first model!


# 🔧 How Ollama Works (Behind the Scenes)

## 1. 📁 Where does it store models?

By default, Ollama stores downloaded models on your local disk:

**`~/.ollama/models`**

You can explore them here like cached files.

## 2. 🌐 Where does it get models from?

Ollama fetches models from the official **Ollama model registry**:

- 🔗 https://ollama.com/library
- These models are pre-converted to an efficient format (quantized .gguf under the hood).

> 💡 You don't need to visit HuggingFace manually unless you're doing advanced stuff.

---

### 🚶‍♂️ Step-by-Step: Using Ollama

**1️⃣ Step 1: Install Ollama**  
**2️⃣ Step 2: Pull a Model**  

`ollama pull mistral`

> ⬇️ This downloads the **Mistral 7B model** to your local disk.

**3️⃣ Step 3: Run the Model**  

`ollama run mistral`

> 💻 This launches an interactive prompt (like ChatGPT in terminal). Type any question, e.g.:  
`What is quantum computing?` 🔬

```markdown
# 🌐 Step 4: Use via API (Text Generation in Python/Node.js)

By default, Ollama also runs a local REST API on:

**http://localhost:11434** 🖥️

> ⚠️ Note: Make sure Ollama is running before making API calls

---

## 📋 Example: Generate Text via Node.js

```javascript
const axios = require('axios');

const response = await axios.post('http://localhost:11434/api/generate', {
    model: 'mistral',
    prompt: 'Explain Blockchain in simple terms',
    stream: false
});

console.log(response.data.response);
```

---

## 🖥️ You can also use curl:

```bash
curl -X POST http://localhost:11434/api/generate \
  -H "Content-Type: application/json" \
  -d '{
    "model": "mistral",
    "prompt": "Explain quantum computing in simple terms.",
    "stream": false
  }'
```

---

## 📋 Step 5: List All Installed Models

```bash
ollama list
```

> 📊 Shows all models downloaded and available locally

---

## 🗑️ Step 6: Remove/Unload a Model

To free up space:

```bash
ollama rm mistral
```

> 💾 Removes the model from your local storage
```

| Command | Description | Icon |
|---------|-------------|------|
| `ollama list` | Show installed models | 📋 |
| `ollama rm <model>` | Remove a model | 🗑️ |
| `curl` API calls | Interact via HTTP | 🌐 |
```

```markdown
# 🛠️ Step 7: Run Custom or Offline Models (Optional)

If you have a `.gguf` file or a model from HuggingFace:

1. 📁 Place the model file inside `~/.ollama/models/`
2. 📝 Create a **Modelfile** to define how it runs
3. ▶️ Run:

```bash
ollama create my-model -f Modelfile
ollama run my-model
```

You can also share and publish your own models to others via `ollama push`.

---

## 📋 Sample Modelfile Example

```dockerfile
FROM /path/to/your/model.gguf
PARAMETER temperature 0.7
PARAMETER num_ctx 4096
TEMPLATE "{{ .Prompt }}"
```

---

## 🌐 Sample Use Case

**How do I build a chat test using Ollama + Express?** 💬

You use `ollama run` in backend or call its API (`/api/generate`) from Node.js server, and build a frontend to send messages to it — like ChatGPT but local.

### Example Express.js endpoint:

```javascript
app.post('/api/chat', async (req, res) => {
  const response = await axios.post('http://localhost:11434/api/generate', {
    model: 'mistral',
    prompt: req.body.message,
    stream: false
  });
  res.json({ reply: response.data.response });
});
```

---

## 📋 Summary Cheatsheet

| Command | Description | Icon |
|---------|-------------|------|
| `ollama pull <model>` | Download a model | ⬇️ |
| `ollama run <model>` | Run the model in terminal | ▶️ |
| `ollama list` | Show installed models | 📋 |
| `ollama rm <model>` | Remove a model | 🗑️ |
| `curl http://localhost:11434/api/...` | Access model via HTTP | 🌐 |
| `ollama create <name> -f <file>` | Create custom model | 🛠️ |

---

> 💡 **Tip**: Visit [Ollama's official documentation](https://github.com/ollama/ollama) for more advanced usage and examples!


```markdown
# ⚠️ You may face an error like this:

**Error:** `Error: failed to pull manifest`
**Pulling metadata:** 
```
error: maximum retries exceeded
Get "https://b2c05a9b1978c25eabcd6ae0f7b3bbbc.2.r2.cloudflarestorage.com/ollama/..."
```

## 🔧 Then add DNS Record in your system: 1.1.1.1

### Procedure:
- Open Network Settings
- Change DNS to Cloudflare's: `1.1.1.1`
- This often resolves download issues with Ollama

---

## 📊 Feature Comparison: Hugging Face vs Ollama

**What it is**

| Feature | Hugging Face 🤗 | Ollama 🦙 |
|---------|----------------|-----------|
| **Purpose** | A massive open-source model hub for LLMs | A local LLM runtime focused on running models on your own machine |
| **Where models run** | Mostly cloud-based or via Colab/Python | Entirely local (on your laptop/desktop) |
| **Model format** | Transformers (PyTorch, TensorFlow, Safetensors, etc.) | Ollama's own format (GGUF under the hood) |
| **Interface** | Python-based (transformers, diffusers, etc.) | CLI + REST API (`ollama run`, `/api/generate`) |
| **Hosting** | Hosts thousands of models by researchers and orgs | Downloads from curated model registry (Ollama Hub) |
| **Usage** | Best for research, training, and online inference | Best for private, offline inference |
| **Models Available** | GPT2, GPT-J, LLaMA, Mistral, BERT, etc. | Mistral, LLaMA2/3, TinyLLaMA, CodeLLaMA, Phi, etc. (quantized) |
| **Ease of Use** | Requires Python setup and environment | One-line install, models ready with `ollama run` |

---

> 💡 **Tip**: If you encounter network issues, try changing your DNS to Cloudflare (1.1.1.1) or Google (8.8.8.8) for better connectivity to Ollama's servers.
```

```markdown
# ⚙️ Customization

Easily fine-tune and upload custom models

Custom model YAML configs supported but limited fine-tuning

---

## 📊 Summary

**Hugging Face** = A global library of models for devs and researchers. Best when you need access to any model, large-scale deployment, or training. 🌍

**Ollama** = Fast, private, local tool to run quantized LLMs easily on your laptop, with no setup hassles or API costs. 💻

---

## 🚀 Try These Models Locally

| Model Name | Parameters | Use Case | Command | Icon |
|------------|------------|----------|---------|------|
| **mistral** | 7B | General Purpose | `ollama run mistral` | 🌬️ |
| **llama3** | 8B | Chat Assistant | `ollama run llama3` | 🦙 |
| **gemma** | 2B | Lightweight AI | `ollama run gemma` | 💎 |
| **codellama** | 7B | Code Generation | `ollama run codellama` | 💻 |
| **tinyllama** | 1B | Ultra Lightweight | `ollama run tinyllama` | 🔬 |

> 💡 **Tip**: Start with smaller models like `tinyllama` or `gemma` for faster response times, then move to larger models like `llama3` for more complex tasks.
```

# 💡 Use Case: Text Generation

You can use LM Studio for:
- 💡 Brainstorming ideas
- 📚 Studying concepts
- 🤖 Local Chatbots
- 🔒 Secure private chat without internet

---

# ⚙️ Bonus Settings You Can Play With

- **🌡️ Temperature**: Controls creativity
- **🎲 Top_p, Top_k**: Controls randomness
- **🧠 Context Length**: How many tokens model can remember
- **📋 Prompt Templates**: For chat-style prompt formatting (like ChatGPT)

---

### 📦 What is GGUF Format?

- Optimized model format used in **LM Studio, Ollama**, and **Text Generation Web UI**
- Supports quantized models (smaller size, faster on CPU)
- Efficient for local deployment

---

## 📊 Bonus: List of Lightweight Models for Low-End Laptops

| Model Name | Size | Description | Icon |
|------------|------|-------------|------|
| **tinyllama** | ~0.5GB | Very small, good for testing | 🔬 |
| **gemma:2b** | ~1.5GB | Google's open-source model | 💎 |
| **mistral:instruct** | ~4GB | Great for Q&A and chat tasks | 🌬️ |
| **llama3:8b** | ~7GB | Meta's latest LLM (8B params) | 🦙 |

---

## 🚀 Pro Tips

- ⬇️ Use `ollama pull mistral` to download a model without running it
- 🔗 In LM Studio, you can download models directly by entering the HuggingFace link
- 📊 Check CPU/RAM usage while running models to monitor performance
- 💾 Start with smaller models if you have limited RAM
- 🔄 Restart Ollama if you encounter performance issues

> 💡 **Remember**: The smaller the model, the faster it runs but with potentially less accurate responses. Choose based on your hardware capabilities!