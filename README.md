## gdm-black

`gdm-black` sets your GDM background color to black (or custom hex color). It requires [`glib2-devel`](https://archlinux.org/packages/core/x86_64/glib2-devel).

> [!NOTE]
> Tested on Arch Linux **only**.

### Usage

> [!IMPORTANT]
> Make `gdm-black` executable first:
>
> ```bash
> chmod +x gdm-black
> ```

+ Set background color to black:

```bash
sudo ./gdm-black
```

+ Set background color to custom hex color:  
(Keep in mind that bash ignores everything after #, so enclose in "" or don't use #)

```bash
sudo ./gdm-black --color "#RRGGBB"
# or
sudo ./gdm-black --color RRGGBB
```

+ Restore the original color:

```bash
sudo ./gdm-black --restore
```

### Automate using pacman hook

Subsequent updates of `gnome-shell` overwrite `gnome-shell-theme.gresource`, hence the background color. This can be circumvented with a pacman hook:

1. Copy `gdm-black` to `/usr/local/bin`:

```bash
sudo cp ./gdm-black /usr/local/bin
```

2. Uncomment `#HookDir`:

```bash
sudo sed -i 's/#HookDir/HookDir/' /etc/pacman.conf
```

3. Copy `gdm-black.hook` to `/etc/pacman.d/hooks`:

```bash
sudo mkdir -p /etc/pacman.d/hooks
sudo cp ./gdm-black.hook /etc/pacman.d/hooks
```

4. (Optional) Append `--color "#RRGGBB"` or `--color RRGGBB` for custom hex color:

```bash
sudo sed -i '/Exec/s/$/ --color "#RRGGBB"/' /etc/pacman.d/hooks/gdm-black.hook
# or
sudo sed -i '/Exec/s/$/ --color RRGGBB/' /etc/pacman.d/hooks/gdm-black.hook
```

### License

[MIT](https://github.com/vobademi/gdm-black/blob/main/LICENSE)
