# InsightPage-userguide
## 1. Overview

InsightPage is your intelligent browser assistant, designed to make your web experience smarter and more efficient. It acts as an AI Sidekick directly within your Chrome browser, offering features like:

*   Instant summaries of web pages.
*   Intelligent interactions: Ask questions about what you're reading, content from URLs, PDFs, or your notes.
*   Smart web search capabilities.
*   Flexible AI integration: Connect to powerful local AI models (like Ollama or LM Studio) or cloud-based services (OpenAI, Gemini).
*   And much more!

This guide will help you understand how to install, configure, and use InsightPage to its full potential.

## 3. Installation and Setup

There are two main ways to install InsightPage:

### A. Installing the Latest Release (Recommended for Most Users)

1.  **Download:** Get the latest release package (usually a `.zip` file) from the [official InsightPage releases page](https://github.com/3-ark/InsightPage-AI_Sidekick/releases).
2.  **Extract:** Unzip the downloaded file into a dedicated folder on your computer.
3.  **Enable Developer Mode in Chrome:**
    *   Open Chrome and navigate to `chrome://extensions`.
    *   In the top-right corner, toggle on "Developer mode."
4.  **Load the Extension:**
    *   Click the "Load unpacked" button that appears after enabling Developer mode.
    *   Select the folder where you extracted the InsightPage files.
5.  InsightPage should now be installed and visible in your Chrome extensions list!

### B. Installing from Source (For Developers or Advanced Users)

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/3-ark/InsightPage-AI_Sidekick.git
    ```
2.  **Navigate to Directory:**
    ```bash
    cd InsightPage
    ```
3.  **Install Dependencies and Build:**
    ```bash
    npm install && npm start
    ```
    This command will install all necessary software packages and then build the extension. The compiled extension files will be located in a folder named `dist/chrome`.
4.  **Enable Developer Mode in Chrome:** (If not already enabled)
    *   Open Chrome and navigate to `chrome://extensions`.
    *   Toggle on "Developer mode."
5.  **Load the Extension:**
    *   Click the "Load unpacked" button.
    *   Select the `dist/chrome` folder from the cloned project directory.

## InsightPage Application User Guide

Welcome to the InsightPage application! This guide will help you understand its features and how to use them effectively.

## Table of Contents

*   [Overview](#1-overview)
*   [Installation and Setup](#3-installation-and-setup)
    *   [Installing the Latest Release (Recommended for Most Users)](#a-installing-the-latest-release-recommended-for-most-users)
    *   [Installing from Source (For Developers or Advanced Users)](#b-installing-from-source-for-developers-or-advanced-users)
*   [InsightPage Application User Guide](#InsightPage-application-user-guide)
*   [Core Chat Functionality](#core-chat-functionality)
    *   [Sending a Message](#sending-a-message)
    *   [Chat Modes](#chat-modes)
    *   [Using Your Notes as Context](#using-your-notes-as-context)
    *   [Searching Chat History](#searching-chat-history)
    *   [Automatic Chat Title Generation](#automatic-chat-title-generation)
*   [Main Menu & Quick Access](#main-menu--quick-access)
*   [Note-Taking Features](#note-taking-features)
    *   [Appending Selected Text to Popover Note](#appending-selected-text-to-popover-note)
    *   [AI-Powered Note Saving (`saveNote` Tool)](#ai-powered-note-saving-savenote-tool)
    *   [AI-Powered Memory Updates (`updateMemory` Tool)](#ai-powered-memory-updates-updatememory-tool)
    *   [Searching Notes](#searching-notes)
*   [Using RAG for Smart Search & Context](#using-rag-for-smart-search--context)
    *   [1. Navigate to RAG Settings](#1-navigate-to-rag-settings)
    *   [2. Configure Your Embedding Model](#2-configure-your-embedding-model)
    *   [3. Generate Embeddings for Your Data](#3-generate-embeddings-for-your-data)
    *   [4. Keeping Your Index Up-to-Date](#4-keeping-your-index-up-to-date)
    *   [5. Query Your Data with RAG](#5-query-your-data-with-rag)
    *   [6. Quick Search from the Main Menu](#6-quick-search-from-the-main-menu)
*   [Model Management](#model-management)
    *   [Fetching and Selecting Models](#fetching-and-selecting-models)
*   [Connecting to LLM Services (API Settings)](#connecting-to-llm-services-api-settings)
*   [Advanced Model Settings](#advanced-model-settings)
    *   [Model Interaction Parameters](#model-interaction-parameters)
    *   [Model List Management (Visibility/Enabled Models)](#model-list-management-visibilityenabled-models)
*   [Context Source Settings](#context-source-settings)
    *   [Page Context Settings (for "Page Mode")](#page-context-settings-for-page-mode)
    *   [Web Search Settings (for "Web Mode")](#web-search-settings-for-web-mode)
*   [Text-to-Speech (TTS)](#text-to-speech-tts)
    *   [Enabling and Configuration](#enabling-and-configuration)
    *   [How it Works](#how-it-works)
*   [Themes & Appearance](#themes--appearance)
    *   [Predefined Themes](#predefined-themes)
    *   [Custom Theme](#custom-theme)
    *   [Appearance Toggles](#appearance-toggles)
    *   [Font Size](#font-size)
*   [Special Features](#special-features)
    *   [Automatic URL Content Scraping](#automatic-url-content-scraping)
    *   [PDF Content Extraction (in Page Mode)](#pdf-content-extraction-in-page-mode)
*   [Personas (AI Personalities) 🥷](#personas-ai-personalities-)
    *   [Selecting a Persona](#selecting-a-persona)
    *   [Managing Personas](#managing-personas)
    *   [Default Persona](#default-persona)
    *   [Example Personas and Their Focus:](#example-personas-and-their-focus)
*   [Troubleshooting](#troubleshooting)

## Core Chat Functionality

This section covers the basic chat features of the application.

### Sending a Message
To start interacting with the AI, simply type your message in the input field at the bottom of the chat panel and press Enter or click the send button.

### Chat Modes
The application offers different modes to tailor the AI's responses based on your needs:

*   **Standard Chat Mode (`chat`)**: This is the default mode. The AI will respond based on its general knowledge and the conversation history.
*   **Web Mode (`web`)**: When in this mode, the AI will first perform a web search based on your query. To provide more comprehensive answers, Web Mode goes beyond just using search snippets; it can actively visit the top few search result pages, fetch their main content, and use this deeper information as context. The application may also optimize your query behind the scenes to get better search results.
*   **Page Mode (`page`)**: In this mode, the AI will use the content of the currently active browser tab (webpage or PDF) as context for its responses. You can ask questions or request summaries about this content. Additionally, InsightPage can understand questions about text within your InsightPage notes or content from URLs you provide directly in the chat. Often, a dedicated "Summarize this page" button or command is available for quick summaries.

### Using Your Notes as Context
You can allow the AI to use the content of your popover note as additional context for its responses. Toggle the "Use Note" option in the settings. When enabled, the information in your popover note will be considered by the AI, which can be helpful for remembering preferences or specific details you'vesaved.

### Searching Chat History
If you need to find past conversations, you can use the search feature within the Chat History view:
*   **Accessing Search:** When you open the Chat History panel, you'll find a search input field at the top.
*   **What is Searched:** The search looks through:
    *   The titles of your saved chats.
    *   The content of the messages within each chat.
*   **How to Use:** Type your keywords into the search field. The list of chats will update dynamically to show only those that match your query.
*   Search is case-insensitive.
*   If no chats match your query, a "No results found" message will be displayed.
*   The search results are paginated if they span multiple pages.

### Automatic Chat Title Generation
The application automatically generates a concise title for new chats based on the initial messages. This helps you quickly identify past conversations. If a title isn't generated, or if you'd like to change it, you can typically do so manually (details may vary based on your specific version of the application).

## Main Menu & Quick Access

The application has a slide-out main menu, typically accessed from an icon in the top-left corner. This panel provides quick access to several key functions:

*   **Quick Theme Toggle:** Often a sun/moon icon, allowing you to swiftly switch between a primary light theme (e.g., "Paper") and a primary dark theme (e.g., "Dark").
*   **Persona Selection:** A dropdown menu to quickly change the active AI Persona.
*   **Model Selection:**
    *   Displays the currently selected LLM.
    *   Clicking on it often turns it into a search field where you can type to find specific models from your configured list.
    *   A dropdown will show matching models, allowing for quick selection.
*   **Navigation Links:**
    *   **Configuration:** Opens the detailed settings panel (described in subsequent sections).
    *   **Chat History:** Takes you to the view where you can browse and load past conversations.
    *   **Note System:** Opens the interface for managing your saved notes.

## Note-Taking Features

The application provides several ways to take and manage notes. These notes are particularly valuable because they can be saved and later injected as context for the AI. For example, you can save key data points in a note and then instruct InsightPage to use this specific information when answering a question, comparing information, or generating content.

### Appending Selected Text to Popover Note
You can quickly add text from web pages to your popover note:
1.  Select the text you want to save on any webpage.
2.  Right-click and choose the option to "Add to Note" (the exact wording might vary).
3.  The selected text will be appended to your current popover note. If the note is empty, the selected text will become its content. A separator is added if there's existing content.

### AI-Powered Note Saving (`saveNote` Tool)
The AI can help you create more structured notes based on your conversation:
*   **How it works**: If you ask the AI to remember something important, take a note on a specific topic, or summarize key decisions, it can use its `saveNote` tool.
*   **Features**:
    *   The AI can create a note with a specific `content`.
    *   It can assign a `title` to the note (or a default one will be generated).
    *   It can add `tags` (e.g., `["project-alpha", "meeting-summary"]`) to help categorize the note.
*   **Where are they saved?**: These notes are saved in the application's persistent note storage system, separate from the quick popover note. You can view them in the "Notes" section or a similar area in the application.

### AI-Powered Memory Updates (`updateMemory` Tool)
The AI can also remember specific pieces of information or summaries by adding them to your popover note, which acts as a persistent "memory":
*   **How it works**: If you provide the AI with a piece of information you want it (and yourself) to remember for later, like a preference, a fact about you, or a key takeaway from the current chat, it can use its `updateMemory` tool.
*   **Features**:
    *   The AI will append a `summary` of the information to your existing popover note.
    *   A timestamp is typically added to the summary (e.g., "User prefers concise answers. (on YYYY-MM-DD)").
*   **Purpose**: This helps the AI maintain context over longer interactions and allows you to easily refer back to important details you've asked it to remember.

### Searching Notes
The Note System also includes a search function to help you quickly find specific notes:
*   **Accessing Search:** In the Note System view, a search input field is available at the top.
*   **What is Searched:** The search scans through:
    *   The titles of your notes.
    *   The content of your notes.
    *   The tags associated with your notes.
*   **How to Use:** Enter your search terms in the input field. The displayed notes will filter in real-time.
*   Search is case-insensitive.
*   A "No notes found" message will appear if your query doesn't match any notes.
*   Results are paginated.
## Using RAG for Smart Search & Context

InsightPage uses a powerful Retrieval-Augmented Generation (RAG) system to search your notes and chat history. This allows you to ask questions based on your own data. The system uses a hybrid approach, combining keyword-based search (BM25) with semantic search (via embeddings) for the best results. Here's how to set it up and use it.

### 1. Navigate to RAG Settings
*   Open the main menu by clicking your persona's avatar in the top-left.
*   Click the **Settings** button to open the full configuration panel.
*   Find and expand the **RAG Settings** section.

### 2. Configure Your Embedding Model
This is the most critical step for good performance. In the "RAG Settings" panel, select an embedding model.
*   **For Local Models:** If you are using a local model (e.g., via Ollama), make sure the model is running *before* you start the embedding process.
*   **Important:** You must use the same embedding model for creating the embeddings and for querying them later.

### 3. Generate Embeddings for Your Data
InsightPage needs to process your notes and chats to create searchable embeddings. You have two modes for this, configured in "RAG Settings":
*   **Manual Mode (Default):** You control when embeddings are created. This is recommended to avoid unnecessary processing and costs (for API models).
*   **Automatic Mode:** Embeddings are automatically created or updated whenever you save a note or chat. This is more convenient but requires your embedding model to be constantly available if it's a local one.

**First-Time Setup:** Go to the main slide-out menu (click the avatar). In the "Embedding Management" section, click the **Rebuild** button. This will process all your existing notes and chats. This may take some time.

### 4. Keeping Your Index Up-to-Date
*   **BM25 (Keyword) Index:** This updates automatically as you add or change notes and chats.
*   **Embeddings (Semantic) Index:**
    *   In **Manual Mode**, you need to periodically click the **Update** button in the "Embedding Management" section of the main menu. This will process only the new or changed items, which is faster than a full rebuild.
    *   In **Automatic Mode**, this happens in the background.

### 5. Query Your Data with RAG
In the main chat input bar, type `/r` followed by your search query.
*   **Example:** `/r what were the key points from the project alpha meeting?`
*   InsightPage will search your knowledge base, find the most relevant information, and feed it to the LLM as context to answer your question.

### 6. Quick Search from the Main Menu
You can perform a quick test search directly from the main slide-out menu. Use the search bar at the top to see instant results from your notes and chats.

### A Note on Language Support
*   **Keyword Search (BM25):** Has excellent support for Latin-based languages. Cyrillic, Korean, Arabic, and Devanagari are also well-supported. Japanese performance is similar to Latin languages.
*   **Semantic Search (Embeddings):** The quality of search for any language depends entirely on the embedding model you choose. A model trained on your target language is crucial for good results.

## Model Management

The application allows you to connect to and switch between different Large Language Models (LLMs) from various providers. InsightPage offers the flexibility to choose your preferred AI engine by supporting two main types of connections, allowing you to balance power, privacy, and cost:

*   **Local Models (e.g., Ollama, LM Studio):** If you have AI models running locally on your computer, InsightPage can connect to them. This is an excellent option for users who prioritize data privacy, want to use specialized open-source models, or need offline access.
*   **Cloud Services (e.g., OpenAI, Gemini):** You can also configure InsightPage to use powerful cloud-based AI services. This option often gives you access to the latest, largest, and most capable models.

Configuration for these different AI models will typically be found in InsightPage's settings panel, detailed in the "Connecting to LLM Services (API Settings)" section.

### Fetching and Selecting Models
*   Once a provider is configured and enabled (see below), the application will attempt to fetch a list of available models from it.
*   All available models from your configured providers will be aggregated into a single list.
*   You can then select your preferred model from this list in the settings panel. The chosen model will be used for all subsequent chat interactions.
*   The list of models is periodically updated. If your currently selected model becomes unavailable, the application will attempt to select another one (usually the first in the list).

## Connecting to LLM Services (API Settings)

To use the AI, you first need to connect the application to one or more Large Language Model (LLM) providers. This is done in the "API Access" or "Connect" section of the main settings panel. For each supported service, you may need to provide an API Key or a specific Endpoint URL.

Supported services and their typical requirements include:
*   **OpenAI:** Requires an API key.
*   **Ollama:** Requires the URL of your Ollama server (e.g., `http://localhost:11434`). The app will then attempt to fetch models from this server.
*   **Groq:** Requires a Groq API key.
*   **Gemini (Google):** Requires a Gemini API key.
*   **OpenRouter:** Requires an OpenRouter API key.
*   **LM Studio:** Requires the URL of your LM Studio server (e.g., `http://localhost:1234`).
*   **Custom Endpoint:** Allows you to connect to other OpenAI-compatible APIs by providing the base URL and an optional API key.

Ensure you save your settings after entering API keys or URLs. The application will use these to fetch available models and communicate with the LLMs.

## Advanced Model Settings

Beyond just selecting a model, you can often fine-tune its behavior and manage your model list in the "Model Settings" or a similarly named section within the main settings panel.

### Model Interaction Parameters
You can adjust parameters that influence how the AI generates responses. These settings usually apply to the currently selected model or globally:

*   **Temperature:** Controls the randomness of the AI's output. Higher values (e.g., 0.8-1.0) make responses more creative and diverse but potentially less factual. Lower values (e.g., 0.2-0.5) make responses more focused, deterministic, and conservative.
*   **Max Tokens:** Sets the maximum length of the AI's response in tokens (pieces of words).
*   **Top P (Nucleus Sampling):** An alternative to temperature for controlling randomness. It considers only the most probable tokens whose cumulative probability mass exceeds a threshold 'P'.
*   **Presence Penalty:** Influences how much the AI tries to avoid repeating topics or phrases already mentioned in the conversation.

Changes to these parameters are usually saved automatically.

### Model List Management (Visibility/Enabled Models)
*   After connecting to LLM services, the application fetches a list of available models.
*   This section may allow you to:
    *   **Refresh Model List:** Manually trigger a re-fetch of models from your configured services.
    *   **Manage Model Visibility:** You might be able to hide or show specific models in the main selection dropdowns, helping you curate a shorter list of your preferred models. (The exact UI for this can vary).

## Context Source Settings

These settings control how much information from external sources (like web pages or search results) is provided to the AI.

### Page Context Settings (for "Page Mode")
Located in the "Page Context" or a similar section in settings:
*   **Content Character Limit:** You can set a limit on the number of characters extracted from a webpage when using "Page Mode." This helps manage the amount of data sent to the AI and can affect performance and cost.

### Web Search Settings (for "Web Mode")
Found in the "Web Search" or a similar section in settings:
*   **Search Results Character Limit:** You can define the maximum number of characters from web search results that will be provided to the AI as context in "Web Mode."

## Text-to-Speech (TTS)

The application can read AI messages aloud using your browser's built-in Text-to-Speech capabilities. You can manage TTS settings in the "Text-to-Speech" section of the settings panel.

### Enabling and Configuration
*   **Voice Selection**:
    *   The application will automatically load available voices from your browser.
    *   You can select your preferred voice from a dropdown list. The list usually displays the voice name and its language (e.g., "Google US English (en-US)").
    *   If no voice is pre-selected in your configuration, an English voice or the first available voice in the list will typically be chosen as the default.
    *   If no voices are available in your browser, or if they fail to load, a message will indicate this, and TTS functionality may be unavailable.
*   **Speech Rate**:
    *   You can adjust the speed at which the AI's messages are spoken using a slider.
    *   The typical range is from 0.5x (half speed) to 2.0x (double speed).
    *   The currently selected rate is displayed next to the slider.

### How it Works
*   The TTS feature uses your browser's Web Speech API. Voice availability and quality can vary between browsers and operating systems. For users seeking more natural-sounding voices, using the Microsoft Edge browser (which has its own advanced TTS capabilities) or exploring third-party Chrome extensions/APIs that integrate local TTS services (such as Piper, Kokoro-FastAPI, or Orpheus-FastAPI) might provide an enhanced audio experience.
*   When an AI message is received and TTS is active (the specific toggle/condition for TTS being active for message reading is usually found near the chat input or main settings), the `speakMessage` function is called.
*   You can typically stop ongoing speech, and some controls might offer pause/resume, though these depend on browser support and how they are implemented in the main chat interface.

## Themes & Appearance

You can customize the application's look and feel through the "Customize" section in the settings panel.

### Predefined Themes
The application comes with several built-in themes that change the color scheme:
*   **Paper**: A light, parchment-like theme.
*   **night-sepia**: A dark, soft theme.
*   **Moss**: A theme with earthy tones.
*   **Light**: A standard light mode theme.
*   **Dark**: A standard dark mode theme.

You can switch between these by selecting your desired theme.

### Custom Theme
*   You have the option to create a **Custom** theme.
*   In the "Custom Theme Colors" area, you can pick specific colors for:
    *   `bg` (Background)
    *   `text` (Main text)
    *   `active` (Active elements, accents)
    *   `bold` (Bold text)
    *   `italic` (Italic text)
    *   `link` (Hyperlinks)
    *   `mute` (Muted/secondary text)
*   Selecting a color for any of these properties will typically automatically switch you to the "Custom" theme and apply your chosen colors.
*   Your custom color choices are saved and will be reapplied when you select the "Custom" theme.

### Appearance Toggles
Within the "Customize" section, you can also find toggles for various visual elements:
*   **Create chat title**: Enable or disable automatic generation of chat titles.
*   **Background illustration**: Show or hide a background image/illustration in the chat panel.
*   **Animated background**: Enable or disable background animations.
*   **Paper texture**: Apply or remove a paper-like texture overlay, which complements themes like "Paper".

### Font Size
*   Adjust the global font size for the application using a slider.
*   The range is typically from 7px to 20px.

## Special Features

The application includes several special features to enhance its contextual understanding and capabilities.

### Automatic URL Content Scraping
*   If you include one or more URLs (e.g., `https://example.com`) directly in your message to the AI, the application will attempt to fetch the content from these web addresses.
*   This scraped content is then provided to the AI as additional context for formulating its response.
*   This is useful if you want the AI to discuss, summarize, or answer questions about specific online articles or resources without needing to be in "Web Mode".

### PDF Content Extraction (in Page Mode)
*   As mentioned in the "Page Mode" section, when you are viewing a PDF document in your browser and activate Page Mode, the application will attempt to extract the text content from the PDF.
*   This extracted text is then used as context for the AI, allowing you to ask questions about or summarize the PDF's content.

## Personas (AI Personalities) 🥷

Personas allow you to define and switch between different personalities or roles for the AI, tailoring its responses and behavior. You can manage personas in the "Persona" section of the main settings panel, and quickly select an active persona from the slide-out menu.

### Selecting a Persona
*   **From Main Settings:** In the "Persona" accordion, a dropdown menu shows all available personas. The currently selected persona's avatar is often displayed alongside.
*   **From Slide-Out Menu:** The slide-out main menu (usually accessed from the top-left) also features a dropdown to quickly switch the active persona.

The application will use the instructions and characteristics defined in the active persona's prompt to guide its responses.

### Managing Personas
Within the "Persona" section of the main settings panel:

*   **Viewing/Editing Prompt:**
    *   A text area displays the instructional prompt for the currently selected persona (e.g., "You are a witty pirate who speaks in rhymes.").
    *   You can click into this text area to edit the prompt.
*   **Saving Changes:**
    *   **Save:** If you've edited the prompt for the current persona, click "Save" to update it.
    *   **Save As...:** If you want to save your edited prompt as an entirely new persona, click "Save As...". This will open a dialog where you can give the new persona a name and optionally upload a custom avatar for it.
    *   **Cancel:** Discards any unsaved changes to the current persona's prompt.
*   **Creating a New Persona:**
    *   Click the "Add" button (usually a `+` icon) to open the "Create New Persona" dialog.
    *   **Name:** Enter a unique name for your new persona.
    *   **Avatar:** You can upload a custom image to serve as the avatar for this persona. If no avatar is uploaded, a default one may be assigned.
    *   **Prompt:** The prompt will initially be empty (if creating via "Add") or will contain the prompt you were editing (if using "Save As..."). You can define the persona's characteristics and instructions here.
    *   Click "Create" to save the new persona. It will typically become the active one.
*   **Deleting a Persona:**
    *   A "Delete" button (usually a trash can icon) allows you to remove the currently selected persona. This option is often available only if you have more than one persona.
    *   You'll be asked to confirm the deletion.
    *   If the active persona is deleted, the application will switch to another available persona (often a default one like "Ein").

### Default Persona
The application usually comes with a default persona (e.g., "Ein," a general helpful assistant) that will be used if no other persona is selected or if your chosen persona is somehow unavailable.

### Example Personas and Their Focus:
InsightPage may offer a range of personas, each designed with a slightly different style and area of expertise. Examples include:
*   **Ein:** Academic researcher - Good for in-depth analysis and factual information.
*   **Warren:** Business analyst - Focuses on business and financial contexts.
*   **Jet:** Friendly assistant - Provides general assistance with a conversational tone.
*   **Agatha:** Creative thinker - Useful for brainstorming and imaginative tasks.
*   **Jan:** Strategist - Helps with planning and strategic thinking.
*   **Sherlock:** Detective - Ideal for problem-solving and uncovering details.
*   **Spike:** All-around assistant - A versatile persona for various tasks.
You can typically switch between personas in the InsightPage settings or directly within the side panel interface.

## Troubleshooting

_(This section will be populated with common issues and solutions if any are apparent from the existing documentation or if common patterns for such extensions are known. Initially, it might contain general advice.)_

*   **Extension Not Loading:**
    *   Ensure Developer Mode is enabled in `chrome://extensions`.
    *   Double-check that you selected the correct folder (the extracted folder for release, or `dist/chrome` for source install) when clicking "Load unpacked."
*   **AI Not Responding:**
    *   Check your AI model configuration in InsightPage's settings. Ensure API keys (for cloud services) are correctly entered or that your local model server (if used) is running and accessible.
    *   If using a cloud model, verify your internet connection.
    *   Try switching to a different AI model, a different persona to see if the issue is specific to one setting.
*   **Summarization or Page Analysis Issues:**
    *   Some web pages with very complex structures, dynamic content, or paywalls might be challenging for the extension to parse perfectly.
    *   Ensure the page is fully loaded before asking InsightPage to summarize or analyze it.
*   **High Token Usage or Slow Responses:**
    *   If using a cloud service, check your usage limits and billing with the AI provider.

---
This document aims to be a comprehensive guide. If you encounter issues not covered here or have suggestions, consider reporting them via the project's GitHub issues page.
