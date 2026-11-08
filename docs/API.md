# 📡 API Upload — Dokumentasi

Dokumentasi lengkap cara upload ke repo ini via API GitHub.

## Endpoint

```

PUT https://api.github.com/repos/{owner}/{repo}/contents/uploads/{filename}

```

## Headers

```http
Authorization: Bearer ghp_xxxxxxxxxxxx
Accept: application/vnd.github+json
X-GitHub-Api-Version: 2022-11-28
User-Agent: TelegramBot-Uploader
Content-Type: application/json
```

Body

```json
{
  "message": "📤 Upload: filename.ext",
  "content": "<base64-encoded-file>",
  "branch": "main"
}
```

Response Sukses

```json
{
  "content": {
    "name": "filename.ext",
    "path": "uploads/filename.ext",
    "sha": "abc123...",
    "size": 12345,
    "download_url": "https://raw.githubusercontent.com/USERNAME/bot-uploads/main/uploads/filename.ext",
    "html_url": "https://github.com/USERNAME/bot-uploads/blob/main/uploads/filename.ext"
  }
}
```

Error Codes

Code Meaning
401 Token invalid/expired
403 Rate limit / no permission
404 Repo not found
409 File conflict (file already exists)
422 Validation failed (file too large)

Limit

· Max file: 100 MB
· Rate limit: 5000 req/jam per token
· Max repo size: 5 GB (free), 100 GB (pro)

---

🐍 Contoh Python

```python
import base64
import requests

TOKEN = "ghp_xxx"
OWNER = "USERNAME"
REPO = "bot-uploads"

def upload(filename, content):
    url = f"https://api.github.com/repos/{OWNER}/{REPO}/contents/uploads/{filename}"
    data = {
        "message": f"Upload {filename}",
        "content": base64.b64encode(content).decode(),
        "branch": "main"
    }
    headers = {
        "Authorization": f"Bearer {TOKEN}",
        "Accept": "application/vnd.github+json",
        "X-GitHub-Api-Version": "2022-11-28"
    }
    r = requests.put(url, json=data, headers=headers, timeout=60)
    r.raise_for_status()
    return r.json()["content"]["download_url"]

# Contoh pakai
with open("foto.jpg", "rb") as f:
    url = upload("foto.jpg", f.read())
    print(url)
```

---

🟢 Contoh Node.js

```javascript
const axios = require('axios');
const fs = require('fs');

const TOKEN = 'ghp_xxx';
const OWNER = 'USERNAME';
const REPO = 'bot-uploads';

async function uploadToGithub(filename, buffer) {
    const content = buffer.toString('base64');
    const path = `uploads/${filename}`;
    
    const res = await axios.put(
        `https://api.github.com/repos/${OWNER}/${REPO}/contents/${path}`,
        {
            message: `📤 Upload: ${filename}`,
            content,
            branch: 'main'
        },
        {
            headers: {
                'Authorization': `Bearer ${TOKEN}`,
                'Accept': 'application/vnd.github+json',
                'X-GitHub-Api-Version': '2022-11-28'
            },
            timeout: 60000
        }
    );
    
    return res.data.content.download_url;
}

// Contoh pakai
const buffer = fs.readFileSync('foto.jpg');
uploadToGithub('foto.jpg', buffer).then(url => console.log(url));
```

---

🐚 Contoh cURL

```bash
# Encode file ke base64
BASE64=$(base64 -w 0 foto.jpg)

# Upload
curl -X PUT \
  -H "Authorization: Bearer ghp_xxx" \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -d "{\"message\":\"Upload\",\"content\":\"$BASE64\",\"branch\":\"main\"}" \
  https://api.github.com/repos/USERNAME/bot-uploads/contents/uploads/foto.jpg
```

---

🔗 URL Akses

Setelah upload, file bisa diakses via:

```
https://raw.githubusercontent.com/USERNAME/bot-uploads/main/uploads/FILENAME
```

Untuk download:

```
https://github.com/USERNAME/bot-uploads/raw/main/uploads/FILENAME
```

Untuk lihat di GitHub:

```
https://github.com/USERNAME/bot-uploads/blob/main/uploads/FILENAME
```

```

Commit changes.

---

### 📄 File 7: `LICENSE`

**Add file** → **Create new file** → nama: `LICENSE`

```

MIT License

Copyright (c) 2026 BalzyOffc

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```

> Ganti `BalzyOffc` dengan username GitHub kamu.

Commit changes.

---

### 📄 File 8: `.github/FUNDING.yml` (Opsional)

**Add file** → **Create new file** → nama: `.github/FUNDING.yml`

```yaml
# Kalau mau terima donasi
github: USERNAME

# Custom links (uncomment yang dipakai)
# custom: ['https://app.buatqris.site/donation/balzy']
