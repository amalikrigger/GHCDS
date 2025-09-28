# Phase 2: Raspberry Pi SSH & Auto-WiFi Setup Assignment

## Objective

Enable SSH on your Raspberry Pi and configure it to automatically connect to the `GHCDS` Wi-Fi network. Then, from another computer on the same network, successfully SSH into the Pi using its hostname or IP address.

## Why This Matters

SSH allows you to control your Raspberry Pi remotely from another computer without needing a monitor, keyboard, or mouse attached. This is an essential step in working with your Pi as a headless device.

## Tasks & Steps

### 1. Enable SSH

- On the Pi desktop: open **Raspberry Pi Configuration → Interfaces → Enable SSH**.
- Or in Terminal, run:
  ```bash
  sudo raspi-config
  ```
  Go to *Interface Options → SSH → Enable*.
- Reboot if prompted.

### 2. Configure Auto-WiFi

- Open the Wi-Fi configuration file:
  ```bash
  sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
  ```
- Add this block (if it is not already there):
  ```
  network={
    ssid="GHCDS"
    key_mgmt=NONE
  }
  ```
- Save with **Ctrl+O, Enter** and exit with **Ctrl+X**.
- Reboot to confirm that the Pi reconnects automatically to `GHCDS`.

### 3. Find the Hostname and IP

- Default hostname: `raspberrypi`.
- To check the current IP address, run:
  ```bash
  hostname -I
  ```
- Write this down. Note that the IP may change after each reboot, so always check before connecting.

### 4. SSH into the Pi

- On another computer connected to `GHCDS`, open Terminal.
- Connect by hostname (if supported):
  ```bash
  ssh pi@raspberrypi.local
  ```
- Or connect by IP (replace with your Pi’s actual IP):
  ```bash
  ssh pi@192.168.x.x
  ```
- Enter the password: **raspberry** (unless changed during setup).

### 5. Verify Connection

- Once logged in, run a command such as:
  ```bash
  uname -a
  ```
- Confirm that you see system information from the Pi.
- Exit the session by typing:
  ```bash
  exit
  ```

## Deliverables

- A screenshot of your Terminal showing a successful SSH login (with the Pi prompt visible).
- The hostname or IP address you used to connect (e.g., `pi@raspberrypi.local` or `pi@192.168.1.50`).
- A screenshot of a command output (such as `uname -a`) while connected to the Pi.

