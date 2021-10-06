# rEFInd theme Regular

A simplistic clean and minimal theme for [rEFInd](https://www.rodsbooks.com/refind/index.html), forked from [munlik's theme](https://github.com/munlik/refind-theme-regular).[^1]

 **press F10 to take screenshot**
 
|![Screenshot 01](https://raw.githubusercontent.com/bobafetthotmail/refind-theme-regular/master/src/white_theme.png)|![Screenshot 02](https://raw.githubusercontent.com/bobafetthotmail/refind-theme-regular/master/src/dark_theme.png)|
|:-:|:-:|
|Regular-Light Theme (Default)|Regular-Dark theme|



### Installation [Quick]:

1. Just paste this command in your terminal and enter your choices.
   #### Linux
   ```
   sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/bobafetthotmail/refind-theme-regular/master/install.sh)"
   ```
   
   #### Windows-TO DO
   If you prefer using [PowerShell Core](https://github.com/PowerShell/PowerShell), replace `powershell` with `pwsh`[^2].
   ```
   powershell -blah blah blah
   ```
   
2. To further adjust icon size, font size, background color and selector color :
   #### Linux
   Edit `/boot/efi/EFI/refind/refind-theme-regular/theme.conf` as root/Superuser.
   
   #### Windows
   Mount EFI System partition and edit `R:\EFI\refind\refind-theme-regular\theme.conf` (Run as admin).
   ```
   mountvol R: /S
   notepad R:\EFI\refind\refind-theme-regular\theme.conf
   ```
   
### Installation [Manual]:
This is written primarily for `Linux`, but doing the equivalent will work for `Windows`.

1. Clone git repository to your `$HOME` directory.
   ```
   git clone https://github.com/bobafetthotmail/refind-theme-regular.git
   ```

2. Remove unused directories and files.
   ```
   sudo rm -rf refind-theme-regular/{src,.git}
   ```
   ```
   sudo rm refind-theme-regular/install.{sh,ps1}
   ```

3. Locate refind directory under EFI partition. For most Linux based system is commonly `/boot/efi/EFI/refind/`. Copy theme directory to it.

   **Important:** Delete older installed versions of this theme before you proceed any further.

   ```
   sudo rm -rf /boot/efi/EFI/refind/{regular-theme,refind-theme-regular}
   ```
   ```
   sudo cp -r refind-theme-regular /boot/efi/EFI/refind/
   ```

4. To adjust icon size, font size, background color and selector color edit `theme.conf`.
   ```
   sudo vi /boot/efi/EFI/refind/refind-theme-regular/theme.conf
   ```

5. To enable the theme add `include refind-theme-regular/theme.conf` at the end of `refind.conf`, and comment out or delete any other themes you might have installed.
   ```
   sudo vi /boot/efi/EFI/refind/refind.conf
   ```

**NOTE**: If you're not getting your full resolution or having color issues, then try disabling the CSM in your UEFI settings.

### Contribute new icons:

0. Fork this repository on github and then git clone your fork of this repository in your Linux system.

1. The icons must be in `svg` format to allow easy generation of icons at any scale. Canvas size must have width and height 128 px for OS icons, or 48 px for tool icons. The actual icon in the svg file should roughly fit in a square with a side of 96 px or 20 px (for OS and tool icons, respectively). Inkscape is a good program to create and work with svg files.

2. Copy the svg file in `/src/svg/big` or `/src/svg/small` (depending on what is more appropriate) and rename them to be consistent with others.

3. Install inkskape and optipng in your linux system as they will be needed to process the icons by the next step.

4. `cd` in the `./src` directory and run the script `./render_bitmap.sh`, which will process the svg files and generate the png files at various sizes.

5. Copy the `png` icons you generated from their `/src/bitmap` subfolder into the appropriate `/icons` subfolders for their size by running `./copy-bitmap.sh`.

6. Commit your changes, upload to your fork and then open a PR.

**More information**

[rEFInd](http://www.rodsbooks.com/refind/) The official rEFInd website
[^1]: Since [Munlik](https://github.com/munlik) seems to have abandoned [his project](https://github.com/munlik/refind-theme-regular), he didn't answer to (my) PRs on github for years.
[^2]: Though pwsh is cross-platform, this script is written exclusively for Windows.
