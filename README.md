# SwiftBar USB Power Usage Monitor

A lightweight **SwiftBar** plugin that monitors USB power consumption on macOS in real time.

## Features

- Lists all connected USB devices drawing current (>0 mA), sorted from **highest to lowest** consumption.
- **Color-coded** usage levels:
  - 🔴 **Red**: 100% of available current
  - 🟠 **Orange**: 50–99% of available current
  - 🟢 **Green**: below 50% of available current
- **Menu bar icon**:
  - `USB ⚠️` → at least one device is at 100%
  - `USB ✅` → no devices at 100%
- **Summary line** in the dropdown:
  ```
  📊 X devices detected — Y at 100%
  ```

---

## Preview

**Menu Bar Icons:**
- Normal (no maxed-out devices):  
  `USB ✅`
- Warning (device(s) at 100% draw):  
  `USB ⚠️`

**Dropdown Example:**
```
📊 6 devices detected — 2 at 100%
Razer Huntsman Elite: 500/500 mA (100%) 🔴
Samsung T7 SSD: 896/900 mA (99%) 🟠
iLok Dongle: 40/500 mA (8%) 🟢
```

---

## Installation

1. **Download the script**  
   Save `usb_current.1m.py` to your SwiftBar plugins folder:
   ```
   ~/Library/Application Support/SwiftBar/plugins/
   ```

2. **Make it executable**  
   ```bash
   chmod +x ~/Library/Application\ Support/SwiftBar/plugins/usb_current.1m.py
   ```

3. **Launch SwiftBar**  
   - Ensure SwiftBar is running and the plugin folder is set correctly.
   - The `1m` in the filename means SwiftBar refreshes the plugin every **1 minute**.

---

## Requirements

- **macOS** (tested on macOS Ventura, Sonoma, Sequoia)
- **SwiftBar** → [Download here](https://swiftbar.app)
- Python 3.x (included in macOS)

---

## How it Works

The plugin runs:
```bash
system_profiler SPUSBDataType
```
It then:
1. Parses each device’s **Current Available (mA)** and **Current Required (mA)**.
2. Calculates the usage percentage.
3. Sorts devices by highest draw.
4. Displays the results with color-coded labels.

---

## Customization

- **Refresh interval** → Change `1m` in the filename to your desired interval (`.5m` for 30 seconds, `2m` for 2 minutes, etc.).
- **Color thresholds** → Edit the `if pct >= 100` / `elif 50 <= pct <= 99` rules in the script.

---

## License

MIT License — you are free to use, modify, and share.

---

## Credits

Developed for SwiftBar by parsing native `system_profiler` USB output.  
Inspired by real-world troubleshooting of high USB bus power draw on macOS.
