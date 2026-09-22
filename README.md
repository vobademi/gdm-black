## gdm-black

`gdm-black` sets your GDM background color to black. It requires [`glib2-devel`](https://archlinux.org/packages/core/x86_64/glib2-devel).

> [!NOTE]
> Tested on Arch Linux **only**.

```bash
git clone https://github.com/vobademi/gdm-black.git
cd ./gdm-black
chmod 755 gdm-black
sudo ./gdm-black
```

### Automate using pacman hook

Subsequent updates of `gnome-shell` overwrite `gnome-shell-theme.gresource`, hence the background color. This can be circumvented with a pacman hook:

1. Edit the following line in `gdm-black.hook` to where `gdm-black` is located:

```bash
Exec = /path/to/gdm-black
```

2. Uncomment `#HookDir`:

```bash
sudo sed -i 's/#HookDir/HookDir/' /etc/pacman.conf
```

3. Copy `gdm-black.hook` to `/etc/pacman.d/hooks`:

```bash
sudo cp ./gdm-black.hook /etc/pacman.d/hooks
```

### License

[MIT](https://github.com/vobademi/gdm-black/blob/main/LICENSE)
