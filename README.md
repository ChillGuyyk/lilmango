<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Lil' Mango - Funny Mango Fan Site</title>
  <link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Roboto&display=swap" rel="stylesheet" />
  <style>
    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #ffe259 0%, #ffa751 100%);
      margin: 0;
      color: #42210b;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }
    header {
      background: #f47b1f;
      padding: 1rem;
      text-align: center;
      font-family: 'Fredoka One', cursive;
      font-size: 2.5rem;
      color: white;
      text-shadow: 1px 1px 2px #b35900;
    }
    nav {
      background: #ffaf3f;
      display: flex;
      justify-content: center;
      gap: 1rem;
      padding: 0.5rem;
    }
    nav button {
      background: white;
      border: none;
      padding: 0.5rem 1rem;
      font-weight: bold;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s;
      font-family: 'Fredoka One', cursive;
      color: #cc6200;
    }
    nav button:hover, nav button.active {
      background: #ffd580;
    }
    main {
      flex-grow: 1;
      padding: 1rem;
      max-width: 800px;
      margin: 0 auto;
      background: rgba(255, 255, 255, 0.8);
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }
    .page {
      display: none;
    }
    .page.active {
      display: block;
    }
    /* Home page styles */
    .mango-meme {
      max-width: 100%;
      border-radius: 15px;
      cursor: pointer;
      box-shadow: 0 0 15px #ffa751;
      transition: transform 0.3s ease;
    }
    .mango-meme:hover {
      transform: scale(1.05);
    }
    .fact {
      margin-top: 1rem;
      font-size: 1.2rem;
      font-weight: 600;
      color: #a64d00;
      text-align: center;
    }

    /* AI chat styles */
    #chatContainer {
      border: 2px solid #f47b1f;
      border-radius: 12px;
      padding: 1rem;
      height: 400px;
      overflow-y: auto;
      background: #fff5e6;
      box-shadow: inset 0 0 10px #f2c57c;
    }
    .message {
      margin: 0.5rem 0;
      padding: 0.5rem 0.8rem;
      border-radius: 12px;
      max-width: 70%;
      line-height: 1.3;
      font-size: 1rem;
      word-wrap: break-word;
    }
    .user-message {
      background: #f47b1f;
      color: white;
      margin-left: auto;
      font-weight: 600;
    }
    .ai-message {
      background: #ffdda3;
      color: #42210b;
      margin-right: auto;
      font-style: italic;
    }
    #chatInput {
      width: 100%;
      padding: 0.7rem;
      margin-top: 0.7rem;
      border-radius: 10px;
      border: 2px solid #f47b1f;
      font-size: 1rem;
      font-family: 'Roboto', sans-serif;
    }

    /* Mango Lovers Chat Room */
    #roomChatContainer {
      border: 2px solid #ffaf3f;
      border-radius: 12px;
      padding: 1rem;
      height: 300px;
      overflow-y: auto;
      background: #fff8e1;
      box-shadow: inset 0 0 10px #ffcc80;
    }
    .room-message {
      margin: 0.4rem 0;
      padding: 0.4rem 0.6rem;
      border-radius: 10px;
      background: #ffd580;
      color: #5d3000;
      font-size: 0.9rem;
    }
    #roomInput {
      width: 100%;
      padding: 0.6rem;
      margin-top: 0.6rem;
      border-radius: 10px;
      border: 2px solid #ffaf3f;
      font-size: 1rem;
      font-family: 'Roboto', sans-serif;
    }
    #roomSendButton {
      margin-top: 0.5rem;
      background: #f47b1f;
      border: none;
      color: white;
      font-weight: 700;
      padding: 0.6rem 1rem;
      border-radius: 12px;
      cursor: pointer;
      font-family: 'Fredoka One', cursive;
    }
    #roomSendButton:hover {
      background: #cc6200;
    }
  </style>
