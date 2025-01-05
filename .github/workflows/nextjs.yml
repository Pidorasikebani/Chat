let nickname = "";
const chatBox = document.getElementById("chat-box");
const messageInput = document.getElementById("message");
const sendButton = document.getElementById("send-btn");
const loginSection = document.getElementById("login-section");
const chatSection = document.getElementById("chat-section");
const loginButton = document.getElementById("login-btn");

// Загружаем сообщения из LocalStorage
function loadMessages() {
    const messages = JSON.parse(localStorage.getItem("chatMessages")) || [];
    renderMessages(messages);
}

// Сохраняем сообщение в LocalStorage
function saveMessage(nickname, message) {
    const messages = JSON.parse(localStorage.getItem("chatMessages")) || [];
    const time = new Date().toLocaleTimeString();
    messages.push({ nickname, message, time });
    localStorage.setItem("chatMessages", JSON.stringify(messages));
    renderMessages(messages);
}

// Отображаем сообщения на экране
function renderMessages(messages) {
    chatBox.innerHTML = messages
        .map(
            (msg) =>
                `<div class="message">
                    <span class="nickname">${msg.nickname}</span>: 
                    <span>${msg.message}</span>
                    <div class="time">${msg.time}</div>
                </div>`
        )
        .join("");
    chatBox.scrollTop = chatBox.scrollHeight;
}

// Авторизация пользователя
loginButton.addEventListener("click", () => {
    const nicknameInput = document.getElementById("nickname").value.trim();
    if (nicknameInput) {
        nickname = nicknameInput;
        loginSection.style.display = "none";
        chatSection.style.display = "block";
        loadMessages();
    } else {
        alert("Введите ник!");
    }
});

// Отправка сообщения
sendButton.addEventListener("click", () => {
    const message = messageInput.value.trim();
    if (message) {
        saveMessage(nickname, message);
        messageInput.value = "";
    }
});

// Загрузка сообщений при старте
loadMessages();
