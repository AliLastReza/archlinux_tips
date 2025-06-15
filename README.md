# Arch Linux Tips And Tricks

Arch Linux Tips and Tricks

Content:
* [How to Disable the Motherboard Beep on Arch Linux (Blacklisting pcspkr)](#how-to-disable-the-motherboard-beep-on-arch-linux-blacklisting-pcspkr)

---

## How to Disable the Motherboard Beep on Arch Linux (Blacklisting pcspkr)

Sometimes, when you press backspace on an empty terminal line, your motherboard speaker beeps. This beep comes from the `pcspkr` kernel module. You can disable it by blacklisting the module so it doesn't load.

### Steps:

1. **Open a terminal.**

2. **Create a blacklist configuration file for the pcspkr module:**

```bash
echo "blacklist pcspkr" | sudo tee /etc/modprobe.d/nobeep.conf
```

This command writes a file named `nobeep.conf` with the line `blacklist pcspkr` inside `/etc/modprobe.d/`.

3. **Unload the pcspkr module immediately (optional):**

If you want to stop the beep without rebooting, run:

```bash
sudo rmmod pcspkr
```

If you get an error that the module is not loaded, it’s probably already off.

4. **Reboot your system (optional but recommended):**

```bash
sudo reboot
```

After reboot, the `pcspkr` module will not load, and the beep will be gone.

That’s it! You have disabled the annoying beep sound from your motherboard speaker.

