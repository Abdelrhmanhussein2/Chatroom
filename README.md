# 💬 Simple Chatroom — Go RPC Edition  

A lightweight chatroom built entirely with **Go’s `net/rpc`**, where every message counts.  
Clients send messages to a central RPC server, and the server keeps everyone in sync by returning the full chat history every time.  

> Think of it as a minimalist WhatsApp that runs straight from your terminal 😄  

---

## 🎬 Demo  

🎥 [**See it in action**](https://drive.google.com/drive/folders/1URbr35o-_0t1axnYDAsKqbcgyf6X1dTb)

---

## 🚀 Highlights  

✅ **Real-time sync (via RPC):** every message you send updates the shared chat instantly.  
✅ **In-memory history:** all messages live inside the server’s memory — fast and simple.  
✅ **Multi-client ready:** open multiple terminals, and everyone chats in the same room.  
✅ **User-friendly input:** supports full sentences, not just single words.  
✅ **Smooth exit:** type `exit` or hit `Ctrl + C` to gracefully leave the room.  

---

## ⚙️ How to Run  

### 🖥️ 1. Start the Server  
```bash
go run server.go
```

### 💻 2. Launch one or more Clients  
```bash
go run client.go
```

Each client acts as a user connected to the same global chatroom.  

---

## 🧠 Example Interaction  

```
> [You]: Hey everyone!
--- Chat History ---
You: Hey everyone!
--------------------

> [Friend]: Hello! How’s it going?
--- Chat History ---
You: Hey everyone!
Friend: Hello! How’s it going?
--------------------
```

---

## 🧩 Project Structure  

### 🧱 `server.go`  
- Runs the **RPC server** that coordinates all clients.  
- Stores messages in a global list (**in-memory**).  
- Provides two main remote procedures:  
  - `SendMessage`: appends a message and returns the full chat history.  
  - `GetHistory`: returns the current chat log.  
- Uses a **mutex lock** for safe concurrent access.  

---

### 💬 `client.go`  
- Prompts for your **username**.  
- Reads **entire lines** (supports spaces).  
- Sends messages via RPC and displays the updated chat log.  
- Keeps running indefinitely — until you decide to leave.  
- Gracefully handles server disconnects.  

---

## 🧰 Tech Stack  

| Component | Description |
|------------|-------------|
| **Language** | Go |
| **Networking** | net/rpc |
| **Concurrency** | goroutines + sync.Mutex |

---

## 🧾 Notes  

- All messages are stored **in RAM**, so they disappear once the server stops.  
- Works perfectly **offline** — no internet required.  
- Simple, clean, and a great introduction to **Go’s RPC system**.  

---

⭐ *Made with Go — because sometimes, simplicity just works.*
