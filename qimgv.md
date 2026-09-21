**Q:** qimgv image fit and fit on window not working

**Ans:** if fit to window" is not working in [qimgv](https://github.com/easymodo/qimgv/issues/578), it is often caused by display scaling issues in Qt6 or window size miscalculations on startup.

Quick Fixes and Workarounds

- **Adjust Qt Scaling Policy:** If you use Linux/Wayland with fractional scaling where Qt6 misbehaves, set the environment variable `QT_SCALE_FACTOR_ROUNDING_POLICY=Ceil` or `RoundPreferFloor`. [[1](https://aur.archlinux.org/packages/qimgv-qt6-kde-git), [2](https://github.com/easymodo/qimgv/issues/578)]
- **Force X11/XCB Backend:** On Linux Wayland sessions, launch qimgv with the environment variable `QT_QPA_PLATFORM=xcb` to bypass native Wayland scaling bugs. [[1](https://github.com/easymodo/qimgv/issues/578)]



**Q:** how to make qimgv start with QT_QPA_PLATFORM=xcb on hyrpland arch new

**Ans:** modify its local `.desktop`

```
cp /usr/share/applications/qimgv.desktop ~/.local/share/applications/
nano ~/.local/share/applications/qimgv.desktop
Exec=env QT_QPA_PLATFORM=xcb qimgv %F


nano ~/.zshrc
alias qimgv="env QT_QPA_PLATFORM=xcb qimgv"
```


