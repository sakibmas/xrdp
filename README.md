# Prerequisite
```
apt-get update
```
```
apt-get install gnome-core xrdp xauth fonts-beng fonts-indic rxvt-unicode -y
```
# Configure
```
cp /etc/xrdp/xrdp.ini{,.bak}
```

```
usermod -aG ssl-cert xrdp
```
## Optimize  
```
sed -i 's/#tcp_send_buffer_bytes=32768/tcp_send_buffer_bytes=0/g' /etc/xrdp/xrdp.ini
```
```
sed -i 's/#tcp_recv_buffer_bytes=32768/tcp_recv_buffer_bytes=0/g' /etc/xrdp/xrdp.ini
```
```
sed -i 's/max_bpp=32/max_bpp=24/g' /etc/xrdp/xrdp.ini
```
```
gsettings set org.gnome.desktop.interface enable-animations false
```
```
gsettings set org.gnome.desktop.background picture-uri ''
```
```
gsettings set org.gnome.desktop.background picture-uri-dark ''
```
```
gsettings set org.gnome.desktop.background primary-color '#000000'
```
```
gsettings set org.gnome.desktop.session idle-delay 600
```

## Review
```
grep -v "^#\|^$\|^;" /etc/xrdp/xrdp.ini | grep tcp
```
```
gsettings get org.gnome.desktop.interface enable-animations
```
```
gsettings get org.gnome.desktop.background picture-uri 
```
```
gsettings get org.gnome.desktop.background picture-uri-dark
```
```
gsettings get org.gnome.desktop.background primary-color
```
```
gsettings get org.gnome.desktop.session idle-delay
```
```
gsettings list-schemas | grep gnome.desktop
```
```
gsettings list-keys org.gnome.desktop.background
```
```
gsettings list-keys org.gnome.desktop.interface
```
```
sysctl net.core.rmem_max
```
```
sysctl net.core.wmem_max
```
```
sysctl net.ipv4.tcp_rmem
```
```
sysctl net.ipv4.tcp_wmem
```
## Restart
```
systemctl restart xrdp xrdp-sesman
```
## Troubleshooting
```
journalctl -xeu xrdp --no-pager --since="3 minutes ago"
```
```
if [ ! -f /var/log/xrdp.log ]; then
    touch /var/log/xrdp.log
    chown xrdp:xrdp /var/log/xrdp.log
fi
```
```
systemctl stop xrdp xrdp-sesman
```
```
truncate -s 0 /var/log/xrdp.log
```
```
systemctl start xrdp xrdp-sesman
```
```
systemctl status xrdp --no-pager -l
```





