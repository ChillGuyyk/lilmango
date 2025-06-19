<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Lil' Mango Fan Site 🍋🥭</title>
  <style/* Background gradient animation */
@keyframes mangoGradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
body {
  background: linear-gradient(-45deg, #ffb347, #ffcc5c, #ffe066, #ffb347);
  background-size: 400% 400%;
  animation: mangoGradient 15s ease infinite;
}

/* Floating mango emoji */
.floating-mango {
  position: fixed;
  font-size: 3rem;
  animation: floatMango 6s ease-in-out infinite;
  user-select: none;
  pointer-events: none;
  z-index: 1000;
}
@keyframes floatMango {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}

/* Cool button hover */
#send-button:hover {
  animation: bounce 0.4s;
  background: #ff3a2d;
}
@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}

/* Fancy font for headers */
header, nav a {
  font-family: 'Luckiest Guy', cursive;
  text-shadow: 1px 1px 0 #fff5cc;
}

/* Chat bubbles style */
.message {
  box-shadow: 0 2px 5px rgba(0,0,0,0.15);
  border-radius: 25px;
  font-weight: 600;
}>
    body {
      margin: 0; padding: 0;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: #ffe066;
      color: #664d03;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }
    header {
      background: #ffb347;
      padding: 20px;
      text-align: center;
      font-size: 2rem;
      font-weight: bold;
      box-shadow: 0 3px 6px rgba(0,0,0,0.1);
    }
    nav {
      background: #ffcc5c;
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 10px 0;
      font-weight: bold;
    }
    nav a {
      color: #664d03;
      text-decoration: none;
      font-size: 1.2rem;
      transition: color 0.3s;
    }
    nav a:hover {
      color: #ff6f61;
    }
    main {
      flex-grow: 1;
      padding: 20px;
      max-width: 800px;
      margin: 0 auto;
    }
    footer {
      background: #ffb347;
      text-align: center;
      padding: 10px;
      font-size: 0.9rem;
      color: #664d03;
      box-shadow: 0 -3px 6px rgba(0,0,0,0.1);
    }
    /* Chat page styles */
    #chat-container {
      display: flex;
      flex-direction: column;
      height: 70vh;
      border: 3px solid #ff6f61;
      border-radius: 10px;
      padding: 10px;
      background: #fff5cc;
      box-shadow: inset 0 0 10px #ffcc5c;
    }
    #messages {
      flex-grow: 1;
      overflow-y: auto;
      padding: 10px;
      border-bottom: 3px solid #ff6f61;
    }
    .message {
      margin: 10px 0;
      padding: 10px;
      border-radius: 15px;
      max-width: 70%;
      clear: both;
    }
    .user-message {
      background: #ffcc5c;
      align-self: flex-end;
      float: right;
    }
    .ai-message {
      background: #ffe066;
      align-self: flex-start;
      float: left;
    }
    #chat-input-container {
      margin-top: 10px;
      display: flex;
      gap: 10px;
    }
    #chat-input {
      flex-grow: 1;
      padding: 10px;
      font-size: 1rem;
      border: 2px solid #ff6f61;
      border-radius: 15px;
      outline: none;
    }
    #send-button {
      background: #ff6f61;
      border: none;
      color: white;
      font-weight: bold;
      padding: 0 20px;
      font-size: 1rem;
      border-radius: 15px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    #send-button:hover {
      background: #ff4a3c;
    }
  </style>
</head>
<body>
  <header>
    Lil' Mango Fan Site 🥭🍋
  </header>
  <nav>
    <a href="#" id="home-link">Home</a>
    <a href="#" id="chat-link">Chat with Lil' Mango</a>
  </nav>
  <main>
    <section id="home-section">
      <h1>Welcome to Lil' Mango!</h1>
      <p>The funniest mango fan site on the web.</p>
      <img src="https://i.imgur.com/WQZexNC.png" alt="Funny Mango Meme" style="max-width:100%; border-radius: 15px; box-shadow: 0 0 10px #ff6f61;" />
      <p>Chat with Lil' Mango and see if you can stump the mango AI 🍋🥭</p>
    </section>

    <section id="chat-section" style="display:none;">
      <div id="chat-container">
        <div id="messages"></div>
        <div id="chat-input-container">
          <input type="text" id="chat-input" placeholder="Say something to Lil' Mango..." />
          <button id="send-button">Send</button>
        </div>
      </div>
    </section>
  </main>
  <footer>
    Made with mango love 🍋🥭 by ChillGuyyk
  </footer>

  <script>
    const homeLink = document.getElementById('home-link');
    const chatLink = document.getElementById('chat-link');
    const homeSection = document.getElementById('home-section');
    const chatSection = document.getElementById('chat-section');

    homeLink.addEventListener('click', (e) => {
      e.preventDefault();
      homeSection.style.display = 'block';
      chatSection.style.display = 'none';
    });

    chatLink.addEventListener('click', (e) => {
      e.preventDefault();
      homeSection.style.display = 'none';
      chatSection.style.display = 'block';
      document.getElementById('chat-input').focus();
    });

    const messagesDiv = document.getElementById('messages');
    const chatInput = document.getElementById('chat-input');
    const sendButton = document.getElementById('send-button');

    function addMessage(text, sender) {
      const msgDiv = document.createElement('div');
      msgDiv.textContent = text;
      msgDiv.classList.add('message');
      if(sender === 'user') msgDiv.classList.add('user-message');
      else msgDiv.classList.add('ai-message');
      messagesDiv.appendChild(msgDiv);
      messagesDiv.scrollTop = messagesDiv.scrollHeight;
    }

    function getAiResponse(userText) {
      // Simple silly AI responses
      const lower = userText.toLowerCase();
      if(lower.includes('hello') || lower.includes('hi')) return "Hey there! Lil' Mango here 🍋🥭!";
      if(lower.includes('mango')) return "Mangoes are the king of fruits, obviously!";
      if(lower.includes('joke')) return "Why did the mango go to the party? Because it was the *peel* of the town!";
      if(lower.includes('bye')) return "See you later, juicy friend!";
      return "I'm Lil' Mango, I don't know everything, but I do know mangoes!";
    }

    sendButton.addEventListener('click', () => {
      const userText = chatInput.value.trim();
      if(!userText) return;
      addMessage(userText, 'user');
      chatInput.value = '';
      setTimeout(() => {
        const aiReply = getAiResponse(userText);
        addMessage(aiReply, 'ai');
      }, 700);
    });

    chatInput.addEventListener('keydown', (e) => {
      if(e.key === 'Enter') sendButton.click();
    });
  </script>
</body>
</html>
