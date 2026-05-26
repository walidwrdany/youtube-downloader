

# 🎬 YouTube Downloader Script

A powerful, user-friendly batch script for downloading videos and audio from YouTube using yt-dlp. Supports playlists, multiple quality options, subtitles, and more.

## ✨ Features

- 📥 **Download Videos** - Up to 4K quality with automatic format selection
- 🎵 **Audio Extraction** - Convert videos to MP3/M4A/Opus with quality control
- 📁 **Playlist Support** - Download entire playlists with sequential numbering
- 🔢 **Partial Playlists** - Download specific ranges (1:10, 5,10-15, etc.)
- 🌐 **Multi-Language Subtitles** - Arabic first, English fallback
- 🚀 **Fast Downloads** - Multi-threaded downloads with aria2 support
- 🔄 **Resume Capable** - Never re-download completed files
- 🎨 **Embedded Metadata** - Thumbnails, descriptions, and chapters
- 🔒 **Age-Restricted Content** - Cookie support for authenticated access
- 📝 **SponsorBlock Integration** - Automatically skip sponsored segments
- ✅ **Auto-Watch Marking** - Marks videos as watched on YouTube

## 📋 Prerequisites

### Required
- **Windows 10/11** (64-bit)
- **Administrator privileges** (for installation)

### Automatic Installation
Run the installer script (option 4) to automatically install:
- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - Core downloader
- [ffmpeg](https://ffmpeg.org/) - Video/audio processing
- [aria2](https://aria2.github.io/) - Accelerated downloads

### Optional (Recommended)
- [Node.js](https://nodejs.org/) - Better YouTube compatibility (solves n-challenge)

### Cookie Setup (For Age-Restricted Content)
1. Install [Get cookies.txt LOCALLY](https://chrome.google.com/webstore/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc) extension
2. Log into YouTube in your browser
3. Click the extension icon → Export cookies
4. Save as `cookies.txt` in the script directory

## 🚀 Quick Start

### Method 1: Using the Script (Recommended)

```batch
# Clone or download the script
git clone https://github.com/walidwrdany/youtube-downloader.git
cd youtube-downloader

# Run as Administrator (right-click → Run as Administrator)
youtube-dl.bat
```

### Method 2: Direct Command Line

```batch
# Download single video (best quality up to 720p)
yt-dlp -f "bestvideo[height<=720]+bestaudio/best" "URL"

# Download playlist with sequential numbering
yt-dlp -o "%%(uploader)s/%%(playlist_title)s/%%(playlist_index)03d - %%(title)s.%%(ext)s" "PLAYLIST_URL"

# Extract audio as MP3
yt-dlp -f bestaudio --extract-audio --audio-format mp3 "URL"
```

## 📖 Usage Guide

### Main Menu Options

| Option | Description |
|--------|-------------|
| **1** | Download Video (MP4 format) |
| **2** | Download Audio Only (MP3/M4A/Opus) |
| **3** | Update yt-dlp to latest version |
| **4** | Install/Update dependencies |
| **5** | Show help and documentation |
| **6** | Exit script |

### Video Download Examples

```batch
# Single video, 720p quality
Option 1 → URL: https://youtube.com/watch?v=... → Quality: 720

# Playlist, download videos 1-10
Option 1 → URL: https://youtube.com/playlist?list=... → Range: 1:10 → Quality: 1080

# Playlist, download specific items
Option 1 → URL: https://youtube.com/playlist?list=... → Range: 1,3,5,10-15 → Quality: 2160

# Best available quality
Option 1 → URL: https://youtube.com/watch?v=... → Quality: auto
```

### Audio Download Examples

```batch
# Single video to MP3 (best quality)
Option 2 → URL: https://youtube.com/watch?v=... → Format: mp3 → Quality: 0

# Playlist to M4A (good quality)
Option 2 → URL: https://youtube.com/playlist?list=... → Format: m4a → Quality: 5

# Entire channel to Opus (worst quality, small size)
Option 2 → URL: https://youtube.com/@channel → Format: opus → Quality: 9
```

## 📁 Output Structure

### Video Downloads
```
Current Directory/
├── UploaderName/
│   ├── Single Video Title.mp4
│   └── Playlist Name/
│       ├── 001 - First Video.mp4
│       ├── 002 - Second Video.mp4
│       └── 003 - Third Video.mp4
```

### Audio Downloads
```
Current Directory/
├── Audio/
│   └── UploaderName/
│       ├── Song Title.mp3
│       └── Album Name/
│           ├── 001 - Track 1.mp3
│           ├── 002 - Track 2.mp3
│           └── 003 - Track 3.mp3
```

### System Files
```
youtube-dl-directory/
├── youtube-dl.bat          # Main script
├── archive.txt             # Download history (prevents re-downloads)
├── cookies.txt             # YouTube cookies (for age-restricted content)
├── config/                 # Temporary config files (auto-generated)
└── logs/                   # Download logs (auto-generated)
```

## ⚙️ Configuration Options

### Quality Settings

| Quality | Resolution | Best For |
|---------|------------|----------|
| 2160p   | 3840x2160  | 4K displays, archiving |
| 1080p   | 1920x1080  | Full HD, general use |
| **720p**| 1280x720   | **Default - Best balance** |
| 480p    | 854x480    | Mobile devices, slow connections |
| 360p    | 640x360    | Very slow connections |
| auto    | Best available | Maximum quality |

### Audio Quality

| Quality | Bitrate | Use Case |
|---------|---------|----------|
| 0 (best) | ~320kbps | Archival, Hi-Fi listening |
| 5 (default) | ~128kbps | General listening |
| 9 (worst) | ~64kbps | Podcasts, voice-only |

## 🛠️ Advanced Features

### SponsorBlock Integration
The script automatically skips:
- 💰 Sponsorship segments
- 📢 Self-promotion content
- 🎬 Intros/Outros
- 🎵 Music off-topic sections
- ⏱️ Filler content

### Cookie Support (Age-Restricted Content)
```batch
# Automatic detection - just place cookies.txt in script folder
# Script will detect and use it automatically
```

### Resume Downloads
```batch
# Archive.txt tracks all completed downloads
# Re-run the same URL to skip already downloaded files
# Perfect for interrupted playlist downloads
```

### Sequential Playlist Numbering
All playlists use 3-digit numbering (001, 002, 003...) for proper sorting in file explorers.

## 🐛 Troubleshooting

### Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| **"n challenge solving failed"** | Install Node.js or use iOS client (built-in) |
| **"Requested format not available"** | Choose lower quality or use "auto" option |
| **Age-restricted content fails** | Export cookies.txt from logged-in browser |
| **Slow download speeds** | Install aria2 (option 4) |
| **"ffmpeg not found"** | Run option 4 to install dependencies |
| **Playlist numbering wrong** | Use option 1 (video) or 2 (audio) - not direct yt-dlp |

### Windows-Specific Issues

```batch
# If script closes immediately:
1. Right-click youtube-dl.bat
2. Select "Run as Administrator"
3. Or open CMD as Admin and run manually

# If Unicode characters don't display:
Run: chcp 65001
Then run script again
```

### Cookie Export Troubleshooting

```batch
# Brave/Chrome cookies fail with "DPAPI" error?
1. Close browser completely
2. Re-export cookies (must be closed during export)
3. Or use Firefox (no encryption issues)

# Still failing?
Use manual export with "Get cookies.txt LOCALLY" extension
Cookies work even with browser open
```

## 📝 Script Internals

### Key Configuration Parameters

```batch
# Format selection (simplified from script)
--format "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]/bestvideo[height<=720]+bestaudio/best"

# Output template (with playlist support)
--output "%(uploader)s/%(playlist_title)s/%(playlist_index)03d - %(title)s.%(ext)s"

# iOS client (bypasses n-challenge)
--extractor-args "youtube:player_client=ios"

# Archive (prevents re-downloads)
--download-archive archive.txt
```

### Environment Variables
```batch
YTDLP_EXE=yt-dlp.exe      # Path to yt-dlp executable
FFMPEG_EXE=ffmpeg.exe     # Path to ffmpeg executable
DOWNLOAD_DIR=%CD%         # Current directory
ARCHIVE_FILE=archive.txt  # Download history
COOKIES_FILE=cookies.txt  # Authentication cookies
```

## 🔄 Updates & Maintenance

### Automatic Updates
```batch
# From script menu
Option 3 → Update yt-dlp

# Manual update
yt-dlp -U
```

### Manual Update Process
```batch
# Update all components
Option 4 → Reinstall dependencies

# Or manually via Chocolatey
choco upgrade yt-dlp ffmpeg aria2 -y
```

## 📊 Performance Tips

### Maximize Download Speed
1. **Install aria2** (option 4) - 2-3x faster downloads
2. **Remove rate limiting** - Script has no limits by default
3. **Use concurrent fragments** - Built-in (5 fragments)
4. **Download during off-peak hours**

### Minimize Bandwidth Usage
```batch
# Limit download speed (add to script)
--limit-rate 1M

# Download lower quality
Quality: 360p

# Audio only
Option 2 → Audio download
```

## 🤝 Contributing

### Reporting Issues
When reporting issues, always include:
1. **Verbose log** - Add `--verbose` to see details
2. **URL being downloaded**
3. **Selected options** (video/audio, quality, range)
4. **yt-dlp version** (shown at script start)

### Feature Requests
Open an issue with:
- Clear description of the feature
- Why it would be useful
- Any relevant examples



## 🙏 Acknowledgments

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - The amazing downloader that powers this script
- [ffmpeg](https://ffmpeg.org/) - Multimedia framework
- [aria2](https://aria2.github.io/) - High-speed download utility
- [Chocolatey](https://chocolatey.org/) - Windows package manager

## ⚠️ Disclaimer

This tool is for educational purposes only. Respect copyright laws and YouTube's Terms of Service. Only download content you have permission to download.

---

## 🎯 Quick Reference Card

```batch
# Most Common Commands (for manual yt-dlp use)

# Download video (720p)
yt-dlp -f "best[height<=720]" "URL"

# Download playlist (numbered)
yt-dlp -o "%%(playlist_index)03d - %%(title)s.%%(ext)s" "PLAYLIST_URL"

# Download audio (MP3)
yt-dlp -f bestaudio --extract-audio --audio-format mp3 "URL"

# Use cookies (age-restricted)
yt-dlp --cookies cookies.txt "URL"
```

---
**Need help?** Run the script and select Option 5 for built-in help!

**Found a bug?** Run with `--verbose` and copy the output when reporting issues.
