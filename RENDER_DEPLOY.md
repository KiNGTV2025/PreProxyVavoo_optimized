# 🎨 Render.com Deployment - StreamFlow Proxy Fast

## 🚀 Hızlı Deploy

### 1. GitHub'a Yükle
```bash
cd streamflow-proxy-fast
git init
git add .
git commit -m "Initial commit"
git push
```

### 2. Render.com
1. https://render.com → **New +** → **Web Service**
2. Connect GitHub repo
3. Settings:
   ```
   Name: streamflow-proxy-fast
   Region: Frankfurt
   Runtime: Docker
   Plan: Free
   ```
4. **Create** → Deploy başlar ✅

**Süre**: 3-5 dakika

---

## 📁 Dosyalar

```
streamflow-proxy-fast/
├── Dockerfile
├── app.py
├── requirements.txt
├── render.yaml      # ← Yeni ekle
└── README.md
```

---

## ⚙️ Environment Variables

Render dashboard'da otomatik:

```bash
PORT=10000  # Render atar
PYTHONUNBUFFERED=1
GEVENT_RESOLVER=ares
```

---

## 🐛 Sleep Sorunu & Çözüm

### Problem
15 dakika inaktivite → Sleep → 30s cold start

### Çözüm: UptimeRobot ✅

1. https://uptimerobot.com
2. **Add Monitor**:
   ```
   URL: https://your-app.onrender.com/health
   Interval: 5 minutes
   ```
3. ✅ Save

App artık 7/24 aktif!

---

## 💰 Maliyet

**Free Tier**:
- 750h/ay (31 gün yeterli)
- StreamFlow çok hafif: ~$0

**UptimeRobot**:
- Free: 50 monitor
- Maliyet: $0

**Toplam: $0/ay** ✅

---

## 🎯 Kullanım

```bash
# M3U8 Proxy
https://your-app.onrender.com/proxy/m3u?url=STREAM_URL

# Auto Resolve
https://your-app.onrender.com/proxy/resolve?url=EMBED_URL

# Stats
https://your-app.onrender.com/api/stats
```

---

## ✅ Checklist

- [ ] render.yaml eklendi
- [ ] GitHub repo hazır
- [ ] Render'da deploy edildi
- [ ] UptimeRobot eklendi
- [ ] Test edildi ✅

---

## 💡 İpucu

**Render sleep sorunlu!**

Alternatif:
- **Railway**: Sleep yok, $1-2/ay ✅✅✅
- **Fly.io**: %100 ücretsiz ✅✅

Render free tier için UptimeRobot şart!
