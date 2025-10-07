# 🚀 Panduan Setup 3proxy di VPS Ubuntu (SOCKS5 Proxy + UFW)

Panduan ini membantu kamu menginstal dan mengonfigurasi **3proxy** di VPS Ubuntu untuk membuat **SOCKS5 proxy server** yang aman dan mudah digunakan.

---

## ⚙️ 1. Install 3proxy
```bash
sudo apt update && sudo apt install 3proxy -y
```

---

## 🧩 2. Edit Konfigurasi
Buka file konfigurasi:
```bash
sudo nano /etc/3proxy/3proxy.cfg
```

Isi dengan konfigurasi berikut:
```bash
auth strong
users celengspeed:CL:celengspeed
allow celengspeed
socks -p1080 -a -i0.0.0.0 -e0.0.0.0
```

---

## 🔁 3. Restart Service
```bash
sudo systemctl restart 3proxy
sudo systemctl status 3proxy
```

---

## 🔥 4. Buka Firewall (UFW)
```bash
sudo ufw allow 1080/tcp
sudo ufw allow 1080/udp
sudo ufw reload
sudo ufw status
```

---

## 🧪 5. Test Lokal (di VPS)
```bash
curl -x socks5h://celengspeed:celengspeed@127.0.0.1:1080 https://api.ipify.org
```

---

## 🌐 6. Test Remote (dari PC / server lain)
```bash
curl -x socks5h://celengspeed:celengspeed@IP_VPS:1080 https://api.ipify.org
```

---

## 📝 7. Catatan
- Jika port `1080` diblokir ISP / provider, ganti ke port lain misalnya `2080`.
- Edit konfigurasi di:
  ```bash
  sudo nano /etc/3proxy/3proxy.cfg
  ```
  Ubah baris:
  ```bash
  socks -p2080 -a -i0.0.0.0 -e0.0.0.0
  ```
- Buka firewall untuk port baru:
  ```bash
  sudo ufw allow 2080/tcp
  sudo ufw allow 2080/udp
  ```
- Lalu restart service:
  ```bash
  sudo systemctl restart 3proxy
  ```

---

## 🧰 Informasi Tambahan
- 📂 Lokasi konfigurasi: `/etc/3proxy/3proxy.cfg`  
- 🧠 Default port: `1080`  
- 🔐 Autentikasi: Username & Password  
- 💡 Proxy Type: SOCKS5  

---

### ❤️ Dibuat oleh [VEZA](https://github.com/fckveza)
Jika panduan ini membantu, jangan lupa beri ⭐ di repo ini!
