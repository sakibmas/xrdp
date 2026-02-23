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
sed -i 's/#tcp_send_buffer_bytes=32768/tcp_send_buffer_bytes=4194304/g' /etc/xrdp/xrdp.ini | grep tcp_send_buffer_bytes
```
```
sed -i 's/#tcp_recv_buffer_bytes=32768/tcp_recv_buffer_bytes=4194304/g' /etc/xrdp/xrdp.ini | grep tcp_recv_buffer_bytes
```
```
usermod -aG ssl-cert xrdp
```
## Review
```
grep -v "^#\|^$\|^;" /etc/xrdp/xrdp.ini
```
```
```
