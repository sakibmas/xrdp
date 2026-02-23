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
sed -i 's/#tcp_send_buffer_bytes=32768/tcp_send_buffer_bytes=4194304/g' /etc/xrdp/xrdp.ini
```
```
sed -i 's/#tcp_recv_buffer_bytes=32768/tcp_recv_buffer_bytes=4194304/g' /etc/xrdp/xrdp.ini
```
```
usermod -aG ssl-cert xrdp
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
