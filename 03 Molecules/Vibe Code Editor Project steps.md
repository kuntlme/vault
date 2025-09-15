---
aliases:
tags:
  - molecule
Reference Link: https://www.youtube.com/watch?v=Mfr8pi-jvu0&t=34827s
Page Number:
Topics:
  - Project Steps
---
# Summary -
These are the full project step by step work.

# Content -

This project is an ambitious endeavor to build a **full-stack web-based AI IDE (Integrated Development Environment)**, drawing inspiration from platforms like StackBlitz. It aims to provide a **fully customized online coding environment** using a select few powerful third-party tools while building most functionalities from scratch.

Here's a detailed breakdown of the project:

### **Project Goal and Purpose**

The primary goal is to create an **online, web-based IDE** that allows users to develop applications directly in their browser. A key differentiator is the **integration of AI capabilities**, offering code suggestions and a chat-based assistant. The project is designed to be fully customizable, avoiding extensive reliance on external packages where possible.

### **Key Features**

*   **User Authentication**: Implemented via **NextAuth.js**, supporting login through both **Google and GitHub** accounts.
*   **User Interface**: Features a modern design with support for both **light and dark modes**.
*   **Project Management**:
    *   Users can **create new projects** by selecting from a variety of pre-defined templates such as React, Next.js, Express, Vue, Hono, and Angular. These templates are categorized for easy navigation.
    *   A **dashboard** displays a list of user projects, including recent and starred (favorited) projects.
    *   **CRUD (Create, Read, Update, Delete)** operations are fully supported for projects, along with the ability to duplicate projects and copy project URLs.
*   **File Explorer**:
    *   Presents a **tree-like view** of all project files and folders.
    *   Allows users to **add new files and folders, rename existing ones, and delete them** in real-time.
    *   **Real-time synchronization** ensures that changes in the editor are reflected instantly in the file explorer and vice-versa.
    *   **Unsaved changes are indicated** with a visual marker.
*   **Code Editor (Monaco Editor)**:
    *   Integrated with the **Monaco Editor** (the same editor used in VS Code) for a rich coding experience.
    *   Provides standard IDE features like **syntax highlighting, formatting, auto-completion, and jump-to-definition**.
    *   **Real-time code editing** is linked to immediate output previews.
    *   Supports **keyboard shortcuts** for common actions, including saving (Ctrl+S), accepting AI suggestions (Tab), and rejecting AI suggestions (Escape).
    *   **Smooth cursor animations** enhance the editing experience.
*   **AI Assistant**:
    *   Offers **real-time, context-aware AI code suggestions** directly within the editor.
    *   Includes an **"Open Chat" panel** where users can interact with an AI assistant, copy code snippets, and receive explanations or debugging help.
    *   Leverages **Code Rabbit** for AI-powered code reviews in GitHub pull requests.
*   **Web Containers and Terminal**:
    *   Integrates **WebContainers** (from StackBlitz) to enable running Node.js applications and executing operating system commands directly within the user's browser tab.
    *   Provides a **live output preview** of the running application.
    *   A **fully functional terminal**, powered by **Xterm.js**, allows users to run commands, view installation logs, and interact with their project's environment.
*   **Progress and Status Indicators**: Displays detailed loading states, progress bars, and success/error messages during project setup, dependency installation, and other operations.

### **Core Technologies Used**

