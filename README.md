# Archlinux Image Builder - `aib`

All cool, but **How can I build my system using `aib`?** It's as simple as running a single command:

```bash
./aib <action> <file.yml>
```
Example:

```bash
./aib build myarch.yml
```

Here are some key **Archlinux Image Builder** constraints built into the system. Each constraint is designed to maximize system stability and security without delving into the complexities of Archlinux, resulting in a concise and readable configuration file for easier maintenance over time:

> [!IMPORTANT]
> For all the security reasons listed in the grub section below, it is MANDATORY that the system runs in UEFI mode.

- **`btrfs`** is the chosen **filesystem**, enabling the creation of system *snapshots*. If an update causes issues (a common occurrence on Archlinux), you can "go back in time" to restore a working state.
- **`grub`** is the selected **bootloader** due to its simplicity and widespread use.
    - **`sbctl`** is included to generate key pairs from a Microsoft CERT and to sign kernel images and the bootloader, enabling **Secure Boot** for enhanced security.
- **System Hardening** includes:
    - **Kernel parameters** that restrict **ICMP** and **IPv4** packet forwarding, preventing the host from forwarding packets for other devices, a common vulnerability in **DDoS attacks** and **ICMP Flooding**.
    - **`ufw`** firewall for managing network security.
- **`pipewire`** is used for **audio**, as it is the latest and de facto standard for Linux audio systems.
- **`gnome`** is the selected **desktop environment** for its simplicity and minimal configuration requirements.
- **`flatpak`** is the **application manager** of choice, providing containerization for applications and fine-grained system and permission management.

> [!NOTE]
> The `gnome` environment is installed with minimal components, avoiding unnecessary bloat. Be sure to configure `gnome-extensions` and `flatpak.applications` in the **YAML** file as needed.

> [!TIP]
> You can customize `gnome` and `flatpak` to your preferences by specifying desired `gnome-extensions` and applications in the **YAML** file for installation on the system.