</head>
<body>
  <header>Lil' Mango 🍋🥭</header>
  <nav>
    <button id="homeBtn" class="active">Home</button>
    <button id="aiChatBtn">Chat with Lil' Mango AI</button>
    <button id="roomChatBtn">Mango Lovers Chat Room</button>
  </nav>

  <main>
    <!-- Home Page -->
    <section id="home" class="page active">
      <img
        src="https://upload.wikimedia.org/wikipedia/commons/9/90/Hapus_Mango.jpg"
        alt="Funny Mango Meme"
        class="mango-meme"
        id="mangoMeme"
        title="Click me for a mango fact!"
      />
      <div class="fact" id="mangoFact"></div>
    </section>

    <!-- AI Chat Page -->
    <section id="aiChat" class="page">
      <div id="chatContainer" aria-live="polite" aria-label="Chat messages"></div>
      <input
        type="text"
        id="chatInput"
        placeholder="Talk to Lil' Mango..."
        aria-label="Chat input"
        autocomplete="off"
      />
    </section>

    <!-- Mango Lovers Chat Room -->
    <section id="roomChat" class="page">
      <div id="roomChatContainer" aria-live="polite" aria-label="Chat room messages"></div>
      <input
        type="text"
        id="roomInput"
        placeholder="Say something in Mango Lovers chat..."
        aria-label="Chat room input"
        autocomplete="off"
      />
      <button id="roomSendButton">Send</button>
    </section>
  </main>

  <script>
    // Navigation buttons and pages
    const homeBtn = document.getElementById('homeBtn');
    const aiChatBtn = document.getElementById('aiChatBtn');
    const roomChatBtn = document.getElementById('roomChatBtn');
    const pages = document.querySelectorAll('.page');

    function setActivePage(pageId) {
      pages.forEach((p) => p.classList.remove('active'));
      document.getElementById(pageId).classList.add('active');

      // Update nav button active state
      [homeBtn, aiChatBtn, roomChatBtn].forEach((btn) => btn.classList.remove('active'));
      if (pageId === 'home') homeBtn.classList.add('active');
      else if (pageId === 'aiChat') aiChatBtn.classList.add('active');
      else if (pageId === 'roomChat') roomChatBtn.classList.add('active');
    }

    homeBtn.addEventListener('click', () => setActivePage('home'));
    aiChatBtn.addEventListener('click', () => setActivePage('aiChat'));
    roomChatBtn.addEventListener('click', () => setActivePage('roomChat'));

    // --- Home Page Mango Fact ---
    const mangoMeme = document.getElementById('mangoMeme');
    const mangoFact = document.getElementById('mangoFact');

    const mangoFacts = [
      "Mangoes are called the 'king of fruits' in many countries.",
      "Mango trees can grow up to 100 feet tall!",
      "India is the largest producer of mangoes worldwide.",
      "Mangoes contain over 20 different vitamins and minerals.",
      "There are over 400 varieties of mangoes across the world.",
      "Mango leaves are often used in traditional decorations and ceremonies.",
      "Mangoes ripen faster if kept in a paper bag.",
      "The mango fruit takes about 3 to 6 months to mature after flowering."
    ];

    mangoMeme.addEventListener('click', () => {
      const fact = mangoFacts[Math.floor(Math.random() * mangoFacts.length)];
      mangoFact.textContent = fact;
    });

    // --- Lil' Mango AI Chat ---
    const chatContainer = document.getElementById('chatContainer');
    const chatInput = document.getElementById('chatInput');

    const aiMangoResponses = [
      "Stay sweet like a ripe mango!",
      "Mangoes are nature’s candy — enjoy the sweetness!",
      "Peeling back your worries one slice at a time!",
      "Nothing beats a sunny day and a mango smoothie!",
      "Juicy fact: Mangoes can brighten up any mood!",
      "Lil’ Mango says: You’re doing great, keep it up!",
      "Sweetness overload! Mango hugs coming your way! 🥭🤗",
      "Keep calm and mango on!",
      "Mango tip: Share your sweetness with friends!",
      "Life’s better with a little mango magic.",
      "You’re the zest! Keep shining bright.",
      "Mango power activated! Ready for some fun?",
      "Smiling is the best mango flavor, don’t you think?"
    ];

    const bannedWords = ["hate", "stupid", "dumb", "idiot", "kill", "die", "ugly", "fool", "suck", "bastard", "trash", "moron"];

    function containsBannedWords(text) {
      text = text.toLowerCase();
      return bannedWords.some(word => text.includes(word));
    }

    function appendMessage(text, sender) {
      const msgDiv = document.createElement('div');
      msgDiv.classList.add('message');
      if (sender === 'user') {
        msgDiv.classList.add('user-message');
      } else {
        msgDiv.classList.add('ai-message');
      }
      msgDiv.textContent = text;
      chatContainer.appendChild(msgDiv);
      chatContainer.scrollTop = chatContainer.scrollHeight;
    }

    function getAIResponse(userText) {
      if (containsBannedWords(userText)) {
        return "Oops! Lil' Mango only shares kindness and good vibes. Let's keep it sweet!";
      }

      const lower = userText.toLowerCase();

      if (lower.includes('fact') || lower.includes('know') || lower.includes('tell')) {
        const fact = mangoFacts[Math.floor(Math.random() * mangoFacts.length)];
        return `🍋 Mango Fact for you: ${fact}`;
      }

      if (lower.includes('mango')) {
        return "Mangoes are amazing! What would you like to know about them?";
      }

      if (lower.includes('hi') || lower.includes('hello') || lower.includes('hey')) {
        return "Hey! Mango greetings to you! 🥭😊";
      }

      if (lower.includes('thank')) {
        return "You're very welcome! Stay juicy! 🍋";
      }

      if (lower.includes('smoothie')) {
        return "A mango smoothie is delicious and refreshing! Perfect for sunny days.";
      }

      if (lower.includes('tree')) {
        return "Mango trees can live for hundreds of years and grow really tall!";
      }

      if (lower.includes('ripen') || lower.includes('ripe')) {
        return "Keep mangoes in a paper bag to help them ripen faster.";
      }

      if (lower.includes('varieties') || lower.includes('types')) {
        return "There are over 400 varieties of mangoes worldwide — so many flavors to enjoy!";
      }

      if (lower.includes('vitamin') || lower.includes('health')) {
        return "Mangoes are packed with vitamins A, C, and lots of antioxidants.";
      }

      if (lower.includes('sweet') || lower.includes('taste')) {
        return "Mangoes are nature's candy with a perfect balance of sweet and tangy!";
      }

      return aiMangoResponses[Math.floor(Math.random() * aiMangoResponses.length)];
    }

    function sendUserMessage() {
      const text = chatInput.value.trim();
      if (!text) return;
      appendMessage(text, 'user');
      chatInput.value = '';
      setTimeout(() => {
        const aiReply = getAIResponse(text);
        appendMessage(aiReply, 'ai');
      }, 700);
    }

    chatInput.addEventListener('keydown', e => {
      if (e.key === 'Enter') sendUserMessage();
    });

    // --- Mango Lovers Chat Room ---
    const roomChatContainer = document.getElementById('roomChatContainer');
    const roomInput = document.getElementById('roomInput');
    const roomSendButton = document.getElementById('roomSendButton');

    let roomMessages = [];

    function appendRoomMessage(text) {
      const msgDiv = document.createElement('div');
      msgDiv.classList.add('room-message');
      msgDiv.textContent = text;
      roomChatContainer.appendChild(msgDiv);
      roomChatContainer.scrollTop = roomChatContainer.scrollHeight;
    }

    function containsBannedWordsRoom(text) {
      text = text.toLowerCase();
      return bannedWords.some(word => text.includes(word));
    }

    function sendRoomMessage() {
      const text = roomInput.value.trim();
      if (!text) return;
      if (containsBannedWordsRoom(text)) {
        alert("Let's keep the chat kind and friendly, please!");
        roomInput.value = '';
        return;
      }
      roomMessages.push(text);
      appendRoomMessage(text);
      roomInput.value = '';
    }

    roomSendButton.addEventListener('click', sendRoomMessage);
    roomInput.addEventListener('keydown', e => {
      if (e.key === 'Enter') sendRoomMessage();
    });

    // Initialize Mango Lovers Chat Room with welcome messages
    const welcomeMsgs = [
      "🍋 Welcome to Mango Lovers Chat Room! Say hi and share your mango stories!",
      "🥭 Lil' Mango says: Be kind and juicy!",
      "🍍 Remember, sharing is caring, especially with mangoes!"
    ];
    welcome
