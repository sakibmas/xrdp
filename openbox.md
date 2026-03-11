```
apt-get -y install xrdp openbox x11-xserver-utils python3-xdg menu libsecret-1-0 libvte-2.91-0 thunar chromium-browser fonts-beng fonts-beng-extra
```
```
tee -a /etc/bash.bashrc << 'RCEOF'
# VTE shell integration with Tilix
if [ "${TILIX_ID}" ] || [ "${VTE_VERSION}" ]; then
  _vte_script=$(ls /etc/profile.d/vte-*.sh 2>/dev/null | sort -V | tail -n1)
  [ -f /etc/profile.d/vte.sh ] && source /etc/profile.d/vte.sh \
    || { [ -n "${_vte_script}" ] && source "${_vte_script}"; }
  unset _vte_script
fi
RCEOF
```
