<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Lil' Mango - The Ultimate Mango Fan Site 🥭🍋</title>

  <link href="https://fonts.googleapis.com/css2?family=Luckiest+Guy&family=Open+Sans&display=swap" rel="stylesheet" />

  <style>
    /* Reset */
    * {
      box-sizing: border-box;
    }
    body {
      margin: 0;
      font-family: 'Open Sans', sans-serif;
      background: linear-gradient(135deg, #fff1b8, #ffb347);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      color: #663300;
    }
    header {
      background: #ff931e;
      padding: 1.5rem 2rem;
      font-family: 'Luckiest Guy', cursive;
      font-size: 2.8rem;
      color: white;
      text-align: center;
      text-shadow: 1px 1px 5px rgba(0,0,0,0.3);
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
      user-select: none;
    }
    nav {
      background: #ffa500cc;
      display: flex;
      justify-content: center;
      gap: 2rem;
      padding: 0.8rem 0;
      font-family: 'Luckiest Guy', cursive;
      font-size: 1.3rem;
      box-shadow: inset 0 -3px 5px rgba(0,0,0,0.1);
      user-select: none;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      padding: 0.25rem 0.75rem;
      border-radius: 30px;
      transition: background-color 0.3s ease, color 0.3s ease;
      cursor: pointer;
    }
    nav a:hover,
    nav a.active {
      background: #ff6f00;
      color: #fffddb;
      box-shadow: 0 0 12px #ff6f00cc;
    }
    main {
      flex-grow: 1;
      max-width: 900px;
      margin: 2rem auto 3rem;
      background: #fff7d1;
      border-radius: 20px;
      box-shadow: 0 6px 20px rgba(255,165,0,0.4);
      padding: 2rem 2.5rem;
      user-select: text;
    }
    section {
      display: none;
    }
    section.active {
      display: block;
    }

    /* Home page */
    #home-section h1 {
      font-family: 'Luckiest Guy', cursive;
      font-size: 3rem;
      margin-bottom: 0.3rem;
      color: #ff6f00;
      text-align: center;
      user-select: none;
    }
    #home-section p {
      font-size: 1.15rem;
      line-height: 1.5;
      max-width: 600px;
      margin: 1rem auto 2rem;
      text-align: center;
      color: #663300;
    }
    #home-meme {
      display: block;
      margin: 0 auto;
      max-width: 320px;
      border-radius: 15px;
      box-shadow: 0 0 20px #ff8c00aa;
      user-select: none;
      transition: transform 0.3s ease;
      cursor: pointer;
    }
    #home-meme:hover {
      transform: scale(1.05) rotate(-3deg);
      box-shadow: 0 0 35px #ff6f00cc;
    }

    /* Chat with Lil Mango */
    #chat-section {
      display: flex;
      flex-direction: column;
      height: 65vh;
      max-height: 600px;
    }
    #chat-container {
      flex-grow: 1;
      background: #fff3b0;
      border-radius: 15px;
      padding: 1rem;
      box-shadow: inset 0 0 15px #ffb347cc;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
    }
    .message {
      max-width: 70%;
      margin: 0.5rem 0;
      padding: 10px 16px;
      border-radius: 20px;
      font-weight: 600;
      box-shadow: 0 2px 7px rgba(0,0,0,0.1);
      line-height: 1.3;
      user-select: text;
      word-wrap: break-word;
    }
    .user-message {
      background: #ffcc5c;
      align-self: flex-end;
      border-bottom-right-radius: 2px;
      color: #663300;
      animation: slideInRight 0.3s ease;
    }
    .ai-message {
      background: #ffe066;
      align-self: flex-start;
      border-bottom-left-radius: 2px;
      color: #663300;
      animation: slideInLeft 0.3s ease;
    }
    @keyframes slideInRight {
      from { transform: translateX(50px); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
    @keyframes slideInLeft {
      from { transform: translateX(-50px); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
    #chat-input-container {
      display: flex;
      margin-top: 10px;
      gap: 10px;
    }
    #chat-input {
      flex-grow: 1;
      padding: 12px 18px;
      font-size: 1rem;
      border-radius: 25px;
      border: 3px solid #ff931e;
      outline: none;
      transition: border-color 0.3s ease;
    }
    #chat-input:focus {
      border-color: #ff6f00;
      box-shadow: 0 0 10px #ff6f00cc;
    }
    #send-button {
      background: #ff6f00;
      border: none;
      color: white;
      font-weight: 700;
      font-size: 1.1rem;
      padding: 0 25px;
      border-radius: 25px;
      cursor: pointer;
      user-select: none;
      transition: background-color 0.3s ease;
      box-shadow: 0 4px 8px #ff6f00bb;
    }
    #send-button:hover {
      background: #e65c00;
      box-shadow: 0 6px 14px #e65c00cc;
      animation: bounce 0.3s;
    }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-6px); }
    }

    /* Mango Lovers Chat room */
    #room-section {
      display: flex;
      flex-direction: column;
      height: 65vh;
      max-height: 600px;
    }
    #room-chat-container {
      flex-grow: 1;
      background: #fff3b0;
      border-radius: 15px;
      padding: 1rem;
      box-shadow: inset 0 0 15px #ffb347cc;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      margin-bottom: 12px;
    }
    .room-message {
      max-width: 80%;
      margin: 0.4rem 0;
      padding: 10px 18px;
      border-radius: 20px;
      font-weight: 600;
      background: #ffcc5c;
      color: #663300;
      box-shadow: 0 1px 5px rgba(0,0,0,0.1);
      word-wrap: break-word;
      user-select: text;
      animation: fadeInMessage 0.3s ease;
    }
    @keyframes fadeInMessage {
      from { opacity: 0; transform: translateY(15px); }
      to { opacity: 1; transform: translateY(0); }
    }
    #room-input-container {
      display: flex;
      gap: 10px;
    }
    #room-input {
      flex-grow: 1;
      padding: 12px 18px;
      font-size: 1rem;
      border-radius: 25px;
      border: 3px solid #ff931e;
      outline: none;
      transition: border-color 0.3s ease;
    }
    #room-input:focus {
      border-color: #ff6f00;
      box-shadow: 0 0 10px #ff6f00cc;
    }
    #room-send-button {
      background: #ff6f00;
      border: none;
      color: white;
      font-weight: 700;
      font-size: 1.1rem;
      padding: 0 25px;
      border-radius: 25px;
      cursor: pointer;
      user-select: none;
      transition: background-color 0.3s ease;
      box-shadow: 0 4px 8px #ff6f00bb;
    }
    #room-send-button:hover {
      background: #e65c00;
      box-shadow: 0 6px 14px #e65c00cc;
      animation: bounce 0.3s;
    }

    /* Footer */
    footer {
      text-align: center;
      padding: 1rem 1rem;
      background: #ff931e;
      color: white;
      font-family: 'Luckiest Guy', cursive;
      box-shadow: 0 -3px 8px rgba(0,0,0,0.15);
      user-select: none;
      font-size: 1.1rem;
    }

    /* Responsive */
    @media (max-width: 600px) {
      main {
        margin: 1rem 1rem 2rem;
        padding: 1.5rem 1.8rem;
      }
      nav {
        gap: 1rem;
        font-size: 1.1rem;
      }
      #home-section h1 {
        font-size: 2.2rem;
      }
      #chat-section, #room-section {
        height: 55vh;
        max-height: none;
      }
    }

  </style>
