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
gsettings set org.gnome.desktop.session idle-delay 600
```

## Review
```
grep -v "^#\|^$\|^;" /etc/xrdp/xrdp.ini
```
```
sysctl net.core.rmem_max
sysctl net.core.wmem_max
sysctl net.ipv4.tcp_rmem
sysctl net.ipv4.tcp_wmem
```
## Restart
```
sudo systemctl restart xrdp xrdp-sesman
```