*   **Frontend Framework**: **Next.js** (v15.3.4) - The foundational React framework providing server-side rendering, routing, and optimizations.
*   **UI Components**: **Shadcn UI** - A collection of beautifully designed, accessible, and customizable UI components.
*   **Database**: **MongoDB** - A NoSQL database used for storing project and user data.
*   **ORM/Database Toolkit**: **Prisma** - A next-generation ORM simplifying database interactions and schema definition for MongoDB.
*   **Authentication**: **NextAuth.js (Auth.js)** - Handles robust authentication, specifically Google and GitHub OAuth, with a Prisma adapter for database integration.
*   **Code Editor Core**: **Monaco Editor** - The powerful text editor component behind VS Code, providing the core editing experience.
*   **Local AI Engine**: **Ollama** - Allows running large language models (LLMs) locally, specifically **Code Llama** (a 7B parameter model is used for suggestions and chat), eliminating the need for external AI API keys and ensuring data privacy.
*   **Browser-Based Runtime**: **WebContainers** - A crucial technology enabling Node.js environments to run entirely within the browser, provided by StackBlitz.
*   **Terminal Emulator**: **Xterm.js** - A feature-rich JavaScript library for building terminal emulators in web applications.
*   **State Management**: **Zustand** - A minimalist state management library, used for managing complex states like the file explorer.
*   **Styling**: **Tailwind CSS** - A utility-first CSS framework.
*   **Theming**: `next-themes` - For dynamic light/dark mode switching.
*   **Version Control**: **Git/GitHub** for project versioning and collaboration, with **Code Rabbit** for AI-assisted code reviews on pull requests.

### **Development Process (Chapter Overview)**

The project's development is meticulously documented across multiple chapters, each building upon previous functionalities:

*   **Initial Setup**: Covered the foundational setup of a Next.js project, integrating Shadcn UI components, and establishing Git repository for version control.
*   **Database Integration**: Detailed the setup of **MongoDB** and **Prisma**, including schema definition for users and projects.
*   **Authentication**: Implemented robust user authentication using **NextAuth.js** for Google and GitHub logins, including secure middleware for route protection.
*   **UI Development**: Focused on building the landing page and the dashboard's user interface, including responsiveness and theme toggles.
*   **Project Functionality**: Developed the logic for project creation (using templates), editing, duplication, and deletion, along with displaying recent and starred projects.
*   **File System Explorer**: Constructed a dynamic and recursive file explorer, enabling real-time file and folder management (add, rename, delete) directly within the IDE.
*   **Code Editor**: Integrated and configured the **Monaco Editor**, enabling core editing features, syntax highlighting, and tracking of unsaved changes.
*   **Web Containers & Terminal**: Implemented **WebContainers** to run Node.js projects in the browser and integrated **Xterm.js** for a functional terminal, displaying installation logs and live application output.
*   **AI Integration (Ollama)**: Guided through the local installation of **Ollama** and the **Code Llama** model. Subsequent chapters focused on building an AI suggestion hook, creating API endpoints to interact with Ollama for real-time code suggestions, and developing a chat-based AI assistant UI.
*   **Code Saving and Optimization**: Implemented the functionality to save active file changes and save all open files, ensuring synchronization with WebContainers and the database. Actions were wrapped in `useCallback` for performance optimization.

### **Challenges and Insights**

*   **MongoDB Replica Set Requirement**: A significant challenge involved configuring MongoDB to run as a replica set, as required by Prisma for transactional operations, highlighting a specific database setup nuance.
*   **Complex AI Prompt Engineering**: The developer acknowledged the complexity of crafting effective AI prompts for code generation and contextual understanding, leveraging various techniques and external tools for this.
*   **Advanced React Patterns**: The project extensively uses advanced React hooks (`useEffect`, `useCallback`, `useRef`, `useImperativeHandle`) and state management with Zustand, making it a "pretty advanced project" requiring deep understanding.
*   **Real-time Debugging**: The development process openly showcases real-time debugging of issues, from UI glitches to complex AI integration problems and WebContainer initialization errors.

### **Future Enhancements and Assignments**

The developer suggested several areas for future improvement and assigned tasks:

*   **Enhanced File Explorer Icons**: Replacing generic file/folder icons with proper technology-related icons.
*   **Fix Multi-Suggestion Bug**: Addressing an issue where accepting AI suggestions might insert the code multiple times.
*   **"Close All Files" Feature**: Fully implementing the functionality to close all open files simultaneously.
*   **"Toggle Favorite" Functionality**: Completing the implementation of the project starring/favoriting feature.
*   **Real-time Estimated Setup Time**: Dynamically calculating and displaying the estimated time for project setup.
*   **Billing and Payment Features**: Future expansion could include role-based authentication to support billing or payment functionalities.

This project provides a comprehensive guide to building a modern, feature-rich web-based IDE with integrated AI, covering a wide array of web development concepts and advanced techniques.