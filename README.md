# Block YouTube Shorts (AdGuard Filters)

A continually updated list of AdGuard filters to completely remove YouTube Shorts from the desktop web interface. 

YouTube frequently updates its site structure, breaking older Adblock rules. This repository provides updated selectors that catch the new layout, removing Shorts from the homepage, subscriptions, search, sidebar menus, and related videos.

## 📱 A Quick Note on Mobile 
While these filters are mainly for the YouTube desktop webpage, there is a great side effect: **If you use this blocker on your PC for a few days, YouTube's algorithm actually stops pushing Shorts to you as frequently on the mobile app, too!**

## ⚙️ How to Install

### Option A: Subscribe to the list (Recommended)
By subscribing, your AdGuard will automatically fetch any future updates I make to these filters.
1. Open AdGuard settings.
2. Go to **Filters** > **Custom Filters** (or **Add Custom Filter**).
3. Paste the raw URL of the text file:
   `https://raw.githubusercontent.com/[YOUR-USERNAME]/[YOUR-REPO-NAME]/main/youtube-shorts-blocker.txt`

### Option B: Manual Copy-Paste
1. Open AdGuard settings.
2. Go to **User Rules**.
3. Copy the contents of `youtube-shorts-blocker.txt` and paste them into the box.
4. Click Apply/Save.

## 🛠 Why Old Rules Broke (Technical Details)
* YouTube added the `[is-shorts]` custom attribute for the dedicated homepage shelves.
* They heavily rely on `ytd-rich-item-renderer` now, requiring AdGuard's extended CSS with `:has(a[href*="/shorts/"])` to force the blocker to check for the specific Shorts link structure inside any grid item before hiding it.
* The sidebar navigation attributes changed, meaning `a[title="Shorts"]` is now nested differently and requires targeting the parent elements directly.

## 🤝 Contributing
If YouTube changes its layout again and you notice Shorts leaking through, please open an Issue or submit a Pull Request!