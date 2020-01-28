# Emacs with 256/true color support in Windows Console

## Background
- Current emacs in Windows Console (`emacs -nw` at cmd.exe) support only 16 colors.
- Windows Console recently support true color by Virtual Terminal sequences.
- Windows Terminal will come.
- Vim already support truecolor in Windows Console.(https://github.com/vim/vim/commit/cafafb381a04e33f3ce9cd15dd9f94b73226831f)

## Build
*Note*: This is **experimental**.
Current implementation is based on Emacs 26.3.

Prerequisites:
- Windows 10
- MSYS2 and MINGW-w64
- Dependancies are installed (See https://github.com/tsuu32/emacs-w32con-vt/blob/master/nt/INSTALL.W64)

Steps:
1. Clone this repo and `./autogen.sh` to generate `configure` script in *MSYS2 bash*:

```sh
git clone https://github.com/tsuu32/emacs-w32con-vt.git
cd emacs-w32con-vt
./autogen.sh
```

2. Run `configure` with `--with-w32-vt-color=NUMBER` option:

```c
./configure --without-dbus --with-w32-vt-color=24bit
```

You can set `16` or `256`, `24bit` for `NUMBER`.

3. Run Make:

```sh
make
```

4. Run Emacs in *cmd.exe* or *powershell.exe*:

```
path\to\emacs-w32con-vt\src\emacs.exe -nw
```

## Screenshot
With [zenburn theme](https://github.com/bbatsov/zenburn-emacs).

![](emacs-zenburn-w32con-256color.jpg)

## Bug
- Starting emacs with no theme cause buggy at 24bit color.

## Future work
- [x] Autoconf support.
- [ ] Use escape sequences more (not only color).
- [ ] Etc.