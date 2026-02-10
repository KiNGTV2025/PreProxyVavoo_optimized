# 🚂 Railway.app Deployment - StreamFlow Proxy Fast

## 🚀 Hızlı Başlangıç

### 1. GitHub'a Yükle
```bash
cd streamflow-proxy-fast
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/USERNAME/streamflow-proxy.git
git push -u origin main
```

### 2. Railway'de Deploy
1. https://railway.app → **New Project**
2. **Deploy from GitHub repo**
3. Repository seç
4. Otomatik deploy başlar ✅

### 3. Test Et
```bash
curl https://your-app.up.railway.app/health
```

---

## 📁 Gerekli Dosyalar

Proje root'unda:
```
streamflow-proxy-fast/
├── app.py
├── requirements.txt
├── nixpacks.toml          ← Yeni ekle
├── .env.example           ← Yeni ekle
├── README.md
└── .gitignore
```

---

## ⚙️ Environment Variables

Railway dashboard → **Variables** sekmesi:

**Zorunlu** (Railway otomatik ekler):
```bash
PORT=${{PORT}}
```

**Opsiyonel**:
```bash
PYTHONUNBUFFERED=1
GEVENT_RESOLVER=ares
```

---

## 🔧 nixpacks.toml Açıklaması

```toml
[start]
cmd = "python app.py"
```

Basit! StreamFlow Proxy hafif bir app, extra dependency yok.

---

## 📊 Railway Free Tier Kullanımı

StreamFlow Proxy çok hafif:
- **Idle**: ~$0.50/ay
- **Orta kullanım**: ~$1-2/ay
- **Yoğun kullanım**: ~$3-4/ay

**$5/ay kredi ile rahatça kullanılır!**

---

## 🎯 Kullanım

Deploy sonrası URL:
```
https://your-app.up.railway.app
```

### M3U8 Proxy
```
https://your-app.up.railway.app/proxy/m3u?url=STREAM_URL
```

### Auto Resolve
```
https://your-app.up.railway.app/proxy/resolve?url=EMBED_URL
```

### API Stats
```
https://your-app.up.railway.app/api/stats
```

---

## 🐛 Troubleshooting

### App Crashes
```bash
# Logs kontrol et
railway logs

# Port binding kontrol et - app.py'de:
PORT = int(os.environ.get("PORT", 7860))
```

### Slow Performance
```python
# Session pool zaten optimize, ek ayar gerekmez
# Gerekirse chunk size artır (app.py line 250):
chunk_size = 131072  # 128KB
```

---

## ✅ Checklist

- [ ] nixpacks.toml eklendi
- [ ] GitHub repo hazır
- [ ] Railway hesabı var
- [ ] Deploy tamamlandı
- [ ] Health check çalışıyor
- [ ] Test stream başarılı

---

**🎉 Hazır! StreamFlow Proxy Railway'de çalışıyor.**

Çok daha hızlı ve stabil! ⚡
