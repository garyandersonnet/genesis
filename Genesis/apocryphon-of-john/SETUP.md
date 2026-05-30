# Deployment Guide — apocryphon-of-john.garyanderson.net

## 1. Create a GitHub Repository

1. Go to https://github.com/new
2. Name it **apocryphon-of-john**
3. Set it to **Public**
4. Click **Create repository**

## 2. Push these files

```bash
cd path/to/apocryphon-of-john
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/apocryphon-of-john.git
git push -u origin main
```

## 3. Enable GitHub Pages

1. Go to **Settings → Pages**
2. Source: **Deploy from a branch**, branch: `main`, folder: `/ (root)`
3. Click **Save**

## 4. Configure DNS

In your domain registrar, add:

| Type  | Name                 | Value                     |
|-------|----------------------|---------------------------|
| CNAME | apocryphon-of-john   | YOUR_USERNAME.github.io   |

## 5. Set Custom Domain in GitHub Pages

1. **Settings → Pages → Custom domain**: type `apocryphon-of-john.garyanderson.net`
2. Click **Save**, wait for DNS verification
3. Check **Enforce HTTPS** ✓

---

## Adding Videos & Songs

Open `index.html`, find the `chapters` array in the `<script>` block.
Each chapter has `media: []`. Add items:

```js
// YouTube
{ type: "youtube", title: "The Invisible Spirit", description: "...", youtubeId: "YOUR_ID" }

// Local audio
{ type: "song", title: "Barbelo", description: "...", src: "audio/barbelo.mp3" }

// Local video
{ type: "video", title: "Yaldabaoth", description: "...", src: "media/yaldabaoth.mp4" }

// SoundCloud
{ type: "soundcloud", title: "Pronoia Hymn", description: "...", src: "https://soundcloud.com/YOUR_URL" }
```
