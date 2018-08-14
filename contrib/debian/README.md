
Debian
====================
This directory contains files used to package recurd/recur-qt
for Debian-based Linux systems. If you compile recurd/recur-qt yourself, there are some useful files here.

## recur: URI support ##


recur-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install recur-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your recurqt binary to `/usr/bin`
and the `../../share/pixmaps/recur128.png` to `/usr/share/pixmaps`

recur-qt.protocol (KDE)

