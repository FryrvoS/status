<p align="center">
    <a href="https://fryrvo.com" target="_blank" rel="noopener noreferrer">
        <img src="https://cdn.fryrvo.com/assets/fryrvo_branding/Logo_bg.png" alt="icon" width="120">
    </a>
</p>

<div align="center">

# Status
Source code for the Fryrvo Status page at [status.fryrvo.com](https://status.fryrvo.com)

</div>

> [!NOTE]
> **Note:** This repository is a fork of [louislam/uptime-kuma](https://github.com/louislam/uptime-kuma). please go check them out!

---

### Docker Compose

```bash
mkdir fryrvo-status
cd fryrvo-status
curl -o compose.yaml https://git.lgbt/api/v1/repos/fryrvo/status/raw/compose.yaml
docker compose up -d
```
page is now running on all network interfaces (e.g. http://localhost:3001 or http://your-ip:3001).

### Non-Docker


```bash
git clone https://git.lgbt/fryrvo/status.git
cd status
npm run setup

# Option 1. Try it
node server/server.js

# (Recommended) Option 2. Run in the background using PM2
# Install PM2 if you don't have it:
npm install pm2 -g && pm2 install pm2-logrotate

# Start Server
pm2 start server/server.js --name fryrvo-status
```
Uptime Kuma is now running on all network interfaces (e.g. http://localhost:3001 or http://your-ip:3001).


### Build
```bash
npm run build
docker build -f docker/dockerfile --target release -t git.lgbt/fryrvo/status:latest .
docker push git.lgbt/fryrvo/status:latest
```

### update on server
```bash
cd ~/fryrvo-status
docker compose pull
docker compose up -d
docker compose logs -f
```