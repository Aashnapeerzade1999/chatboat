<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chatbot with Menu</title>
  <style>
    body {
      font-family: "Arial", sans-serif;
      margin: 0;
      padding: 0;
    }

    .gif-trigger {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 1;
      cursor: pointer;
      height: 100px;
      /* transition: transform 0.3s ease; Add transition for smooth movement */
    }

    /* .gif-trigger:hover  {
      opacity: 1;
      visibility: visible;
      bottom: 10px; 
      /* transform: translateX(3px); Move right by 5px on hover */
   
.overlay{
background-color: gray;
}

    .chat-container {
      width: 300px;
      height: 350px;
      position: fixed;
      bottom: 20px;
      right: 10px;
      background-color: #ffffff;
      border: 1px solid #ffffff;
      border-radius: 10px;
      overflow-y: auto;
      overflow-x: hidden;
      display: none;
    }

    .chat-header {
      background-color: #07a5ee;
      color: #fff;
      padding: 10px;
      border-radius: 10px 10px 0 0;
      width: 100%;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .chat-header h2 {
      margin: 0;
      font-size: 18px;
    }

    .chat-box {
      padding: 10px;
    }

    .message {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
    }

    .message.bot {
      justify-content: flex-start;
    }

    .message.user {
      justify-content: flex-end;
    }

    .message p {
      background-color: #d3e7f4;
      color: #000;
      padding: 10px;
      border-radius: 20px;
      max-width: 70%;
      word-wrap: break-word;
    }

    .message.user p {
      background-color: #a0e7e5;
      color: #000;
    }

    #user-input {
      width: calc(100% - 70px);
      padding: 10px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 5px;
      margin-bottom: 10px;
      position: sticky;
    }

    #send-btn {
      width: 60px;
      background-color: #4CAF50;
      color: #fff;
      padding: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      position: sticky;
    }

    #send-btn:hover {
      background-color: #3e8e41;
    }

    .menu {
      display: flex;
      flex-direction: column;
      width: 100%;
      margin: 10px 0;
    }

    .menu a {
      font-family: 'Times New Roman', Times, serif;
      color: #030303;
      cursor: pointer;
      font-size: 16px;
      font-weight: 100;
      line-height: 1;
      text-align: center;
      margin: 1vh auto;
      padding: 1vh 0;
      width: 80%;
      background: rgba(255, 255, 255, 0.3);
      backdrop-filter: blur(15px);
      border-radius: 5px;
      text-decoration: none;
      will-change: color, text-shadow, font-size;
      transition: all 0.3s ease;
      border: 1px solid #07a5ee;
      background-color: #c4dae4;
    }

    .menu a:hover {
      transform: scale(1);
      background: rgba(255, 255, 255, 0.8);
    }

    .menu_1 {
      display: flex;
      flex-direction: column;
      width: 100%;
      margin: 10px 0;
    }

    .menu_1 a {
        font-family: 'Times New Roman', Times, serif;
      color: #030303;
      cursor: pointer;
      font-size: 16px;
      font-weight: 100;
      line-height: 1;
      text-align: center;
      margin: 1vh auto;
      padding: 1vh 0;
      width: 80%;
      background: rgba(255, 255, 255, 0.3);
      backdrop-filter: blur(15px);
      border-radius: 5px;
      text-decoration: none;
      will-change: color, text-shadow, font-size;
      transition: all 0.3s ease;
      border: 1px solid #07a5ee;
      background-color: #c4dae4;
    }

    .menu_1 a:hover {
      transform: scale(1);
      background: rgba(255, 255, 255, 0.8);
    }
  </style>
