---
tags:
  - atom
  - coding
Topics:
  - AI
  - LLM
---
## Day 1: What is LLM? Why LLMs Matter in 2025?

**What is LLM?**
* **LLM** = Large Language Model
* It’s a type of **Artificial Intelligence** that can understand, generate, and interact using **human language**
* Trained on **massive text data** like books, websites, Wikipedia, etc.
* Example: ChatGPT, Claude, Gemini
![[Pasted image 20250831201735.png]]
Think of LLM as a very advanced auto-complete engine, but for full conversations, code, essays, and more.

---

**Why LLMs Matter in 2025?**
* Replacing traditional software in many areas
* Powering apps like chatbots, code assistants, AI tutors, and even business analysts
* Easy to integrate in your own apps
* Future of jobs = You + AI (LLMs will be your assistant)

---

**Famous LLMs You Should Know**
* **GPT** (OpenAI) — ChatGPT, GPT-4o
* **Claude** (Anthropic - AI safety and research company)
* **LLaMA** (Meta, open-source)
* **Mistral** (Open-weight French LLM)
Here is the text extracted from the image:

**How Does an LLM Actually Work?**

**Simple explanation:**

1.  **Tokenization:** Breaks your text into smaller units (tokens)
2.  **Embedding:** Converts tokens into numbers (vectors)
3.  **Transformer:** Uses an **attention mechanism** to decide which words matter
4.  **Prediction:** Generates the next token (word/letter) based on training

“**Attention is all you need**” – the core of how LLMs work
![[Pasted image 20250831202404.png]]
![[Pasted image 20250831202531.png]]
### 🧩 Step 1: Tokenization
This step breaks the input text into smaller units called tokens.

These tokens could be words, subwords, or even characters (depending on the tokenizer).

Input = "Most famous cheese in France?"

Tokens (subword-style): [_Most, _famous, _cheese, _in, _France, ?]

Important Note: These are not just words — spaces matter (e.g., see _famous). This helps the model handle unknown words and multiple languages.

You can also visualize this process using the [OpenAI Tokenizer](https://platform.openai.com/tokenizer).

### 🧩 Step 2: Embedding

* Now, each token is converted into a **vector** — a list of numbers.
* These vectors **represent the meaning** of the tokens in mathematical space.
* "cheese" → `[0.12, -0.55, 1.03, ...]` (just an example vector)

If a sentence is tokenized into **5 tokens**, you will get **5 separate vectors** — one for each token.

**Example:**

`["I", "love", "AI", "model", "s"]`

[
    [0.01, -0.92, 0.11, ..., 0.34], // vector for "I"
    [0.45, 0.82, 0.66, ..., 0.91], // vector for "love"
    [0.12, 0.34, -0.75, ..., 0.01], // vector for "AI"
    ...
]

Each token → one vector (usually 768 or 1024 dimensions depending on the model).

🧠 Do all LLMs give the same vector for apple?
No - embeddings vary depending on:

1. The model (GPT, LLaMA, BERT all have different embeddings).
2. The training data (different LLMs "understand" words differently).
3. The tokenizer used (byte-pair encoding, WordPiece, etc.).

### 🧩 Step 3: Transformer (Attention)

* Here comes the smart part: the **transformer** looks at the **entire sentence** and tries to understand:
    * What is important?
    * What words are related?
    * What to focus on?

* **Example:**
    * The model learns that "**cheese**" and "**France**" are related.
    * "**famous**" adds extra weight.
    * The attention mechanism focuses more on "**cheese**" and "**France**".

### 📌 This is like a human thinking:

"Hmm... I've heard of Brie, Camembert... those are cheeses from France."

### 🧩 Step 4: Prediction (Output)

* Now the LLM is ready to **predict the next most likely tokens.**

* **Given the input:** "Most famous cheese in France?"
    * The model might generate: "**Brie**"
    * Or, if allowed to continue: "**Brie is one of the most well-known cheeses in France.**"

![[Pasted image 20250831204602.png]]

### 👍 The prediction depends on:

* The training data
* The prompt
* Temperature (creativity)
* Max token length

---

### 🧠 Tip for Students:

LLM doesn't "search" the web — it "predicts" based on what it has already learned from massive training data.
![[Pasted image 20250831205513.png]]
![[Pasted image 20250831205604.png]]

The token with the highest probability is not always chosen, and that's because of **sampling strategies** and **decoding settings** like:

### 🔥 1. Temperature

* Controls **randomness**.
* **Lower (~0.2):** More **deterministic** (almost always picks top token).
* **Higher (~1.0+):** More **diverse**, samples from wider range.
![[Pasted image 20250831205932.png]]
### 📊 2. Top-k Sampling

* Only consider the **top-k most probable tokens** (e.g., top 40).
* Randomly sample from them based on their probabilities.
* Discards the rest.

### 🎯 3. Top-p Sampling (Nucleus Sampling)

* Picks the **smallest set of tokens** whose cumulative probability is $\ge p$ (e.g., 0.9).
* Then samples **within that set**.
* More adaptive than top-k.

![[Pasted image 20250831211117.png]]

### 🛡️ 4. Min-p (minimum probability cutoff)

* Discards tokens whose probability is **below a threshold** (e.g., 0.1).
* Helps avoid unlikely garbage outputs.
![[Pasted image 20250831211402.png]]
![[Pasted image 20250831211827.png]]