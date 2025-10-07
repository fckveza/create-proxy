Panduan Setup 3proxy di VPS Ubuntu (SOCKS5 Proxy + UFW)
1. Install 3proxy
-----------------
sudo apt update && sudo apt install 3proxy -y
2. Edit Konfigurasi
-------------------
sudo nano /etc/3proxy/3proxy.cfg
Isi dengan konfigurasi berikut:
auth strong
users celengspeed:CL:celengspeed
allow celengspeed
socks -p1080 -a -i0.0.0.0 -e0.0.0.0
3. Restart Service
------------------
sudo systemctl restart 3proxy
sudo systemctl status 3proxy
4. Buka Firewall (UFW)
----------------------
sudo ufw allow 1080/tcp
sudo ufw allow 1080/udp
sudo ufw reload
sudo ufw status
5. Test Lokal (di VPS)
-----------------------
curl -x socks5h://celengspeed:celengspeed@127.0.0.1:1080 https://api.ipify.org
6. Test Remote (dari PC / server lain)
--------------------------------------
curl -x socks5h://celengspeed:celengspeed@IP_VPS:1080 https://api.ipify.org
7. Catatan
----------
- Jika port 1080 diblokir ISP / provider, ganti ke port lain misalnya 2080.
- Konfigurasi ulang di /etc/3proxy/3proxy.cfg:
 socks -p2080 -a -i0.0.0.0 -e0.0.0.0
- Buka firewall juga:
 sudo ufw allow 2080/tcp
 sudo ufw allow 2080/udp
- Lalu restart service:
 sudo systemctl restart 3proxy
