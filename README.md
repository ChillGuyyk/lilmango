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
    #
