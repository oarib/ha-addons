# 💡📺 HyperHDR Add-on for Home Assistant

Run **HyperHDR** — a powerful Ambilight system — directly on your Home Assistant OS!  
Perfect for DIY enthusiasts using Raspberry Pi + addressable LEDs.

---

## ✨ Features

- ✅ Based on the latest stable [HyperHDR](https://github.com/awawa-dev/HyperHDR)
- 🐳 Lightweight and precompiled for ARM64 (Raspberry Pi 4/5)
- 🎨 LED ambient lighting effects powered by real-time HDMI capture
- 🧠 Works with WLED controllers, grabbers, SK6812/WS2812 strips, and more

---

## 🧰 Recommended Hardware

- Raspberry Pi 4 (or better)
- Addressable LED strip (SK6812, WS2812, etc.)
- ESP32 controller running WLED
- Optional: HDMI splitter, video grabber, 5V power supply

---

## 🌐 Access the HyperHDR Web UI

Once installed, open:

```
http://<homeassistant-ip>:8090
```

Use your Home Assistant device IP or `homeassistant.local`.

---

## 🐳 Docker Image

This add-on pulls the latest image from Docker Hub:

👉 [obaida/hyperhdr-aarch64](https://hub.docker.com/r/obaida/hyperhdr-aarch64)

Built automatically via GitHub Actions.

[![HyperHDR logo](https://raw.githubusercontent.com/oarib/ha-addons/refs/heads/master/addon-hyperhdr/logo.png)](https://www.hyperhdr.eu/)
