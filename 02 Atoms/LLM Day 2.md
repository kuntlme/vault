---
aliases:
tags:
  - atom
Reference Link: (insert link to book)
Page Number:
Topics:
  - LLM
  - AI
---
# Day 2: HuggingFace & Open-Source LLMs

Today, you’ll explore the **HuggingFace** ecosystem, learn how to search and use open-source LLMs, understand quantized models, and run text generation in Colab using the 🤗 transformers library.

---

### What is HuggingFace?

A platform for hosting ML models, datasets, and tools.  
Like GitHub, but for AI models.  
Running AI applications directly from the browser via **Spaces**  

🔗 **Website:** [https://huggingface.co](https://huggingface.co)

---

### HuggingFace Hub includes:

- **Models:** LLMs like GPT2, Mistral, LLaMA, etc.  
- **Datasets:** IMDB, SQuAD, etc.  
- **Spaces:** Web apps built using models.  
- **Inference API:** Test models directly in the browser or through the API.  


| Component       | Description |
|-----------------|-------------|
| 🧠 **Models**      | Pretrained models like GPT2, Mistral, LLaMA, BERT |
| 📊 **Datasets**    | Public datasets like SQuAD, IMDB, and Common Crawl |
| ⚡ **Inference API** | Free testing interface for models |
| ✏️ **Spaces**       | Public web apps built using HuggingFace models |

---

**In simple words:**  
**Inference = using a trained AI model to make predictions or generate results.**

## 🤖 What Is Hugging Face Inference API?

The Inference API by Hugging Face lets you use AI models hosted on Hugging Face servers,  
without downloading or running them locally.  

So you don’t need a GPU or set up PyTorch or anything.  

---

## 🖋️ What Happens Behind the Scenes?

1. You choose a model (e.g., [gpt2](https://huggingface.co/gpt2), [facebook/bart-large](https://huggingface.co/facebook/bart-large), [mistralai/Mistral-7B](https://huggingface.co/mistralai/Mistral-7B))  
2. Hugging Face hosts that model on their own powerful GPUs  
3. You make a REST API call to  
   👉 `https://api-inference.huggingface.co/models/{model-name}`  
4. The model **runs inference** = takes your input, generates prediction/output  
5. You get the result back  

---

## 🤔 Why Do People Always Say "You Need a GPU for AI"?

Because **GPUs are built for doing many math calculations at the same time** —  
which is exactly what AI models need.  

---

## ⬛ What is a CPU?

- **CPU = Central Processing Unit**  
- It's like your computer’s **main brain**  
- Designed to handle **a few tasks very fast**  
- Good at: Opening apps, Running OS, Doing a few calculations at a time  

👉 A **very smart person**, doing 1 math problem at a time — super accurate, but only one thing at once.

## 📑 What is a GPU?

- **GPU = Graphics Processing Unit**  
- Originally made for games, to draw images (lots of pixels, colors)  
- But later we realized: **“Wow, it can do 1000s of math problems in parallel!”**  

---

## 🔢 It has thousands of small cores that can do:

- Matrix multiplications  
- Vector operations  
- Math needed for AI  

---

👉 *A core is like a **mini-brain** inside your computer’s processor. Each core can **do one task (like a math problem) at a time.***

## 💻 In a CPU

- Most modern CPUs have **4 to 16 cores**  
- So your computer can run **4 to 16 tasks at once** (parallel processing)  

🧠 Imagine a **CPU with 4 cores** like:  
👉 4 students solving 4 different problems at the same time.  

---

## 🖼️ In a GPU

- GPUs have **hundreds or even thousands of smaller cores**  
  (e.g., *NVIDIA RTX 4090 has 16,384 cores*)  

🧠 Imagine a **GPU with 1000 cores** like:  
👉 A classroom with **1000 students**, each doing a tiny piece of a huge puzzle — all at once.

This photo seems to be a presentation slide explaining how AI tasks are run and whether they can be executed on a CPU. Here is the content of the photo in markdown format:
Because AI tasks (like LLMs, image generation, etc.) involve:
 * Multiplying giant matrices (like 1000x1000 numbers)
 * Repeating this millions of times
The more cores you have:
 * The more pieces of the task can be done simultaneously
 * So the job finishes much faster
✅ Can You Run AI Models on a CPU?
You can run small AI models on a CPU, especially low-size models, and it's a great way to get started without needing a GPU.
Small LLMs like distilBERT, TinyLlama, GPT2-small, mistral-7B (with quantization)
Tasks like:
 * Text classification
 * Question-answering
 * Basic text generation
 * Sentiment analysis
￼💖￼ These are lightweight models that don't need thousands of GPU cores.

## 🔹 What is a Quantized Model?
Quantization means reducing the model size by storing numbers with lower precision (e.g. int4 instead of float32), making them:
 * 🟢 Faster to load
 * 🟢 Lighter in size (less storage required)

## 1️⃣ 1. What Do You Mean by "Model Parameters"?
In AI models, parameters are the numbers the model "learns" during training.
AI Model = Predict Next word
For that, it needs data
Imagine:
 * You train a model to translate Hindi to English.
 * It learns millions (or billions) of rules, weights, and values.
 * These are all stored as numbers.
For example:
 * GPT-2 has 124 million parameters
 * GPT-3 has 175 billion parameters
A "parameter" = A learned number (like a weight) the model uses to generate predictions. A parameter is always a number (value)—usually a weight—stored inside the model.
Summary Table
| Term | Simple Meaning | Example |
|---|---|---|
| Weight | How important something is | "great" = 0.95, "boring" = -0.6 |
| Value | The actual number stored in the model | 0.95, -0.6, etc. |
| Rule | A learned pattern or decision that the model makes | "If not before, good = negative." |
<span style="color:pink">💖</span> AI doesn't write if-else—it learns patterns by adjusting weights from lots of data.

Final Analogy
Imagine you're learning to drive:
 * You learn how much to press the accelerator (weight)
 * You store that info in your brain (value)
 * After many drives, you know what to do at a turn (rule)
AI does the same, but in mathematical form.
## 🔢 2. How to Calculate Model Size from Parameters?
Each parameter is a number.
Usually stored as:
 * float32 → takes 4 bytes (default)
 * int8 → takes 1 byte
 * int4 → takes 0.5 byte
| Memory unit | Description |
|---|---|
| Kilo Byte | 1 KB = 1024 Bytes |
| Mega Byte | 1 MB = 1024 KB |
| Giga Byte | 1 GB = 1024 MB |
| Tera Byte | 1 TB = 1024 GB |
| Peta Byte | 1 PB = 1024 TB |
| Hexa Byte | 1 EB = 1024 PB |
| Zetta Byte | 1 ZB = 1024 EB |
| Yotta Byte | 1 YB = 1024 ZB |
| Bronto Byte | 1 Bronto Byte = 1024 YB |
| Geop Byte | 1 Geo Byte = 1024 Bronto Bytes |
Formula:
Model Size = Number of Parameters x Size of each parameter

Example:
| Model | Parameters | Precision | Size |
|---|---|---|---|
| GPT-2 | 124M | float32 (4 bytes) | 124M x 4 = ~496 MB |
| GPT-2 (int8) | 124M | int8 (1 byte) | 124M x 1 = ~124 MB |
| LLaMA 7B | 7B | float32 | 7B x 4 = ~28 GB |
| LLaMA 7B (4-bit) | 7B | int4 (0.5 byte) | 7B x 0.5 = ~3.5 GB |
So when people say "quantized model is smaller", it's because we store those parameters with lower precision.
Quantization means converting the model's numbers (parameters) from high-precision to low-precision to make the model smaller and faster.

Analogy:
Imagine storing $123,456789

Full: float32 (full precision) → takes more space
Rounded: int4 or int8 → less accurate, but way smaller
Types of Precision:
| Type | Bits | Bytes | Accuracy | Size |
|---|---|---|---|---|
| float32 | 32 bits | 4 bytes | 🔥 High | ❌ Big |
| int8 | 8 bits | 1 byte | 👍 Good | ✅ Smaller |
| int4 | 4 bits | 0.5 byte | 👌 Acceptable | ✅✅ Smallest |

### 🧠 What is a Low-Size Model?
A low-size model:
 * Has fewer parameters (e.g., 60M, 124M)
 * Or is quantized (4-bit, 8-bit)
 * Can run on CPU or less RAM (under 2-4 GB)
🔤 Naming Convention of Models
Model names often include architecture, size, quantization, and version:
Example: TheBloke/Mistral-7B-Instruct-v0.1-GGUF
| Part | Meaning |
|---|---|
| TheBloke | Organization/maintainer |
| Mistral | Base model architecture |
| 7B | Model size (7 billion parameters) |
| Instruct-v0.1 | Instruction-tuned version |
| GGUF | File format used in quantized models |

### 🧠 What Does 7B, 13B, 70B Mean?
These represent the number of parameters in the model:
| Model Size | Description | Requirements |
|---|---|---|
| 1B-7B | Lightweight models | Can run locally |
| 13B-30B | Mid-size, better reasoning | Requires GPU |
| 65B-180B | Powerful but slow and heavy | Needs high-end GPU or cloud |
⚠️ More parameters = more intelligence but needs more RAM and time

Bonus: HuggingFace Model Picker Cheatsheet
| Use Case | Model Example | Notes |
|---|---|---|
| Chatbot | mistralai/Mistral-7B-Instruct | Fast, instruction-tuned |
| Summarization | facebook/bart-large-cnn | Great for articles |
| Code Generation | Salesforce/codegen-2B | For Python/JS code |
| Hindi LLMs | ai4bharat/IndicBART | Multilingual support |
| Quantized Model | TheBloke/Mistral-7B-GGUF | Lightweight, fast |
Example: https://huggingface.co/google/gemma-3-4b-it-gqt-q4_0-gguf
What is 🤗 Transformers Library?
 * Official Python library by HuggingFace.
 * Gives access to hundreds of pretrained models.
 * Just 3-4 lines of code to load and use LLMs.
 * Supports multiple tasks: text generation, classification, translation, etc.
✍️ Hands-On Activity
Goal: Generate text using a pretrained model
 * Open Google Colab
 * Paste and Run:
<!-- end list -->
!pip install transformers

from transformers import pipeline

generator = pipeline("text-generation", model="gpt2")
output = generator("Bharat ka AI future", max_length=50, num_return_sequences=1)

print(output[0]["generated_text"])

✅ You'll see GPT-2 generate Hindi+English text based on the prompt.
✅ max_length (int)
This defines the total length of the generated sequence including the input prompt tokens.
<br>
<span style="color:red">📌</span> It means: "how long should the final output be (including input)?"
 * If the prompt has 10 tokens, and max_length=50, the model will generate up to 40 new tokens.
 * This is a hard limit. If the model hits it, it stops generating even if the sentence isn't complete.
✅ num_return_sequences (int)
This specifies how many different completions you want the model to generate.
<br>
<span style="color:red">📌</span> It means: "give me this many variations of the output."
 * If set to 1 → you get one response
 * If set to 3 → you get three different versions of the response (helpful for sampling diverse completions)