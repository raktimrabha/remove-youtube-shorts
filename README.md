# Block YouTube Shorts (AdGuard Filters)

A continually updated list of AdGuard filters to completely remove YouTube Shorts from the desktop and mobile web interfaces. 

YouTube frequently updates its site structure, breaking older Adblock rules. This repository provides updated selectors that catch the new layout, removing Shorts from the homepage, subscriptions, search, sidebar menus, and related videos.

## 📱 A Quick Note on Mobile 
While these filters are mainly for the YouTube desktop webpage, there is a great side effect: **If you use this blocker on your PC for a few days, YouTube's algorithm actually stops pushing Shorts to you as frequently on the mobile app, too!**

## 📝 The Filters (Updated March 2026)
```text
! --- 1. Layout & Grid Fixes ---
! Fix empty spaces left behind by blocked grids
www.youtube.com##ytd-rich-grid-row,#contents.ytd-rich-grid-row:style(display: contents !important)

! --- 2. Hide Shelves & Sections (Updated for March 2026) ---
! Hide dedicated Shorts shelves (using custom attribute)
youtube.com##[is-shorts]
! Hide Shorts sections everywhere except History
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-rich-section-renderer:has(a[href^="/shorts/"])
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-reel-shelf-renderer:has(a[href^="/shorts/"])

! --- 3. Hide Individual Scattered Shorts ---
! Catches Shorts masquerading as regular videos
youtube.com##ytd-video-renderer:has(a[href*="/shorts/"])
youtube.com##ytd-grid-video-renderer:has(a[href*="/shorts/"])
youtube.com##ytd-rich-item-renderer:has(a[href*="/shorts/"])
youtube.com##ytd-compact-video-renderer:has(a[href*="/shorts/"])

! --- 4. Hide Search Results & Remixes ---
! The new 2026 Search page layout
www.youtube.com##ytd-search grid-shelf-view-model:has(a[href^="/shorts/"])
! Hide short remixes
www.youtube.com##ytd-reel-shelf-renderer:has(#title:has-text(/(^| )Shorts.?Remix.*$/i))

! --- 5. Hide Tabs, Chips & Navigation ---
www.youtube.com##ytd-guide-entry-renderer:has(yt-formatted-string:has-text(/^Shorts$/i))
www.youtube.com##ytd-mini-guide-entry-renderer:has(.title:has-text(/^Shorts$/i))
www.youtube.com##yt-chip-cloud-chip-renderer:has(*:has-text(/^Shorts$/i))
www.youtube.com##yt-tab-shape:has-text(/^Shorts$/)

! --- MOBILE (Algorithm Training) ---
m.youtube.com##ytm-rich-item-renderer:has(#video-title:has-text(/(^| )#Shorts?( |$)/i))
m.youtube.com##ytm-item-section-renderer:has(#video-title:has-text(/(^| )#Shorts?( |$)/i))
m.youtube.com##ytm-pivot-bar-item-renderer:has(.pivot-shorts)
m.youtube.com##ytm-video-with-context-renderer:has([data-style="SHORTS"])
m.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-rich-section-renderer:has(.yt-core-attributed-string:has-text(/(^| )Shorts( |$)/i))
m.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-reel-shelf-renderer.item:has(.reel-shelf-title-wrapper .yt-core-attributed-string:has-text(/(^| )Shorts( |$)/i))
m.youtube.com##ytm-reel-shelf-renderer:has(.reel-shelf-title-wrapper .yt-core-attributed-string:has-text(/(^| )Shorts.?Remix.*$/i))
m.youtube.com##ytm-chip-cloud-chip-renderer:has(.yt-core-attributed-string:has-text(/^Shorts$/i))
m.youtube.com##ytm-reel-shelf-renderer:has(ytm-shorts-lockup-view-model)
m.youtube.com##yt-tab-shape:has-text(/^Shorts$/)
```

## ⚙️ How to Install

### Option A: Subscribe to the list (Recommended)
By subscribing, your AdGuard will automatically fetch any future updates I make to these filters.
1. Open AdGuard settings.
2. Go to **Filters** > **Custom Filters** (or **Add Custom Filter**).
3. Paste the raw URL of the text file:
   `https://raw.githubusercontent.com/raktimrabha/remove-youtube-shorts/main/remove-yt-shorts-filters.txt`

### Option B: Manual Copy-Paste
1. Open AdGuard settings.
2. Go to **User Rules**.
3. Copy the contents of `remove-yt-shorts-filters.txt` and paste them into the box.
4. Click Apply/Save.

## 🛠 2026 Updates (Technical Details)
* The new 2026 layout requires fixing empty spaces left behind by blocked grids using `:style(display: contents !important)`
* Hiding Shorts dynamically everywhere except the History page requires `:matches-path` filters.
* YouTube heavily relies on nested elements now, requiring AdGuard's extended CSS with `:has()` to force the blocker to check the specific Shorts link structure before hiding it.
* Mobile-specific rules targeting `m.youtube.com` have been added to stop algorithm training completely on mobile browsers.

## 🤝 Contributing
If YouTube changes its layout again and you notice Shorts leaking through, please open an Issue or submit a Pull Request!