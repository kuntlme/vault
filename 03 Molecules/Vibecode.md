---
aliases:
  - Codeplay
  - web-code-editor
status: Running
tags:
  - molecule
  - project
  - coding
topic:
---

tweakcn
unDraw

[[Vibe Code Editor Project steps]]
Ai part reference
![[Pasted image 20250825231509.png]]
![[Pasted image 20250826011244.png]]
![[Pasted image 20250826011532.png]]
AI route
1. handles post request
2. accept the currentFile cotent, cursor position, and type of suggestion request.
3. analyzed the code context 
4. build an AI promt for the generation model
5. calls a local ai service.
## steps: 
1. validate body
2. analyze the code context
3. build ai prompt
4. call ai model
5. return response
![[Pasted image 20250828202511.png]]
![[Pasted image 20250828213307.png]]