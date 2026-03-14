# 💬 ChatGPT Export Viewer

A free, offline, single-file tool to browse, search, and export your entire ChatGPT conversation history. One HTML file, 85 KB — no Python, no dependencies, no sign-ups. Open in browser, load your export folder. View conversations with images, audio playback, and full-text search. Export to PDF, HTML, Markdown, or RTF — single or bulk. 100% offline, zero external calls. Your data never leaves your computer.

![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)

---

## What is this?

When you download your data from ChatGPT (Settings → Data Controls → Export Data), you get a ZIP file full of JSON files that are impossible to read. This tool turns that raw export into a clean, searchable conversation viewer — right in your browser.

**Just open one HTML file. That's it.**

---

## Getting Started (No Coding Required)

### Step 1: Export your ChatGPT data

1. Go to [chat.openai.com](https://chat.openai.com)
2. Click your profile icon → **Settings** → **Data Controls** → **Export Data**
3. OpenAI will email you a download link (may take a few minutes to a few hours)
4. Download and **unzip** the file to a folder on your computer

### Step 2: Open the viewer

1. Download `chatgpt-viewer.html` from this repository
2. Double-click it to open in your browser (Chrome or Edge recommended)

### Step 3: Load your data

1. Click **Choose Folder**
2. Select the unzipped export folder
3. Your conversations will load automatically

That's it — you can now browse, search, and export all your ChatGPT conversations.

> **Tip:** The viewer remembers your last folder. Next time you open it, your conversations reload automatically (Chrome/Edge only).

---

## Features

### 📖 Conversation Browser

- **Sidebar list** of all conversations sorted by date, with message count and media indicators
- **Search** across all conversation titles and content
- **Sort** by date or message count (click once for descending, again for ascending, third click removes)
- **Filter** to show only conversations with images or audio
- **Light and dark theme** toggle

### 💬 Message Viewer

- Messages displayed in chat bubbles with role labels (**You** / **ChatGPT** / **System**)
- **Timestamps** on every message (Eastern Time, AM/PM)
- Full **Markdown rendering**: headers, bold, italic, code blocks, tables, blockquotes, lists
- **Images** displayed inline with click-to-zoom lightbox
- **Audio** playback for voice messages included in your export
- **Voice mode transcripts** shown as text when audio files aren't available

### 🔍 In-Chat Search

Open with **Ctrl+F** or the 🔍 button when viewing a conversation:

- **Text search**: type to find, matches highlighted in yellow, use ▲▼ or Enter/Shift+Enter to jump between matches
- **Image jump**: click 🖼️ to cycle through all images in the conversation
- **Audio jump**: click 🔊 to cycle through all audio clips

### 📤 Single Conversation Export

When viewing a conversation, use the buttons in the header:

| Format | What you get |
|--------|-------------|
| **.md** | Markdown file — great for pasting into notes or other AI tools |
| **.html** | Standalone webpage with embedded images and audio players |
| **.pdf** | PDF document with JPEG images embedded |
| **.rtf** | Rich text document that opens in Word, LibreOffice, Pages, Google Docs |

### 📦 Bulk Export

Click **↓ Export** in the sidebar header to export all conversations at once:

| Format | Description |
|--------|------------|
| **Export as .md** | ZIP of Markdown files — fastest export |
| **Export as .html** | ZIP of HTML files with embedded media |
| **Export as .pdf** | ZIP of PDF files |
| **Export as .rtf** | ZIP of RTF files for word processors |

- Progress bar shows export status
- **Cancel** button to stop at any time
- Files are numbered for easy sorting (00001, 00002, etc.)

---

## Privacy & Security

**Your data never leaves your computer.**

- ✅ Runs 100% offline in your browser
- ✅ Zero network requests — no servers, no tracking, no analytics
- ✅ No cookies, no local storage of your conversation data
- ✅ No external scripts or CDN dependencies
- ✅ Single HTML file — you can read every line of code

The only network-related feature is Chrome's File System Access API for remembering your folder location between sessions. This is a browser-local permission — no data is transmitted.

---

## ⚠️ Windows & macOS Security Warnings

### Windows SmartScreen (when opening the viewer)

When you first open `chatgpt-viewer.html`, Windows may show:

> **"Windows protected your PC"** — Microsoft Defender SmartScreen prevented an unrecognized app from starting.

1. Click **"More info"**
2. Click **"Run anyway"**

Or: Right-click the `.html` file → **Properties** → check **"Unblock"** → **OK**, then open it.

### Windows Security Warning (on exported files)

When you open exported files (`.pdf`, `.html`, `.rtf`) from a ZIP, Windows may block them:

> **"Windows found that this file is potentially harmful. To help protect your computer, Windows has blocked access to this file."**

**This is normal.** Windows marks all files extracted from downloaded ZIPs as "from the internet." Even unblocking individual files may not work — the security flag persists.

**The reliable fix — unblock the ZIP before extracting:**

1. Right-click the `.zip` file **before you extract it**
2. Click **Properties**
3. At the bottom, check **"Unblock"**
4. Click **OK**
5. **Now** extract the ZIP — all files inside will be clean

**If you already extracted:**

1. Create a **new folder** somewhere on your computer (e.g., Desktop)
2. **Copy** all files from the extracted folder into the new folder
3. The copies will not have the security block

**Alternative — disable the warning for a folder:**

1. Open **Windows Security** → **Virus & threat protection** → **Settings**
2. Under **Exclusions**, add the folder where you save your exports

### macOS Gatekeeper Warning

On Mac, you may see:

> **"chatgpt-viewer.html" can't be opened because it is from an unidentified developer.**

**How to open:**

1. Go to **System Preferences** → **Security & Privacy** → **General**
2. You'll see a message about the blocked file — click **"Open Anyway"**

**Or:** Right-click the file → **Open** → Click **Open** in the dialog. This bypasses Gatekeeper for that specific file.

### Why do these warnings appear?

Both Windows and macOS flag files that were downloaded from the internet — this is called "Mark of the Web" (MOTW) on Windows and Gatekeeper on Mac. When you download a ZIP and extract it, every file inside inherits this flag. This is an operating system security feature, not a problem with the viewer or your exports. The files are safe — they contain only text, images, and standard document formatting.

---

## Supported Export Formats

The viewer handles all known ChatGPT export structures:

- **Text messages** — all roles (user, assistant, system, tool)
- **Images** — user uploads, DALL-E generations, inline images
- **Audio** — voice messages from conversations (2024 format with `/audio/` folders)
- **Voice mode transcripts** — shown as text when audio files expired before export
- **Code blocks** — with syntax preservation
- **Citations** — ChatGPT's internal citation markers are automatically stripped
- **Multi-JSON exports** — all `conversations-*.json` files are merged and deduplicated

### Known Limitations

- **Voice mode audio (post-January 2025)**: ChatGPT stopped including voice audio files in exports. The transcript text is still shown.
- **PNG images in PDF export**: Only JPEG images are embedded in PDFs. PNG images show as text placeholders.
- **Very large exports**: Bulk HTML export with thousands of image-heavy conversations may use significant memory. Use the Cancel button if the browser becomes unresponsive.

---

## Browser Compatibility

| Browser | Status | Notes |
|---------|--------|-------|
| **Chrome** | ✅ Full support | Folder persistence on refresh |
| **Edge** | ✅ Full support | Folder persistence on refresh |
| **Firefox** | ✅ Works | No folder persistence (uses fallback file picker) |
| **Safari** | ⚠️ Partial | Folder picking may require individual file selection |

---

## Technical Details

For developers or the curious:

- **Single file**: ~80KB HTML file, zero dependencies, zero build step
- **Conversation tree walking**: Follows the `current_node` → parent chain to reconstruct the correct active conversation branch (handles edits, regenerations, and branches)
- **Audio matching**: Maps `sediment://` asset pointers to audio files using folder structure and `export_manifest.json`
- **PDF generator**: Custom binary PDF builder (MiniPDF class) with Helvetica fonts, JPEG image embedding, and Unicode normalization
- **RTF generator**: Native RTF output with font tables, color tables, embedded JPEG images, and Markdown-aware formatting
- **ZIP generator**: Custom ZIP builder with CRC32, streaming mode for large exports
- **No eval, no dynamic code**: All code is static and auditable

---

## License

MIT License

Copyright (c) 2026 Marcus Thraen

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
