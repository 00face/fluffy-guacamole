# fluffy-guacamole
## Tip, Tricks, Solutions
### <img src="https://github.com/user-attachments/assets/8f488d3f-bc6f-40b6-a4e6-c321056bbf9e" data-canonical-src="https://github.com/user-attachments/assets/8f488d3f-bc6f-40b6-a4e6-c321056bbf9e" width="720" height="450" />

# Setting Up `xwinwrap` with `glmatrix` or any Screensaver as Desktop Background in Linux

## Screensaver as background Table of Contents

- [Step 1: Install Required Packages](#step-1-install-required-packages)
- [Step 2: Clone the `xwinwrap` Repository](#step-2-clone-the-xwinwrap-repository)
- [Step 3: Build and Install `xwinwrap`](#step-3-build-and-install-xwinwrap)
- [Step 4: Install `xscreensaver`](#step-4-install-xscreensaver)
- [Step 5: Locate the `glmatrix` Binary](#step-5-locate-the-glmatrix-binary)
- [Step 6: Run `glmatrix` as Desktop Background](#step-6-run-glmatrix-as-desktop-background)
- [Explanation of `xwinwrap` Options](#explanation-of-xwinwrap-options)
- [Troubleshooting](#troubleshooting)
- [Additional Resources](#additional-resources)

## Step 1: Install Required Packages

```markdown
First, install the necessary development packages and dependencies:

```bash
sudo apt-get install mpv xorg-dev build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev
```

## Step 2: Clone the `xwinwrap` Repository

Clone the `xwinwrap` repository from GitHub:

```bash
git clone https://github.com/mmhobi7/xwinwrap.git
cd xwinwrap
```

## Step 3: Build and Install `xwinwrap`

Build and install `xwinwrap`:

```bash
make
sudo make install
make clean
```

## Step 4: Install `xscreensaver`

Install `xscreensaver` and its additional packages:

```bash
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
```

## Step 5: Locate the `glmatrix` Binary

Ensure that the `glmatrix` binary is located. Typically, it can be found in `/usr/libexec/xscreensaver/`:

```bash
ls /usr/libexec/xscreensaver/glmatrix
```

## Step 6: Run `glmatrix` as Desktop Background

Use `xwinwrap` to run `glmatrix` as your desktop background:

```bash
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/libexec/xscreensaver/glmatrix -root -window-id WID
```

## Explanation of `xwinwrap` Options

- `-ni`: No input (the window will not accept any input).
- `-fs`: Fullscreen mode.
- `-s`: Sticky (the window will stay on all virtual desktops).
- `-st`: Skip taskbar (the window will not appear in the taskbar).
- `-sp`: Skip pager (the window will not appear in the pager).
- `-b`: Below (the window will be placed below other windows).
- `-nf`: No focus (the window will not take focus).
- `--`: Separates `xwinwrap` options from the command to run.
- `/usr/libexec/xscreensaver/glmatrix -root -window-id WID`: The command to run the `glmatrix` screensaver with the specified window ID.

## Troubleshooting

If you encounter any issues, ensure that:
- The path to the `glmatrix` binary or screensaver's binary you want to use is correct:
  `sudo find / -name "glmatrix" 2>/dev/null`
The location of xscreensaver binaries can vary depending on the distribution and how it was installed.
- All dependencies are correctly installed.
- `xwinwrap` is correctly built and installed.

## Additional Resources

- [xwinwrap GitHub Repository](https://github.com/mmhobi7/xwinwrap)
- [xscreensaver Package](https://packages.ubuntu.com/xscreensaver)

```
