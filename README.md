<div align="center">

# 📤 Bot Uploads

**Storage repository untuk file upload dari Telegram Bot**

[![Size](https://img.shields.io/github/repo-size/USERNAME/bot-uploads?style=flat&color=blue)](https://github.com/USERNAME/bot-uploads)
[![Last Commit](https://img.shields.io/github/last-commit/USERNAME/bot-uploads?style=flat&color=green)](https://github.com/USERNAME/bot-uploads)
[![Files](https://img.shields.io/github/directory-file-count/USERNAME/bot-uploads/uploads?style=flat&color=orange&label=files)](https://github.com/USERNAME/bot-uploads/tree/main/uploads)

</div>

---

## ⚠️ JANGAN HAPUS REPO INI

Repo ini digunakan bot Telegram sebagai **storage permanen** untuk file yang di-upload via command `/tourl`.

---

## 📂 Struktur

```

bot-uploads/
├── uploads/              ← file upload masuk sini
│   ├── image_.jpg
│   ├── video_.mp4
│   └── ...
├── docs/
│   └── API.md           ← dokumentasi API
├── .github/
│   └── workflows/
│       └── cleanup.yml  ← auto cleanup file lama
└── README.md

```

---

## 🔗 URL Akses

Setelah upload, file dapat diakses via:

```

https://raw.githubusercontent.com/USERNAME/bot-uploads/main/uploads/FILENAME

```

**Contoh:**
```

https://raw.githubusercontent.com/USERNAME/bot-uploads/main/uploads/image_1705123456_a3f9b2.jpg

```

---

## 📊 Batasan

| Aspek | Limit |
|-------|-------|
| Max file | 100 MB |
| Max repo | 5 GB (free) |
| Rate limit | 5000 req/jam |

---

## 🧹 Cleanup

### Manual
1. Buka folder `uploads/`
2. Klik file → 🗑️ → Commit

### Otomatis
Workflow `cleanup.yml` akan hapus file **> 30 hari** setiap hari Minggu jam 3 pagi.

---

## 🔐 Keamanan

- ✅ Repo **public** — diperlukan untuk raw URL access
- ✅ Token bot **tidak disimpan** di repo
- ✅ Auto-cleanup file lama untuk hemat storage

---

## 📝 Lisensi

MIT License — bebas pakai & modifikasi.
