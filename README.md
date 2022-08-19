# WatchMate

Companion app for [PineTime](https://www.pine64.org/pinetime/) smart watch running [InfiniTime](https://github.com/InfiniTimeOrg/InfiniTime/) firmware.

Visually optimized for GNOME, adaptive for Linux phone and desktop.

![collage_2022-08-14_readme](/uploads/8dbf136bec813c09d44fac6d0b22b54c/collage_2022-08-14_readme.png)

##### Features

- Discover and connect to the watch via Bluetooth
- Serve current time to the watch
- Read data from the watch (battery level, heat rate, firmware version)
- Perform OTA firmware update (from manually selected files or automatically downloaded release)
- Automatically check for available firmware updates
- Integrate with media-players
- More to come

## Install

### ArchLinux

WatchMate is available on AUR as [watchmate-git](https://aur.archlinux.org/packages/watchmate-git), so you can install it either [manually](https://wiki.archlinux.org/title/Arch_User_Repository#Installing_and_upgrading_packages) or with your [AUR helper](https://wiki.archlinux.org/title/AUR_helpers) of choice, for example:

```
paru -S watchmate-git
```

### Flathub

WatchMate is on [Flathub](https://flathub.org/apps/details/io.gitlab.azymohliad.WatchMate). To install it from command line execute the following command:

```
flatpak install flathub io.gitlab.azymohliad.WatchMate
```

## Build

### Native

##### Prerequisites

- [GTK4](https://gtk-rs.org/gtk4-rs/stable/latest/book/installation_linux.html)
- [Libadwaita](https://gtk-rs.org/gtk4-rs/stable/latest/book/libadwaita.html#linux)
- [Rust](https://www.rust-lang.org/tools/install)

##### Build and Run

To compile and run the project, execute the following command from repo directory:

```
cargo run --release
```

### Flatpak

##### Prerequisites

- [flatpak](https://www.flatpak.org/setup/)
- [flatpak-builder](https://docs.flatpak.org/en/latest/flatpak-builder.html)

##### Install Dependencies

```
flatpak install org.gnome.Platform//42 org.gnome.Sdk//42 org.freedesktop.Sdk.Extension.rust-stable//21.08
```

##### Build

```
flatpak-builder --user build-dir flatpak/io.gitlab.azymohliad.WatchMate.yml
```

##### Run

```
flatpak-builder --run build-dir flatpak/io.gitlab.azymohliad.WatchMate.yml watchmate
```

##### Install

```
flatpak-builder --install build-dir flatpak/io.gitlab.azymohliad.WatchMate.yml
```

## Roadmap

- [x] Bluetooth device discovery, connecting to InfiniTime watch
- [x] Sharing time via Current Time Service
- [x] Reading data from the watch
    - [x] Battery level
    - [x] Firmware version
    - [x] Heart rate
- [x] OTA firmware update
    - [x] Firmware update from manually selected file
    - [x] Automatic firmware downloading from [InfiniTime releases](https://github.com/InfiniTimeOrg/InfiniTime/releases)
- [x] Media-player control
- [ ] Secure pairing
- [ ] Notifications
- [ ] Settings
- [ ] About dialog
- [x] Packaging and distribution
    - [x] Flathub
    - [x] AUR


## Tech Stack and Thanks

WatchMate stands on the shoulders of the following giants:

- [Rust](https://www.rust-lang.org/) programming language.
- [Relm4](https://relm4.org/), [GTK4](https://gtk.org/) ([rs](https://gtk-rs.org/)) and [Libadwaita](https://gnome.pages.gitlab.gnome.org/libadwaita/) ([rs](https://world.pages.gitlab.gnome.org/Rust/libadwaita-rs/)) for GUI.
- [BlueR](https://world.pages.gitlab.gnome.org/Rust/libadwaita-rs/) (an official [BlueZ](http://www.bluez.org/) Bindings for Rust) for the bluetooth stack.
- Awesome parts of Rust ecosystem, like [tokio](https://tokio.rs/), [serde](https://serde.rs/), [reqwest](https://github.com/seanmonstar/reqwest), [zbus](https://gitlab.freedesktop.org/dbus/zbus/), [anyhow](https://github.com/dtolnay/anyhow) and others (see [Cargo.toml](Cargo.toml) for the full list).

I'm deeply grateful to all people behind these technologies. WatchMate wouldn't be possible without them: first, it would be technically unliftable; second, even with the alternatives, I probably wouldn't enjoy it so much, and joy is vitally important for hobby projects like this one.
