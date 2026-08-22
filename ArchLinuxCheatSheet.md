# Arch Linux — Cheat Sheet

## Package Manager

```
> pacman -Q                     # List of installed packages.
> pacman -Qi <package>          # Report info about <package>.
> pacman -Ql <package>          # List files owned by <package>.
> pacman -Qo <path>             # Report which package owns file located at <path>.
> pacman -Qs "<reg.ex>"         # Search for packages matching <reg.ex>.
> pacman -Q | grep "<reg.ex>"   # List installed packages, pipe to "grep" matching <reg.ex> (faster than "pacamn -Qs").
> pacman -S <package>           # Install <package> from internet repository.
> pacman -U <tarball>           # Install package from <package>.tar.zst (tarball).
> pacman -Rs <package>          # Remove <package> and orphan dependencies.
> pacman -Rns $(pacman -Qdtq)   # Remove orphan packages remaining on system.
> pacman -Scc                   # Clear package cache.
> pacman -S archlinux-keyring   # Update archlinux-keyring (Required before "pacman -Syu" after no recent full package updates).
> pacman -Syu                   # Full package updates.
> pactree <package>             # Show tree of package dependencies for <package>.
> pactree -r <package>          # Show packages depending on <package>.
```

## Arch Linux — Distro Commands

```
> pacstrap <root.dir> <package>...       # Install initial Arch Linux <package> or multiple <package> to <root.dir>.
  # e.g. > pacstrap . base base-devel.
> arch-chroot <chroot-dir> <command>     # Change to new Arch Linux root.
  # e.g. > arch-chroot . /bin/bash.
> pacman-key --init                      # Initialise Arch Linux keyring.
> pacman-key --populate archlinux        # Populate Arch Linux keyring.
> mkinitcpio -p linux                    # Update initramfs boot-image (configured in "/etc/mkinitcpio.conf").
> grub-mkconfig -o /boot/grub/grub.cfg   # Generate a GRUB boot-loader configuration (configured in "/etc/default/grub").
```

[![FOSS Cheat Sheets — License](https://img.shields.io/badge/LICENSE-CC0--1.0-blue?style=for-the-badge&logo=creativecommons&logoColor=white)](LICENSE.md)
