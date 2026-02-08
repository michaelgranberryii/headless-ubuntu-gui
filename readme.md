# Minimal “server + desktop” setup (pro move)
```bash
sudo apt install ubuntu-server
sudo apt install xfce4 xfce4-goodies lightdm
```

# Select lightdm, then press Enter.
Wait for gui selection

# Install the dummy Xorg driver
```bash
sudo apt update
sudo apt install xserver-xorg-video-dummy
```

# Create the Xorg dummy config
```bash
sudo nano /etc/X11/xorg.conf
```

### Paste exactly this (safe, minimal, 1080p):
```bash
Section "Device"
    Identifier "DummyDevice"
    Driver "dummy"
    VideoRam 256000
EndSection

Section "Monitor"
    Identifier "DummyMonitor"
    HorizSync 30-70
    VertRefresh 50-75
EndSection

Section "Screen"
    Identifier "DummyScreen"
    Monitor "DummyMonitor"
    Device "DummyDevice"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1920x1080"
    EndSubSection
EndSection
```

# Make sure Wayland is disabled (important)
```bash
sudo nano /etc/gdm3/custom.conf
```

### Ensure this line exists and is not commented:
```bash
WaylandEnable=false
```

# Reboot
```bash
sudo reboot
```
