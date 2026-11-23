# Block YouTube Shorts (AdGuard Filters)

A continually updated list of AdGuard filters to completely remove YouTube Shorts from the desktop and mobile web interfaces. 

YouTube frequently updates its site structure, breaking older Adblock rules. This repository provides updated selectors that catch the new layout, removing Shorts from the homepage, subscriptions, search, sidebar menus, and related videos.

## ⚙️ How to Install

### Option A: Subscribe to the list (Recommended)
By subscribing, your AdGuard or uBlock Origin will automatically fetch any future updates.
1. Open **AdGuard** (**Filters** > **Custom Filters**) or **uBlock Origin** (**Filter lists** > **Import**).
2. Click the copy icon below and paste the raw filter list URL:

```text
https://raw.githubusercontent.com/raktimrabha/remove-youtube-shorts/main/remove-yt-shorts-filters.txt
```

### Option B: Quick Copy-Paste
1. Open **AdGuard** (**User Rules**) or **uBlock Origin** (**My Filters**).
2. Expand the block below, click the **Copy** icon in the top-right corner, paste it in, and click **Apply/Save**.

<details>
<summary><strong>Click to expand & copy the filters (Updated November 2026)</strong></summary>

```text
! --- 1. Layout & Grid Fixes ---
! Fix empty spaces left behind by blocked grids
www.youtube.com##ytd-rich-grid-row, #contents.ytd-rich-grid-row:style(display: contents !important)

! --- 2. Hide Shelves & Sections (Desktop) ---
! Catch elements strictly marked as shorts
youtube.com##[is-shorts]
! Hide Shorts shelves & sections everywhere except History
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-rich-section-renderer:has(ytd-rich-shelf-renderer[is-shorts], a[href^="/shorts/"], ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2)
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-reel-shelf-renderer
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)grid-shelf-view-model:has(a[href^="/shorts/"], ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2, .shortsLockupViewModelHost)
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-item-section-renderer:has(ytd-reel-shelf-renderer, ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2, grid-shelf-view-model:has(a[href^="/shorts/"]))

! --- 3. Hide Individual Scattered Shorts (Desktop) ---
! Catches Shorts masquerading as regular videos in feeds, sidebar, and playlists
www.youtube.com##ytd-video-renderer:has(a[href^="/shorts/"])
www.youtube.com##ytd-grid-video-renderer:has(a[href^="/shorts/"])
www.youtube.com##ytd-rich-item-renderer:has(a[href^="/shorts/"], ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2, [overlay-style="SHORTS"])
www.youtube.com##ytd-compact-video-renderer:has(a[href^="/shorts/"])
www.youtube.com##yt-lockup-view-model:has(a[href^="/shorts/"])
www.youtube.com##ytd-playlist-video-renderer:has(a[href^="/shorts/"])
www.youtube.com##ytd-playlist-panel-video-renderer:has(a[href^="/shorts/"])
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-shorts-lockup-view-model
www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-shorts-lockup-view-model-v2

! --- 4. Hide Search Results & Remixes ---
! Modern Search layout & Shorts Remix shelves
www.youtube.com##ytd-search grid-shelf-view-model:has(a[href^="/shorts/"], ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2, .shortsLockupViewModelHost)
www.youtube.com##ytd-reel-shelf-renderer:has(.yt-core-attributed-string:has-text(/(^| )Shorts.?Remix.*$/i))
www.youtube.com##grid-shelf-view-model:has(.yt-core-attributed-string:has-text(/(^| )Shorts.?Remix.*$/i))

! --- 5. Hide Tabs, Chips & Navigation (Desktop) ---
! Remove from sidebars, filter chips, and channel tabs
www.youtube.com###guide [title="Shorts"]
www.youtube.com##ytd-guide-entry-renderer:has(a[title="Shorts"])
www.youtube.com##ytd-guide-entry-renderer:has(yt-formatted-string:has-text(/^Shorts$/i))
www.youtube.com##.ytd-mini-guide-entry-renderer[title="Shorts"]
www.youtube.com##ytd-mini-guide-entry-renderer[aria-label="Shorts"]
www.youtube.com##ytd-mini-guide-entry-renderer:has(a[title="Shorts"])
www.youtube.com##yt-chip-cloud-chip-renderer:has(*:has-text(/^Shorts$/i))
www.youtube.com##chip-bar-view-model chip-view-model:has(*:has-text(/^Shorts$/i))
www.youtube.com##yt-tab-shape[tab-title="Shorts"]
www.youtube.com##yt-tab-shape:has-text(/^Shorts$/)
www.youtube.com##tp-yt-paper-tab[aria-label="Shorts"]

! --- 6. Redirect Accidental Clicks (uBlock Origin Only) ---
! Forces clicked Shorts to open in the normal video player
||youtube.com/shorts/*$uritransform=/shorts\/(.*)/watch\?v=\$1/

! --- 7. MOBILE (Algorithm Training & UI) ---
m.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-rich-section-renderer:has(ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2, a[href^="/shorts/"])
m.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-rich-section-renderer:has(.yt-core-attributed-string:has-text(/(^| )Shorts( |$)/i))
m.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytm-reel-shelf-renderer
m.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)grid-shelf-view-model:has(a[href^="/shorts/"], ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2)
m.youtube.com##ytm-rich-item-renderer:has(a[href^="/shorts/"], ytm-shorts-lockup-view-model, ytm-shorts-lockup-view-model-v2)
m.youtube.com##ytm-video-with-context-renderer:has(a[href^="/shorts/"], [data-style="SHORTS"])
m.youtube.com##ytm-compact-video-renderer:has(a[href^="/shorts/"])
m.youtube.com##ytm-rich-item-renderer:has(#video-title:has-text(/(^| )#Shorts?( |$)/i))
m.youtube.com##ytm-item-section-renderer:has(#video-title:has-text(/(^| )#Shorts?( |$)/i))
m.youtube.com##ytm-pivot-bar-item-renderer:has(.pivot-shorts)
m.youtube.com##ytm-chip-cloud-chip-renderer:has(.yt-core-attributed-string:has-text(/^Shorts$/i))
m.youtube.com##yt-tab-shape[tab-title="Shorts"]
m.youtube.com##yt-tab-shape:has-text(/^Shorts$/)
```

</details>

## 📱 A Quick Note on Mobile 
While these filters are mainly for the YouTube desktop webpage, there is a great side effect: **If you use this blocker on your PC for a few days, YouTube's algorithm actually stops pushing Shorts to you as frequently on the mobile app, too!**

## 🛠 2026 Updates (Technical Details)
* The new 2026 layout requires fixing empty spaces left behind by blocked grids using `:style(display: contents !important)`
* Hiding Shorts dynamically everywhere except the History page requires `:matches-path` filters.
* YouTube heavily relies on nested elements now, requiring AdGuard's extended CSS with `:has()` to force the blocker to check the specific Shorts link structure before hiding it.
* Mobile-specific rules targeting `m.youtube.com` have been added to stop algorithm training completely on mobile browsers.

## 🤝 Contributing
If YouTube changes its layout again and you notice Shorts leaking through, please open an Issue or submit a Pull Request!