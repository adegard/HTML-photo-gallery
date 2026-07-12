# Local Photo Gallery

A lightweight, single-file HTML photo gallery that browses your local photos directly in the browser using the [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API). No server required.

## Features

- **Local folder browsing** - Open any folder of photos organized as `YYYY/YYYY-MM/` (e.g., `2024/2024-06/photo.jpg`)
- **Year/month navigation** - Browse by year albums or dive into specific months
- **Lightbox viewer** - Full-screen view with zoom (0.5x-4x), keyboard navigation, and slideshow mode
- **Favorites** - Star/unstar photos, filter to view only favorites
- **Rotation** - Rotate individual photos or batch-rotate selected photos (stored per photo)
- **Search** - Filter photos by filename, year, or month
- **Albums** - Create named albums from selected photos; export/import album data as JSON
- **Batch selection** - Multi-select photos for bulk rotate, favorite, or hide operations
- **Stats** - View total photos, visible/hidden counts, favorites, busiest year, etc.
- **Cached thumbnails** - Uses the Cache API for fast repeat loads
- **Auto-reconnect** - Remembers your folder between sessions (permission re-prompted)

## Requirements

- A modern browser with File System Access API support (Chrome 86+, Edge 86+)
  - Firefox and Safari do **not** support this API
- **Mobile (Android/iOS)**: Works via file picker fallback — no special API needed

## Installation

1. Download or clone this repository:
   ```bash
   git clone https://github.com/adegard/HTML-photo-gallery.git
   ```
2. Open `gallery.html` directly in your browser:
   ```
   File > Open File > gallery.html
   ```
   Or simply double-click `gallery.html` in your file manager.

## Usage

1. Click **Open** in the header to select your root photo folder.
2. The folder must be organized as:
   ```
   photos/
   ├── 2024/
   │   ├── 2024-01/
   │   │   ├── img001.jpg
   │   │   └── img002.png
   │   └── 2024-06/
   │       └── vacation.webp
   └── 2023/
       └── 2023-12/
           └── holiday.jpg
   ```
3. Supported formats: **JPG**, **JPEG**, **PNG**, **WebP**
4. Use the toolbar to search, create albums, start a slideshow, or view stats.

### Mobile (Android / iOS)

- Tap **Open** and select your photo folder.
- **First run may take a while** if you have thousands of photos — the browser needs to scan every file. Subsequent opens are much faster thanks to caching.
- Android Chrome may not return all files at once for very large folders. If photos are missing, tap **Open** again and re-select the same folder — each tap accumulates more photos until everything is found.
- Swipe left/right in the lightbox to navigate between photos.
- Tap **Clear** to reset cached data and start fresh.

### Keyboard Shortcuts (Lightbox)

| Key | Action |
|-----|--------|
| `←` / `→` | Previous / Next photo |
| `F` | Toggle favorite |
| `Delete` | Hide photo from gallery |
| `Esc` | Close lightbox / stop slideshow |

### Notes

- **Delete** is a soft-delete (hides from gallery only). Original files on disk are never touched.
- Favorites, rotations, and hidden state are saved in `localStorage` per browser.
- Albums can be exported as JSON and imported on another browser/device.
