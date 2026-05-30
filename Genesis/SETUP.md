# Deployment Guide — genesis.garyanderson.net

## 1. Create a GitHub Repository

1. Go to https://github.com/new
2. Name it **genesis** (or anything you like)
3. Set it to **Public**
4. Click **Create repository**

## 2. Push these files

From this folder, run:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/genesis.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

## 3. Enable GitHub Pages

1. In your repo, go to **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose branch: `main`, folder: `/ (root)`
4. Click **Save**

GitHub will show you a URL like `https://YOUR_USERNAME.github.io/genesis` — but we'll override that with your custom subdomain.

## 4. Configure DNS

In your domain registrar (wherever garyanderson.net DNS is managed), add a **CNAME record**:

| Type  | Name    | Value                          |
|-------|---------|--------------------------------|
| CNAME | genesis | YOUR_USERNAME.github.io        |

> Replace `YOUR_USERNAME` with your actual GitHub username.

DNS changes typically propagate in 15–60 minutes (sometimes up to 24 hours).

## 5. Verify in GitHub Pages settings

1. Go back to **Settings → Pages** in your repo
2. Under **Custom domain**, type: `genesis.garyanderson.net`
3. Click **Save** — GitHub will verify the CNAME
4. Once verified, check **Enforce HTTPS** ✓

Your site will be live at **https://genesis.garyanderson.net** 🎉

---

## Adding Videos & Songs

Open `index.html` and find the `chapters` array near the top of the `<script>` block.

Each chapter has a `media: []` array. Add items like this:

### YouTube video
```js
{ type: "youtube", title: "Let There Be Light", description: "AI anthem for day one.", youtubeId: "YOUR_YOUTUBE_ID" }
```

### Local video file
```js
{ type: "video", title: "The Garden", description: "...", src: "media/ch2-garden.mp4" }
```

### Local audio/song
```js
{ type: "song", title: "In the Beginning", description: "...", src: "audio/ch1-beginning.mp3" }
```

### SoundCloud track
```js
{ type: "soundcloud", title: "Creation", description: "...", src: "https://soundcloud.com/YOUR_TRACK_URL" }
```

Put audio files in an `audio/` folder and video files in a `media/` folder, then commit and push.
