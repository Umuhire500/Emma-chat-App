<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Emmanuel Chat App</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="app-container">
    <header class="header">
      <h1>Emmanuel Chat App</h1>
    </header>

    <div class="chat-container">
      <div class="chat-box" id="chat-box">
        <!-- Messages will appear here -->
      </div>

      <div class="message-input-container">
        <input type="text" id="message-input" placeholder="Type a message..." />
        <button id="send-btn">Send</button>
      </div>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>

/* styles.css */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.app-container {
  width: 350px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  height: 500px;
}

.header {
  background-color: #4267B2;
  color: white;
  padding: 15px;
  text-align: center;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}

.chat-container {
  display: flex;
  flex-direction: column;
  height: 100%;
  padding: 10px;
}

.chat-box {
  flex-grow: 1;
  overflow-y: auto;
  padding: 10px;
  margin-bottom: 10px;
  background-color: #e9eff1;
  border-radius: 10px;
  max-height: 300px;
}

.message-input-container {
  display: flex;
  justify-content: space-between;
}

#message-input {
  width: 80%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 14px;
}

#send-btn {
  width: 15%;
  padding: 10px;
  background-color: #4267B2;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 14px;
  cursor: pointer;
}

#send-btn:hover {
  background-color: #365899;
}

.message {
  background-color: #dcf8c6;
  padding: 8px 12px;
  margin: 5px 0;
  border-radius: 10px;
  max-width: 80%;
  word-wrap: break-word;
}

.message.user {
  background-color: #e9eff1;
  margin-left: auto;
}

// script.js

// Get references to elements
const messageInput = document.getElementById("message-input");
const sendButton = document.getElementById("send-btn");
const chatBox = document.getElementById("chat-box");

// Event listener for the send button
sendButton.addEventListener("click", function () {
  const message = messageInput.value.trim();

  if (message !== "") {
    // Add the message to the chat box
    addMessage(message, "user");

    // Clear the input field
    messageInput.value = "";

    // Auto-scroll to the bottom of the chat box
    chatBox.scrollTop = chatBox.scrollHeight;

    // Simulate a reply from Emmanuel (auto-response)
    setTimeout(() => {
      addMessage("Hello, how can I help you today?", "emmanuel");
      chatBox.scrollTop = chatBox.scrollHeight; // Scroll down after the new message
    }, 1000); // Simulated delay for response
  }
});

// Function to add a message to the chat box
function addMessage(message, sender) {
  const messageElement = document.createElement("div");
  messageElement.classList.add("message");
  messageElement.classList.add(sender);
  messageElement.textContent = message;
  chatBox.appendChild(messageElement);
}
