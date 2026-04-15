# 🎧 MAMArr WebApp

Self-hosted web interface for **MyAnonamouse** audiobook lovers.  
Search, preview, and send torrents directly to **qBittorrent** — with optional **Discord notifications** and full Docker support.

---

## 🚀 Features

✅ **FastAPI Backend** — Handles user auth, MAM search, and torrent management  
✅ **React + Tailwind Frontend** — Responsive UI with cover art and toast notifications  
✅ **qBittorrent Integration** — Send torrents straight to your client  
✅ **Discord Webhook** — Get notified when new torrents are added  
✅ **Docker Ready** — One-command deployment on any server or NAS  
✅ **Nginx Frontend Hosting** — Optimized static serving for lightweight setups  

---

## 🧩 Project Structure

```
mam-webapp/
├── backend/
│   ├── main.py              # FastAPI backend
│   ├── requirements.txt
│   ├── .env.example         # Example environment variables
│
├── frontend/
│   ├── src/                 # React app source
│   ├── index.css            # Tailwind styles
│   ├── App.jsx              # Main UI logic
│   ├── vite.config.mjs
│   ├── Dockerfile           # Nginx + build container
│
├── docker-compose.yml       # Stack definition
├── README.md
└── LICENSE
```

---

## ⚙️ Environment Setup

Create a `.env` file inside `backend/` based on the provided `.env.example`:

```env
# Example .env

# --- MyAnonamouse ---
MAM_COOKIE=YOUR_MAM_COOKIE_HERE
MAM_BASE=https://www.myanonamouse.net

# --- qBittorrent ---
QBITTORRENT_URL=http://qbittorrent:8080
QBITTORRENT_USER=admin
QBITTORRENT_PASS=adminadmin
QBITTORRENT_SAVEPATH=/media/audiobooks

# --- App ---
JWT_SECRET=change_this_secret_key
INVITE_CODE=invite-only-secret

# --- Optional Discord Webhook ---
DISCORD_WEBHOOK=https://discord.com/api/webhooks/XXXXXXXX
```

---

## 🔑 Getting Your MAM ID and Cookie

You’ll need both a **MAM ID** and a **Cookie** for API access:

1. **Log in** to [MyAnonamouse.net](https://www.myanonamouse.net)
2. Go to **Profile → Security**
3. Copy your **Security Identifier (MAM ID)**  
4. Open **Developer Tools → Application → Cookies**
5. Copy the entire **`mam_id`** or **`uid`** cookie value
6. Add both to your `.env` file

⚠️ **Never share your MAM cookie or ID publicly!**

---

## 🐳 Docker Deployment

### Build & Start
```bash
docker compose up -d --build
```

### Stop
```bash
docker compose down
```

### Verify
```bash
curl http://localhost:5747/api/test
# {"status":"ok"}
```

---

## 🌐 Reverse Proxy (Optional)

You can expose both services via **Nginx Proxy Manager** (or Caddy, Traefik, etc.):


| Service | Example URL                | Internal Port |
|----------|---------------------------|----------------|
| Frontend | https://mam.yourdomain.uk | 5050 |
| Backend  | https://api.yourdomain.uk | 5747 |

✅ Ensure both use **HTTPS** and **WebSockets** are enabled.

---

## 🪩 Example Workflow

1. Login or register with your invite code  
2. Search audiobooks by **title**, **author**, **series**, or **narrator**  
3. Preview cover art (from **iTunes** / **Google Books**)  
4. Click **“Add to qBittorrent”**  
5. A modern toast appears on-screen  
6. (Optional) Discord webhook sends a styled notification  

---

## 📦 Tech Stack

| Layer | Technology |
|-------|-------------|
| Backend | FastAPI (Python 3.12) |
| Frontend | React + Vite + TailwindCSS |
| Database | SQLite |
| Notifications | Discord Webhook |
| Deployment | Docker / Docker Compose |
| Proxy | Nginx Proxy Manager |

—

<img width="1920" height="898" alt="image" src="https://github.com/user-attachments/assets/1b3c6b43-f5ed-4acd-8478-5c3771edf5d7" />

<img width="1881" height="1043" alt="image" src="https://github.com/user-attachments/assets/2beea17c-f630-445e-9342-364df8f2fad3" />


## 🧠 Credits

Created by [**(ipillyx)**](https://github.com/ipillyx)  
Built with ❤️ for the MAM community.

---

## 📝 License

MIT License © 2025 

