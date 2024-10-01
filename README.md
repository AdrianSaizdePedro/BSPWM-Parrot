# BSPWM-Parrot Setup

This repository contains a fully automated setup script to install and configure BSPWM on Parrot OS with several additional tools like Polybar, Picom, Kitty, and custom themes and fonts.

## Installation Instructions

To install the configuration, follow these steps:

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/AdrianSaizdePedro/BSPWM-Parrot.git
    ```

2. **Navigate into the Directory**:
    ```bash
    cd BSPWMparrot
    ```

3. **Make the Installation Script Executable**:
    ```bash
    chmod +x install.sh
    ```

4. **Run the Installation Script**:
    ```bash
    ./install.sh
    ```

This script will:
- Update the system
- Install all necessary dependencies for BSPWM, Polybar, Picom, Kitty, ZSH, and other utilities
- Set up Polybar and Picom with your custom configurations
- Install Powerlevel10k for both the user and root
- Copy configuration files and themes for BSPWM, Polybar, Rofi, and Kitty
- Set up custom hotkeys, fonts, and terminal settings
- Install a custom wallpaper and ZSH plugins

Once the installation completes, you will receive a notification saying "BSPWM INSTALADO".

## Customizing the Setup

After installation, you may want to customize certain aspects of the system to fit your preferences. Below are some key files and options to modify.

### Hotkey Customization

The hotkeys for the window manager and other utilities are defined in the `~/.config/sxhkd/sxhkdrc` file. Here are some useful bindings:

- **Launch Terminal**: 
    ```bash
    super + Return
    /opt/kitty/bin/kitty
    ```

- **Program Launcher** (via Rofi):
    ```bash
    super + d
    rofi -show run
    ```

- **Reload Sxhkd Config**:
    ```bash
    super + Escape
    pkill -USR1 -x sxhkd
    ```

You can add or modify these bindings to change how BSPWM behaves. For example, you can change the default terminal emulator, or assign different hotkeys for launching applications.

### Polybar Configuration

The Polybar settings are located in `~/.config/polybar/current.ini`. It defines the appearance and modules of your bar. Example sections to modify include:

- **Bar Layout** (e.g., `bar/primary`, `bar/secondary`):
    ```ini
    [bar/primary]
    width = 2.5%
    height = 40
    background = ${color.white}
    foreground = #000000
    modules-center = sysmenu
    ```

You can modify the `modules-center` or `modules-left` values to change what is displayed in the Polybar. You can also modify the `background` and `foreground` color values to personalize your color scheme.

### Kitty Configuration

Kitty terminal settings are located in `~/.config/kitty/kitty.conf`. Some key settings include:

- **Font Family and Size**:
    ```bash
    font_family      HackNerdFont
    font_size 12
    ```

- **Keybindings**:
    You can modify the keybindings for various functions, such as:
    ```bash
    map ctrl+left neighboring_window left
    map ctrl+right neighboring_window right
    ```

### Wallpaper Customization

To change the wallpaper, replace the images in the `~/Wallpaper/` folder with your desired images. The script will automatically apply the wallpapers from this folder during installation.

### Additional Scripts and Tools

- **Scripts**:
    - The script `~/config/bin/ethernet_status.sh` is used to display the Ethernet status in Polybar. You can modify this script to change the output or appearance.
    - Custom screenshot functionality is set up with `flameshot`, accessible with the `Print` key.
  
- **Kitty as Root**:
    Configuration for running Kitty as root is set up in `/root/.config/kitty/`. This allows consistent terminal behavior across both user and root sessions.

## ZSH and Powerlevel10k Customization

After the installation, your terminal will be using ZSH with Powerlevel10k. The ZSH configuration is in `~/.zshrc` and `~/.p10k.zsh`. You can tweak these files to change the appearance and functionality of your terminal.

- To change the Powerlevel10k theme, you can edit `.p10k.zsh`:
    ```bash
    vim ~/.p10k.zsh
    ```

- The root user has a separate Powerlevel10k configuration in `/root/.p10k.zsh`.

## Notes

- If you encounter issues with permissions, ensure all necessary scripts are executable:
    ```bash
    chmod +x ~/.config/bspwm/bspwmrc
    chmod +x ~/.config/bspwm/scripts/*
    ```

- To reset or reapply the setup, simply run the installation script again:
    ```bash
    ./install.sh
    ```

## Credits

Special thanks to the maintainers of BSPWM, Polybar, Kitty, Picom, and all other tools used in this setup.
