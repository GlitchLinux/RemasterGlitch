# RemasterGlitch v1.0 Debian Package

<img width="244" height="249" alt="RemasterGlitch" src="https://github.com/user-attachments/assets/a3b81d4f-27b6-453b-8bf1-a1253e281512" />

## Build Information
- **Package Name:** remasterglitch
- **Version:** 1.0-amd64
- **Architecture:** amd64 (x86_64)
- **Size:** 15MB (includes bundled ISO files)
- **Built:** April 10, 2026

## Package Contents

```
/usr/bin/remasterglitch              - Launcher script
/usr/local/bin/remasterglitch        - Symlink (created on install)
/usr/share/remasterglitch/
  ├── remasterglitch.py              - Main application (PyQt5)
  ├── RemasterGlitch.png             - Application icon
  └── ISO-Hybrid-Base.tar.lzma       - Bundled ISO build files (NO DOWNLOAD NEEDED)
/usr/share/applications/
  └── remasterglitch.desktop         - Desktop entry for application menu
```

## What's Different from Source

✅ **Bundled ISO Files**
- `ISO-Hybrid-Base.tar.lzma` is included in the package
- Modified `remasterglitch.py` line 142 to use `/usr/share/remasterglitch/ISO-Hybrid-Base.tar.lzma`
- No external downloads required during build—much faster!

✅ **Proper Debian Structure**
- All files installed to standard Debian directories
- Launcher symlink to `/usr/local/bin/remasterglitch` for PATH access
- Desktop entry for graphical menu integration
- MD5 checksums for integrity verification

## Installation

```bash
sudo dpkg -i remasterglitch-1.0.deb
sudo apt-get install -f  # (if dependencies are missing)
```

## Dependencies (Automatically Installed)
- python3
- python3-tk
- xorriso
- squashfs-tools
- cpio, lzma, curl, rsync
- grub-pc-bin, grub-efi-amd64-bin
- mtools, dosfstools, util-linux

## Usage

**From command line:**
```bash
remasterglitch
# or
/usr/bin/remasterglitch
```

**From application menu:**
Search for "RemasterGlitch" in your application launcher

## Uninstall

```bash
sudo apt remove remasterglitch
# or
sudo dpkg -r remasterglitch
```

## File Locations After Install

| Path | Content |
|------|---------|
| `/usr/bin/remasterglitch` | Launcher (bash) |
| `/usr/share/remasterglitch/remasterglitch.py` | Main app (Python) |
| `/usr/share/remasterglitch/RemasterGlitch.png` | Icon |
| `/usr/share/remasterglitch/ISO-Hybrid-Base.tar.lzma` | ISO build files |
| `/usr/share/applications/remasterglitch.desktop` | Desktop entry |

## Key Improvements Over Manual Installation

1. **No Manual Downloads** - ISO files bundled in package
2. **Automatic Dependency Resolution** - apt handles all deps
3. **System Integration** - Desktop menu, symlink, proper paths
4. **Easy Uninstall** - `apt remove remasterglitch`
5. **Version Tracking** - Package manager knows installed version

## Build Details

**Modified for Debian:**
- `RemasterGlitch.py` → `remasterglitch.py` (lowercase, Unix convention)
- ISO fetch URL changed from GitHub to `/usr/share/remasterglitch/`
- All paths use standard FHS (Filesystem Hierarchy Standard)

**Package Control File:**
```
Package: remasterglitch
Version: 1.0-amd64
Architecture: amd64
Maintainer: Marcus <marcus@glitchlinux.com>
Depends: python3, python3-tk, xorriso, squashfs-tools, cpio, lzma, curl, rsync, grub-pc-bin, grub-efi-amd64-bin, mtools, dosfstools, util-linux
```

## Troubleshooting

**"remasterglitch: command not found"**
- Ensure `/usr/local/bin` is in your PATH: `echo $PATH`
- Or use full path: `/usr/bin/remasterglitch`

**Missing dependencies**
- Run: `sudo apt-get install -f`
- Or manually install: `sudo apt-get install python3 xorriso squashfs-tools ...`

**Permission denied on launcher**
- Package postinst should handle this, but verify:
  - `ls -l /usr/bin/remasterglitch` (should be `-rwxr-xr-x`)

---

**Distribution:** Ready for Debian 11+, Ubuntu 20.04+
**Maintenance:** Update version in DEBIAN/control for future releases
