# Proxmox VE (Trixie) — No-Subscription Repo Fix & System Update

This guide switches Proxmox from **enterprise** repositories (subscription required) to **no-subscription** repositories and performs a full system update via shell.

---

## 🖥 Requirements

- Proxmox VE 8.x (Debian 12 *Trixie*)
- Shell or SSH access as `root`

---

## 📂 Step-1 — Disable Enterprise Repository

```bash
nano /etc/apt/sources.list.d/pve-enterprise.list
Comment the enterprise repo line:

# deb https://enterprise.proxmox.com/debian/pve trixie pve-enterprise


Save & exit:

CTRL + O
ENTER
CTRL + X

📂 Step-2 — Disable Enterprise Ceph Repo (Optional)
nano /etc/apt/sources.list.d/ceph.list


Comment:

# deb https://enterprise.proxmox.com/debian/ceph-squid trixie enterprise


Save & exit:

CTRL + O
ENTER
CTRL + X

📂 Step-3 — Add Debian + No-Subscription Repositories
nano /etc/apt/sources.list


Add the following lines:

deb http://deb.debian.org/debian trixie main contrib
deb http://deb.debian.org/debian trixie-updates main contrib
deb http://security.debian.org/debian-security trixie-security main contrib

deb http://download.proxmox.com/debian/pve trixie pve-no-subscription


Save & exit:

CTRL + O
ENTER
CTRL + X

🔄 Step-4 — Refresh Package Index
apt update

🚀 Step-5 — Upgrade System Packages
apt full-upgrade -y

🔁 Step-6 — Reboot (If Kernel Updated)
reboot

🧾 Step-7 — Validate Proxmox Version
pveversion -v

🧹 (Optional) Clean Old Packages
apt autoremove --purge -y

✔ Compatibility
Component	Status
Proxmox 8.x	✅
Debian Trixie (12)	✅
No-Subscription Setup	✅
Enterprise Subscription	❌ Not required
Notes



---

If you want:

✔ **actual `.md` file download**  
✔ turn into **GitHub repo**  
✔ add screenshots / badges  
✔ add Bengali version  

Tell me which one 👍