</head>
<body>

  <div class="chat-container" id="chat-container">
    <div class="chat-header">
      <h2>Chatbot</h2>
    </div>
    <div class="chat-box" id="chat-box">
      <div class="menu_1">
        <a href="#" class="menu-item_1" data-response="Enter your number:">Enter your number:</a>
        <a href="#" class="menu-item_1" data-response="Please complete your KYC.">complete your KYC.</a>
        <a href="#" class="menu-item_1" data-response="What would you like to update?">What would you like to update</a>
        <a href="#" class="menu-item_1" data-response="Please verify your details.">verify your details</a>
        <a href="#" class="menu-item_1" data-response="Please verify your details. first"> verify your contact us</a>
        <!-- Add more menu items here -->
      </div>
      <div class="message bot"></div>
    </div>
    <input type="text" id="user-input" placeholder="Type your message...">
    <button id="send-btn">Send</button>
  </div>

  <div class="gif-trigger">
    <img src="gif.gif" class="gif-trigger" alt="Cute GIF">
    <!-- <div class="overlay">hi from comet AI</div> -->
  </div>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      const gifTrigger = document.querySelector('.gif-trigger');
      const chatContainer = document.getElementById('chat-container');
      const chatBox = document.getElementById('chat-box');
      const userInput = document.getElementById('user-input');
      const sendBtn = document.getElementById('send-btn');
      const menuItems = document.querySelectorAll('.menu-item_1');

      gifTrigger.addEventListener('mouseenter', function() {
        const overlay = this.querySelector('.overlay');
        overlay.style.opacity = '1';
        overlay.style.visibility = 'visible';
      });

      gifTrigger.addEventListener('mouseleave', function() {
        const overlay = this.querySelector('.overlay');
        overlay.style.opacity = '0';
        overlay.style.visibility = 'hidden';
      });
      
  gifTrigger.addEventListener('click', function() {
  if (chatContainer.style.display === 'block') {
    chatContainer.style.display = 'none';
  } else {
    chatContainer.style.display = 'block';
  }
});


      function sendMessage(message, sender) {
        const messageElement = document.createElement('div');
        messageElement.classList.add('message', sender);
        const messageContent = document.createElement('p');
        messageContent.innerText = message;
        messageElement.appendChild(messageContent);
        chatBox.appendChild(messageElement);
        chatBox.scrollTop = chatBox.scrollHeight;
      }

      function createMenu() {
        const menu = document.createElement('div');
        menu.className = 'menu';
        const menuItems = [
          { text: 'Enter your number:', response: 'Enter your number:' },
          { text: 'Please complete your KYC.', response: 'Please complete your KYC.' },
          { text: 'What would you like to update?', response: 'What would you like to update?' },
          { text: 'Please verify your details.', response: 'Please verify your details.' }
        ];
        menuItems.forEach(item => {
          const link = document.createElement('a');
          link.href = '#';
          link.className = 'menu-item';
          link.setAttribute('data-response', item.response);
          link.innerText = item.text;
          link.addEventListener('click', function() {
            sendMessage(item.response, 'bot');
          });
          menu.appendChild(link);
        });
        return menu;
      }

      function botReply(message) {
        let reply = "I'm sorry, I didn't understand that. Can you please be more specific?";

        const lowerCaseMessage = message.toLowerCase();

        if (lowerCaseMessage === 'hi' || lowerCaseMessage === 'hello') {
          reply = "Hello there! How can I help you today?";
          sendMessage(reply, 'bot');
        }
         else if (lowerCaseMessage === 'menu') {
          const menu = createMenu();
          chatBox.appendChild(menu);
          chatBox.scrollTop = chatBox.scrollHeight;
        }
        else if (lowerCaseMessage === 'i want to create my account'||lowerCaseMessage === 'new account') {
            reply = "ok enter your number register your self  fisrt";
            sendMessage(reply, 'bot');
        }
        else if (lowerCaseMessage === 'kyc'||lowerCaseMessage === 'KYC') {
            reply = "i sent to otp first enter your number";
            sendMessage(reply, 'bot');
        }
        else {
          sendMessage(reply, 'bot');
        }
      }

      sendBtn.addEventListener('click', function() {
        const userMessage = userInput.value.trim();
        if (userMessage !== '') {
          sendMessage(userMessage, 'user');
          userInput.value = '';
          botReply(userMessage);
        }
      });

      userInput.addEventListener('keydown', function(e) {
        if (e.key === 'Enter') {
          sendBtn.click();
        }
      });

      menuItems.forEach(item => {
        item.addEventListener('click', function() {
          const response = this.getAttribute('data-response');
          sendMessage(response, 'bot');
        });
      });
    });
  </script>

</body>
</html>
