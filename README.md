# WebSocket Echo Server
---
## Project Description
The WebSocket Echo Server is a lightweight and efficient application designed to demonstrate real-time communication between a client and server using WebSocket technology. It showcases a minimalistic architecture where the server echoes any message it receives back to the client.

## Why WebSockets?
WebSockets provide full-duplex communication over a single TCP connection, making them ideal for real-time applications like chat apps, stock tickers, and collaborative tools.
This project emphasizes simplicity and efficiency, showcasing how to build a WebSocket server and client from scratch.
---
## Table of Contents
  - [Installation and Setup](#installation-and-setup)
  - [Usage Instructions](#usage-instructions)
  - [How It Works](#how-it-works)
  - [Additional Information](#additional-information)


---

# Installation and Setup
  ## Prerequisites
- Node.js (Download from Node.js)
- A modern web browser for testing the client.

  ## Setup Instructions
  - Clone the Repository:
    
 ```   
git clone https://github.com/SebastianPE0/JS_WebSocket.git
   ```

  ```
cd WebSocketEchoServer
  ```

  - Install Dependencies:
    
  ```
npm install
  ```

  - Run the Server:

  ```
node server.js
  ```
The server will start on ws://localhost:8080.

## Usage Instructions
  1. Open the client.html file in your browser.
  2. Connect to the server.
  3. Type a message in the input field and click Send.
  4. Observe the echoed message from the server in the browser.

## How It Works
  - Server (server.js)
The server is implemented using Node.js and the ws library:

  - Listens for WebSocket connections.
  - Handles incoming messages and echoes them back.
Example Code:

  ```
const WebSocket = require('ws');

const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', (ws) => {
    ws.on('message', (message) => {
        ws.send(`Echo: ${message}`);
    });
});
  ```
  ### Client (client.html)

A simple HTML page with embedded JavaScript to interact with the WebSocket server:

  - Connects to the WebSocket server.
Sends messages and displays responses dynamically.
Example Code:

  ```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>WebSocket Client</title>
</head>
<body>
    <h1>WebSocket Client</h1>
    <input id="message" type="text" placeholder="Enter a message">
    <button onclick="sendMessage()">Send</button>
    <div id="output"></div>

    <script>
        const socket = new WebSocket('ws://localhost:8080');

        socket.onmessage = (event) => {
            document.getElementById('output').innerHTML += `<p>${event.data}</p>`;
        };

        function sendMessage() {
            const msg = document.getElementById('message').value;
            socket.send(msg);
        }
    </script>
</body>
</html>
  ```
--- 
## Additional Information
Screenshot of the execution is added where the execution of the client and the message reflected on the server are checked

![image](https://github.com/user-attachments/assets/da78f697-e147-4bf8-b635-c2e3bb2d7756)

