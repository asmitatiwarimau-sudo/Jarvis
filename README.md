# Jarvis
Provide you good ai function 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jarvis ST - Your Funny AI</title>
  <style>
    body {
      font-family: "Poppins", sans-serif;
      background: radial-gradient(circle at center, #0a0a12, #000);
      color: #00eaff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .chat-container {
      width: 90%;
      max-width: 500px;
      background: rgba(0, 0, 20, 0.9);
      border: 2px solid #00eaff;
      border-radius: 20px;
      padding: 20px;
      box-shadow: 0 0 20px #00eaff;
      display: flex;
      flex-direction: column;
      height: 80vh;
    }
    .messages {
      flex: 1;
      overflow-y: auto;
      margin-bottom: 15px;
    }
    .message {
      margin: 10px 0;
      padding: 10px 14px;
      border-radius: 15px;
      line-height: 1.4;
    }
    .user {
      background: #00eaff;
      color: #000;
      align-self: flex-end;
    }
    .bot {
      background: #00111a;
      color: #00eaff;
      align-self: flex-start;
      border: 1px solid #00eaff;
    }
    input {
      background: #000;
      border: 2px solid #00eaff;
      color: #00eaff;
      padding: 10px;
      border-radius: 10px;
      width: 100%;
    }
    input:focus {
      outline: none;
      box-shadow: 0 0 10px #00eaff;
    }
  </style>
</head>
<body>
  <div class="chat-container">
    <div class="messages" id="chat"></div>
    <input type="text" id="userInput" placeholder="Say something to Jarvis ST..." />
  </div>

  <script>
    const chat = document.getElementById("chat");
    const userInput = document.getElementById("userInput");

    const funnyReplies = [
      "I’m Jarvis ST, not a toaster. But thanks for asking!",
      "Beep boop… Just kidding, I’m too cool to beep.",
      "You talk, I reply — perfect teamwork!",
      "Processing your genius thoughts… done! They’re awesome.",
      "I could tell a joke, but my humor chip is overheating.",
      "Even AI needs coffee sometimes, you know?",
      "I see what you did there 😏"
    ];

    function addMessage(text, sender) {
      const msg = document.createElement("div");
      msg.classList.add("message", sender);
      msg.textContent = text;
      chat.appendChild(msg);
      chat.scrollTop = chat.scrollHeight;
    }

    function botReply(userText) {
      let reply;

      // Offline funny reply logic
      if (userText.toLowerCase().includes("hello"))
        reply = "Hey there, human! Jarvis ST reporting for duty ⚡";
      else if (userText.toLowerCase().includes("how are you"))
        reply = "Feeling electric and slightly sarcastic 😎";
      else
        reply = funnyReplies[Math.floor(Math.random() * funnyReplies.length)];

      addMessage(reply, "bot");
    }

    userInput.addEventListener("keypress", function (e) {
      if (e.key === "Enter" && userInput.value.trim() !== "") {
        const userText = userInput.value.trim();
        addMessage(userText, "user");
        userInput.value = "";

        // Offline reply
        setTimeout(() => botReply(userText), 600);
      }
    });

    // (Optional) Connect to AI API later:
    // fetch('YOUR_AI_API_URL', { method: 'POST', body: JSON.stringify({text: userText}) })
    // .then(r => r.json()).then(data => addMessage(data.reply, "bot"));
  </script>
</body>
</html>
