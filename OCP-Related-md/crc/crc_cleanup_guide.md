# CodeReady Containers (CRC) Full Cleanup Guide

## 1. Stop and Delete CRC Cluster

```bash
crc stop
crc delete
```

## 2. Full Cleanup (Removes All Files)

```bash
crc cleanup
sudo rm -rf ~/.crc  # Removes configs, cache, and VM disks
```

## 3. Remove CRC Binary

```bash
sudo rm -f /usr/local/bin/crc
```

## 4. Free Up Additional Space

### A. Delete Downloaded Files

```bash
rm -f ~/crc-linux-*.tar.xz ~/pull-secret.txt
```

### B. Remove Libvirt/KVM Assets (If No Longer Needed)

```bash
sudo virsh list --all              # Check for leftover VMs
sudo virsh undefine crc            # Remove CRC VM definition
sudo rm -f /var/lib/libvirt/images/crc*.qcow2  # Delete disk images
```

## 5. Verify Memory/Disk Space is Freed

```bash
df -h     # Check disk space
free -h   # Check memory
```

## Optional: Remove Dependencies

If you no longer need virtualization tools:

- For RHEL/CentOS:

```bash
sudo dnf remove -y libvirt qemu-kvm virt-manager
```

- For Debian/Ubuntu:

```bash
sudo apt purge -y qemu-kvm libvirt-daemon-system
```

---

## What This Cleans Up

| Component     | Location                            |
|--------------|-------------------------------------|
| CRC VM       | `~/.crc/machines/crc`               |
| Cache        | `~/.crc/cache`                      |
| Configs      | `~/.crc/crc.json`                   |
| Disk Images  | `/var/lib/libvirt/images/`          |

---

## After Uninstall

- **Memory:** The CRC VM typically uses 8–12 GB RAM (now freed).
- **Disk Space:** Saves 30–50 GB (VM + images + cache).

---

Let me know if you need help with any step! 🚀
