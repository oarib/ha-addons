# 🧩 OArib — Home Assistant Add-ons

Welcome to my custom Home Assistant add-ons repository — built for performance, simplicity, and full Raspberry Pi (ARM64) compatibility.

---

## 📦 Available Add-ons

| Add-on         | Description                                   | Architecture |
|----------------|-----------------------------------------------|--------------|
| **HyperHDR**   | Next-gen Ambilight system for your setup      | `aarch64`    |

---

## 🚀 How to Add This Repository to Home Assistant

1. Open **Home Assistant**
2. Go to **Settings → Add-ons → Add-on Store**
3. Click the **three dots (⋮)** in the top-right → **Repositories**
4. Add this URL:

```
https://github.com/oarib/ha-addons
```

5. Click **HyperHDR** from the list to install it 🎉

---

## 🔁 Auto-Update Powered by GitHub Actions

This repository is fully automated:

- 🔄 Clones the latest [HyperHDR](https://github.com/awawa-dev/HyperHDR) code daily
- 🛠 Builds a multi-arch Docker image (`aarch64`)
- 🚀 Pushes to [Docker Hub](https://hub.docker.com/u/obaida)

You always get the freshest version, no manual work needed ✅
