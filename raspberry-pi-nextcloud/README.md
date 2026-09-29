# ☁️ Self-Hosted Nextcloud — Raspberry Pi 5

I built a **self-hosted cloud server** on a Raspberry Pi 5 as part of my homelab.

The goal was to create my own private cloud for **file storage and future homelab services**.

---

## 🖥️ Hardware

* **Raspberry Pi 5**
* **Raspberry Pi OS**
* **3TB External HDD**
* Raspberry Pi SD card
* Fedora workstation for remote administration

---

## ⚙️ Setup

I started with a fresh installation of Raspberry Pi OS and configured the Pi remotely from my Fedora workstation using **SSH**.

I then:

* Configured SSH access
* Connected the 3TB external HDD
* Mounted and configured persistent storage
* Installed and configured Nextcloud
* Set up MariaDB
* Configured the web server and PHP
* Troubleshot filesystem permissions and storage issues

---

## Final Architecture

After experimenting with a traditional installation, I rebuilt the environment using **Docker**.

```text
                    ┌─────────────────────┐
                    │    Fedora Laptop    │
                    │   Remote via SSH    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Raspberry Pi 5   │
                    │                     │
                    │   ┌─────────────┐   │
                    │   │  Nextcloud  │   │
                    │   │   Docker    │   │
                    │   └──────┬──────┘   │
                    │          │           │
                    │   ┌──────▼──────┐   │
                    │   │   MariaDB   │   │
                    │   │  SD Card    │   │
                    │   └─────────────┘   │
                    │                     │
                    │   ┌─────────────┐   │
                    │   │    3TB HDD  │   │
                    │   │ File Storage│   │
                    │   └─────────────┘   │
                    └─────────────────────┘
```

### Storage

The final setup uses:

| Component       | Storage          |
| --------------- | ---------------- |
| Raspberry Pi OS | SD Card          |
| MariaDB         | SD Card          |
| Nextcloud files | 3TB External HDD |

---

## Problems I Encountered

During the project, I ran into several issues while building and rebuilding the environment:

* Boot device configuration
* Apache configuration
* MariaDB setup
* PHP version compatibility
* Docker containers
* Filesystem permissions
* exFAT storage limitations
* Nextcloud configuration

I eventually rebuilt the environment from scratch and moved to a **Docker-based deployment**, which gave me a cleaner final setup.

---

## ✅ Final Result

I now have a working **self-hosted Nextcloud server** running on my Raspberry Pi 5.

The system provides:

* ☁️ Private cloud storage
* 💾 3TB external storage
* 🐳 Docker-based deployment
* 🗄️ MariaDB database
* 🔐 Remote administration through SSH
* 🌐 Web-based access

---

> **Project status: Running successfully ✅**