</head>
<body>

  <header>Lil' Mango 🥭</header>

  <nav>
    <a href="#" id="nav-home" class="active">Home</a>
    <a href="#" id="nav-chat">Chat with Lil' Mango AI</a>
    <a href="#" id="nav-room">Mango Lovers Chat Room</a>
  </nav>

  <main>
    <!-- Home Section -->
    <section id="home-section" class="active">
      <h1>Welcome to Lil' Mango!</h1>
      <p>Your ultimate place to celebrate all things mango. Whether you love mango memes, juicy facts, or chatting with fellow mango lovers — you’re in the right spot.</p>
      <img id="home-meme" src="https://i.imgur.com/7P7Tp7r.png" alt="Funny Mango Meme" title="Click me for mango wisdom!" />
      <p style="text-align:center; font-style: italic; color: #cc6600; user-select:none;">Click the mango meme for a surprise mango fact!</p>
    </section>

    <!-- Chat with Lil Mango AI Section -->
    <section id="chat-section">
      <div id="chat-container" aria-live="polite" aria-label="Chat messages with Lil Mango AI"></div>
      <div id="chat-input-container">
        <input type="text" id="chat-input" placeholder="Ask Lil' Mango anything..." aria-label="Type your message to Lil Mango" />
        <button id="send-button" aria-label="Send message">Send</button>
      </div>
    </section>

    <!-- Mango Lovers Chat Room Section -->
    <section id="room-section">
      <div id="room-chat-container" aria-live="polite" aria-label="Mango Lovers chat room messages"></div>
      <div id="room-input-container">
        <input type="text" id="room-input" placeholder="Say something to fellow mango lovers..." aria-label="Type your chat message" />
        <button id="room-send-button" aria-label="Send chat message">Send</button>
      </div>
    </section>
  </main>

  <footer>© 2025 Lil' Mango Fan Club — Stay Juicy! 🥭</footer>

  <// --- Lil' Mango AI Chat ---
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

