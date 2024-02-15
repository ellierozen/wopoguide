---
layout: home
search_exclude: true
permalink: /ai
---

<html>
<head>
    <style>
    body {
    font-family: Arial, sans-serif;
    background-color: #006FB9;
}
.main-header {
    font-size: 30px;
    text-align: center;
    margin-bottom: 10px;
    color: #ADD8E6;
}
.sub-header {
    font-size: 25px;
    text-align: center;
    margin-bottom: 30px;
    color: #ADD8E6;
}
.chat-container {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
     max-height: 800px;
}
.chat-messages {
    margin-bottom: 20px;
    overflow-y: auto;
    max-height: 300px;
}
.message {
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    color:#000000
}
.user {
    background-color: #f2f2f2;
    text-align: right;
}
.bot {
    background-color: #e6f7ff;
    text-align: left;
}
.user-input {
    width: calc(100% - 70px);
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
}
.send-button {
    width: 60px;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
    transition: background-color 0.3s;
}
.send-button:hover {
    background-color: #0056b3;
}
</style>
</head>
<body>
    <h1 class="main-header">Chatbot</h1>
    <h2 class = "sub-header">Ask it anything about water polo</h2>
    <div class="chat-container">
        <div id="chat-messages" class="chat-messages"></div>
        <input type="text" id="user-input" class="user-input" placeholder="Type your message...">
        <button onclick="sendMessage()" class="send-button">Send</button>
    </div>
    <!-- Gif -->
    <img src="https://cdn.discordapp.com/attachments/879557685253664768/1207445276508299274/dgcrl11-19db592b-2427-44de-b7e4-8c317c14eda1.gif?ex=65dfac0b&is=65cd370b&hm=be9b878b6715fd585b69f5349b15b30c61b98b890034205ede26eecf3eff6880&" alt="Avatar" style="width:100%; height:150px">
    <script>
        const chatMessages = document.getElementById('chat-messages');
        const userInput = document.getElementById('user-input');
        function appendMessage(role, content) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message', role);
            messageDiv.innerText = content;
            chatMessages.appendChild(messageDiv);
        }
        function sendMessage() {
            const userMessage = userInput.value;
            appendMessage('user', userMessage);
            // Send user message to backend
            fetch('http://127.0.0.1:8088/api/ai/ask', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    model: 'gpt-3.5-turbo',
                    prompt: userMessage
                })
            })
            .then(response => response.json())
            .then(data => {
                const botMessage = data.answer;
                appendMessage('bot', botMessage);
            })
            .catch(error => {
                console.error('Error:', error);
                appendMessage('bot', 'Error occurred while processing your message.');
            });
            // Clear user input field
            userInput.value = '';
        }
    </script>
</body>
</html>
