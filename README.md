# 📬 ReplyMate – Smart AI Gmail Reply Assistant

**ReplyMate** is a Chrome extension that integrates with Gmail and enables users to generate context-aware email replies using AI. It supports tone customization (Formal, Neutral, Informal) and injects the response directly into the Gmail reply box.

---

## 🔧 Tech Stack

| Layer      | Technology                    |
|------------|-------------------------------|
| Frontend   | React , Chrome Extension APIs |
| Backend    | Spring Boot (Java), REST API  |
| AI Model   | GEMINI-AI                     |
| Communication | REST API (`fetch`)         |

---

## 🛠️ Features

- 🧠 Generate AI replies based on email context
- 🌐 Automatically responds in the same language as the original email
- 🎭 Choose reply tone: Formal, Neutral, or Informal
- 💬 Injects smart replies directly into Gmail’s compose box
- 🖱️ Seamless Chrome extension experience
- 🔁 Handles multiple generate-clicks cleanly (overwrites previous response)


---

## ⚙️ Project Structure & Workflow

### 1. **Frontend – Chrome Extension**
- Injects a custom **"ReplyMate"** button and a **tone selector dropdown** into Gmail’s reply toolbar using a content script.
- When the user clicks "ReplyMate":
  - Extracts the latest email content from Gmail using DOM selectors.
  - Sends a `POST` request to the backend API with:
    - Email content
    - Selected tone

### 2. **Backend – Spring Boot API**
- Receives the email content and tone via `POST /api/email/generate`
- Processes the request using an AI model (e.g., OpenAI or other LLM)
- Generates a contextually appropriate reply in the selected tone
- Returns the generated reply as plain text

### 3. **Frontend – DOM Injection**
- On successful response:
  - Clears any existing text in the Gmail compose box
  - Injects the generated reply directly
  - Sets the focus in the compose box for editing or sending

---

## 🧪 Local Development

### 🔌 Backend Setup

1. Clone the backend repository:
    ```bash
    git clone https://github.com/your-username/replymate-backend.git
    cd replymate-backend
    ```
2. Configure API keys (if needed, e.g. OpenAI) in `application.properties`
3. Run the Spring Boot server:
    ```bash
    ./mvnw spring-boot:run
    ```
    Backend should run on: `http://localhost:8080`

### 🌐 Frontend / Chrome Extension Setup

1. Open `chrome://extensions/` in Chrome
2. Enable **Developer Mode**
3. Click **Load Unpacked** and select the folder containing the extension code (with `manifest.json`)
4. Open Gmail → click **Reply** → See **“ReplyMate”** button

---

## 🔁 API Specification

### `POST /api/email/generate`

| Field        | Type   | Description                |
|--------------|--------|----------------------------|
| `emailContent` | String | Raw email text            |
| `tone`         | String | formal / neutral / informal |

**Response:** Plain text email reply string

---

## 🖼️ Screenshots
<img width="1638" height="858" alt="1" src="https://github.com/user-attachments/assets/c681e054-815a-4fc5-8323-d40ff91624d6" />
<img width="1641" height="887" alt="2" src="https://github.com/user-attachments/assets/76c45084-623d-459c-84fe-c212585f28ec" />
<img width="1506" height="535" alt="3" src="https://github.com/user-attachments/assets/4bac758b-5ef8-472e-8c87-9293d8771141" />
<img width="708" height="612" alt="4" src="https://github.com/user-attachments/assets/be749555-c314-4bff-bf83-5dcee93d82fc" />
<img width="1641" height="902" alt="5" src="https://github.com/user-attachments/assets/a89e2f75-3985-4e1f-8936-d7a67bedc274" />
<img width="1638" height="857" alt="6" src="https://github.com/user-attachments/assets/5b5329bf-309f-4e28-a0e5-ab46c7eebaf0" />
<img width="1526" height="543" alt="7" src="https://github.com/user-attachments/assets/fb911e52-8ba7-4063-a2bb-052ea1ab31b5" />

---

## 🚀 Future Improvements

- 🧪 Add spoof-proof authentication for AI response
- 🧠 Fine-tune replies based on email threads
- 💾 Store previous reply logs

---

## 🙋‍♂️ Author

**Faaeiz Khan**  