const mangoResponses = [
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

  // Keyword-based responses:
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

  // If no keyword matched, fallback to a random positive mango phrase:
  return mangoResponses[Math.floor(Math.random() * mangoResponses.length)];
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
>
    // --- NAVIGATION ---
    const navHome = document.getElementById('nav-home');
    const navChat = document.getElementById('nav-chat');
    const navRoom = document.getElementById('nav-room');

    const homeSection = document.getElementById('home-section');
    const chatSection = document.getElementById('chat-section');
    const roomSection = document.getElementById('room-section');

    function setActiveSection(section) {
      // Hide all
      homeSection.classList.remove('active');
      chatSection.classList.remove('active');
      roomSection.classList.remove('active');

      navHome.classList.remove('active');
      navChat.classList.remove('active');
      navRoom.classList.remove('active');

      // Show selected
      section.classList.add('active');
      if (section === homeSection) navHome.classList.add('active');
      else if (section === chatSection) navChat.classList.add('active');
      else if (section === roomSection) navRoom.classList.add('active');
    }

    navHome.addEventListener('click', e => {
      e.preventDefault();
      setActiveSection(homeSection);
    });
    navChat.addEventListener('click', e => {
      e.preventDefault();
      setActiveSection(chatSection);
      chatInput.focus();
    });
    navRoom.addEventListener('click', e => {
      e.preventDefault();
      setActiveSection(roomSection);
      roomInput.focus();
    });


    // --- HOME MANGO MEME CLICK for fun fact ---
    const homeMeme = document.getElementById('home-meme');
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
    homeMeme.addEventListener('click', () => {
      const fact = mangoFacts[Math.floor(Math.random() * mangoFacts.length)];
      alert("🍋 Mango Fact: " + fact);
    });


    // --- Lil' Mango AI Chat ---
    const chatContainer = document.getElementById('chat-container');
    const chatInput = document.getElementById('chat-input');
    const sendButton = document.getElementById('send-button');

    // AI mango responses - positive, fun, no meanness allowed
    const mangoResponses = [
      "Hey there, mango lover! What's juicy with you today?",
      "Did you know mangoes are full of happiness vitamins? 🍋😄",
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

    // Filter out any user input with mean words
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
      // Basic fun filtering: if user is mean, redirect politely
      if (containsBannedWords(userText)) {
        return "Oops! Lil' Mango only shares kindness and good vibes. Let's keep it sweet!";
      }
      // Respond with a random mango phrase or an echo with mango twist
      const lower = userText.toLowerCase();

      // If user asks a question about mangoes, answer a random fact
      if (lower.includes('fact') || lower.includes('know') || lower.includes('mango') || lower.includes('tell')) {
        const fact = mangoFacts[Math.floor(Math.random() * mangoFacts.length)];
        return `🍋 Mango Fact for you: ${fact}`;
      }

      // If user says thanks or hi
      if (lower.includes('hi') || lower.includes('hello')) {
        return "Hey! Mango greetings to you! 🥭😊";
      }
      if (lower.includes('thank')) {
        return "You're very welcome! Stay juicy! 🍋";
      }

      // Otherwise random mango response
      return mangoResponses[Math.floor(Math.random() * mangoResponses.length)];
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

    sendButton.addEventListener('click', sendUserMessage);
    chatInput.addEventListener('keydown', e => {
      if (e.key === 'Enter') sendUserMessage();
    });

    // --- Mango Lovers Chat Room (local simulation) ---
    const roomChatContainer = document.getElementById('room-chat-container');
    const roomInput = document.getElementById('room-input');
    const roomSendButton = document.getElementById('room-send-button');

    // Simple chat history in-memory
    const roomMessages = [];

    function appendRoomMessage(text) {
      const msgDiv = document.createElement('div');
      msgDiv.classList.add('room-message');
      msgDiv.textContent = text;
      roomChatContainer.appendChild(msgDiv);
      roomChatContainer.scrollTop = roomChatContainer.scrollHeight;
    }

    function sendRoomMessage() {
      const text = roomInput.value.trim();
      if (!text) return;
      if (containsBannedWords(text)) {
        alert("Let's keep the chat kind and friendly, please!");
        roomInput.value = '';
        return;
      }
      // Add message to room messages
      roomMessages.push(text);
      appendRoomMessage(text);
      roomInput.value = '';
    }

    roomSendButton.addEventListener('click', sendRoomMessage);
    roomInput.addEventListener('keydown', e => {
      if (e.key === 'Enter') sendRoomMessage();
    });

    // Initialize with some welcome messages
    const welcomeMsgs = [
      "🍋 Welcome to Mango Lovers Chat Room! Say hi and share your mango stories!",
      "🥭 Lil' Mango says: Be kind and juicy!",
      "🍍 Remember, sharing is caring, especially with mangoes!"
    ];
    welcomeMsgs.forEach(msg => appendRoomMessage(msg));

  </script>
</body>
</html>

