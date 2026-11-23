# Block YouTube Shorts (AdGuard & uBlock Origin)

A continually maintained filter list to remove YouTube Shorts across desktop (`www.youtube.com`) and mobile web (`m.youtube.com`) for **AdGuard** and **uBlock Origin**.

YouTube frequently changes its DOM structure, breaking older blockers. This list tracks the latest layout updates to hide Shorts from the homepage, subscriptions, search, watch sidebar, playlists, channel tabs, and navigation menus—while keeping your Watch History intact.

## ⚙️ How to Install

### Option A: Subscribe to the List (Recommended)
Subscribing lets your blocker automatically pull future updates whenever YouTube changes its layout.

1. Open your blocker's custom filter lists:
   - **AdGuard:** Settings → **Filters** → **Custom Filters** → **Add Custom Filter**
   - **uBlock Origin:** Dashboard → **Filter lists** → scroll to **Custom** → check **Import**
2. Copy and paste this URL, then click **Apply / Subscribe**:

```text
https://raw.githubusercontent.com/raktimrabha/remove-youtube-shorts/main/remove-yt-shorts-filters.txt
```

### Option B: Quick Copy-Paste
1. Open your blocker's manual rules:
   - **AdGuard:** Settings → **User Rules**
   - **uBlock Origin:** Dashboard → **My Filters**
2. Expand the block below, click the **Copy** icon in the top-right corner, paste it in, and click **Apply / Save**.

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

## ✅ What Gets Blocked

| Area | Coverage |
| :--- | :--- |
| **Feeds & Shelves** | Home, Subscriptions, Channel pages, and Search Shorts shelves (including Remix shelves) |
| **Individual Videos** | Scattered Shorts in feeds, Watch sidebar recommendations, and playlists |
| **Navigation & UI** | Left sidebar & mini-guide links, filter chips, mobile bottom pivot bar, and channel Shorts tabs |
| **Direct Links (uBO)** | Redirects `/shorts/<id>` clicks to the standard `/watch?v=<id>` player via `$uritransform` |
| **Watch History** | Intentionally preserved (`/feed/history` is excluded from shelf hiding) |

## 📱 A Quick Note on Mobile
In addition to blocking Shorts on `m.youtube.com`, there is a helpful side effect: **using this filter on desktop for a few days reduces how often YouTube's algorithm pushes Shorts to you in the mobile app as well.**

## 🛠 Technical Details (November 2026)
- **Modern View-Models:** Targets YouTube's newer web components (`grid-shelf-view-model`, `yt-lockup-view-model`, `ytm-shorts-lockup-view-model`, `ytm-shorts-lockup-view-model-v2`, and `chip-bar-view-model`) alongside legacy renderers.
- **No Broken Grid Gaps:** Applies `:style(display: contents !important)` to `ytd-rich-grid-row` so remaining videos reflow cleanly when Shorts are removed.
- **History-Safe Path Matching:** Uses `:matches-path(/^(?!\/feed\/history).*$/)` so Watch History stays accessible.
- **Low False Positives:** Matches structural Shorts attributes and `/shorts/` links instead of broad text matching that could hide regular videos with "Shorts" in the title.

## 🤝 Contributing
If YouTube changes its layout and Shorts slip through, please open an Issue or submit a Pull Request with:
- Where the Short appeared (e.g., Home, Search, Watch sidebar, Mobile)
- Your blocker and browser (e.g., AdGuard / uBlock Origin)
