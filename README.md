# Blade & Shield ⚔️🛡️

**A two‑player card game of truth, treachery, and tactical risk — played peer‑to‑peer in your browser.**


## 🎮 What is Blade & Shield?

Blade & Shield is a head‑to‑head duelling card game where you set traps and read your opponent.  
Each round, the **setter** places three cards face‑down — a mixture of truth and bluff — and can optionally attach a **gamble** card to double down on damage. The **caller** then guesses the majority (truths or bluffs). A correct call grants a protective block; a wrong call unleashes damage.  

No accounts. No downloads. Just open the page, share your Peer ID, and play.


## 🃏 The Cards

- **Truth** (green T) — defensive; a majority of truths grants **block** to the winner of the call.  
- **Bluff** (red B) — offensive; a majority of bluffs deals **damage**.  
- **Gamble** (gold G) — optional extra card that adds **bonus damage** equal to the number of bluffs in the set.

You always hold **5 cards** in hand. After each round, your cards are discarded and you draw back to five.


## 🧩 How a Round Works

1. **Setter’s turn**  
   - Fill **exactly 3 set slots** with any combination of cards (at least one Bluff or Gamble must be among them).  
   - Optionally place a **Gamble** card in the Gamble zone.  
   - Lock your selection by clicking **Confirm Set**.

2. **Caller’s turn**  
   - The Caller sees only face‑down cards and whether a Gamble was attached.  
   - Choose to call **Truths** or **Bluffs** (guess the majority).

3. **Reveal**  
   - All cards are revealed. The majority is determined.  
   - **Winner of the call** (who guessed correctly) receives **+X block**, where X is the number of Truths (if the majority was Truths).  
   - **Damage** is dealt to the loser: the number of Bluffs (if majority Bluffs) **plus** any Gamble damage.  
   - Block absorbs damage first.  
   - Both players discard their used hand and draw new cards.

4. **Swap roles**  
   - After the round, the Setter becomes the Caller, and vice versa.  
   - First to reduce the opponent’s HP to 0 wins!


## 🌐 Connecting & Playing

The game uses **PeerJS** to create a direct peer‑to‑peer connection between browsers.  
By default, it connects to the public `0.peerjs.com` signaling server, but this server **may be blocked in some regions**.  
The game includes a built‑in **Advanced** panel so you can point it to your own custom signaling server — completely solving the connectivity issue.

### Quick Start (using the default server)

1. Open [index.html](https://yatoalma.github.io/BladeAndShield1/) in your browser.  
2. Wait for your **Peer ID** to appear.  
3. Share your ID with your opponent (via chat, email, etc.).  
4. Your opponent pastes your ID and clicks **Connect**.  
5. The game starts automatically — no sign‑up required.

### 🔧 Using a Custom Signaling Server (recommended for blocked regions)

If you see **“Could not reach the connection server”** or you’re in a country where `0.peerjs.com` is blocked, follow these steps:

#### Option A: Use an existing community server (if available)

Sometimes friends run shared servers. If you know the host, port, and path, just fill the **Advanced** panel.

#### Option B: Deploy your own server on Render (free, 5 minutes)

1. Create a free account at [render.com](https://render.com).  
2. Create a new **Web Service** from a public GitHub repository containing these two files:
   - **`package.json`**
     ```json
     {
       "name": "peerjs-signal",
       "scripts": { "start": "npx peerjs --port $PORT --path /" },
       "dependencies": { "peer": "^1.0.2" }
     }
   - **`server.js`**
     ''' server.js (can be empty)
     Set the Start Command to npm start and use the Free instance type.

3. Once deployed, you’ll get a URL like https://your-service.onrender.com.
4. In the game’s Advanced panel, enter:
- Host: your-service.onrender.com
- Port: 443
- Path: /
- Secure (HTTPS): ✅ checked
6. Click Save — your Peer ID will appear instantly.

Both players must use the same custom server to see each other.



🛠️ Tech Stack

PeerJS (WebRTC) for peer‑to‑peer data channel
Render (or any Node.js host) for the optional custom signaling server
Vanilla JavaScript, CSS, and HTML — no frameworks
Fonts: Google Fonts (Cinzel, Inter)


🤝 Credits
Built with ❤️ as a showcase of browser‑based P2P gaming.
No accounts, no tracking, no ads. Just you and your opponent.

If you run into issues, check the browser console (F12) for detailed diagnostic messages.

