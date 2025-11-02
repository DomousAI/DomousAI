body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    height: 100vh;
}

.gradient-background {
    background: linear-gradient(135deg, #74ebd5, #acb6e5);
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
}

.chatbot {
    background: white;
    border-radius: 10px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.1);
    width: 300px;
    max-width: 90%;
    display: flex;
    flex-direction: column;
}

.chatbot-header {
    background: #007BFF;
    color: white;
    padding: 10px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    text-align: center;
}

.chatbot-messages {
    flex-grow: 1;
    padding: 10px;
    overflow-y: auto;
    max-height: 300px;
    border: 1px solid #ddd;
}
