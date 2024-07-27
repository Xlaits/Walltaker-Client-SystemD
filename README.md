# Walltaker-Client-SystemD
A SystemD service for running Walltaker.

## Requirements
1. A properly set up JBerliner's Walltaker Client
2. `wal`, `pywal`, or `python-pywal` (Optional)
3. A wallpaper setting program compatable with `wal`, such as `feh`

## Basic Setup
1. clone and configure [Plush Pawrest's/JBerliner's Walltaker Client, found here.](https://gitlab.com/JBerliner/walltaker-client) It is hosted on gitlab.
2. Install `wal`, sometimes called `pywall` or `python-pywal` in your package manager.
3. clone this repo.
4. Edit `walltaker.service`
     1. Change `ExecStart=` from `/usr/bin/bash /home/username/path/to/walltaker.sh 1>/dev/null 2>/dev/null` to point to walltaker.sh in `walltaker-client`.
     2. If you want to have the service:
        1. Reset your wallpaper to a specified one: change `ExecStopPost=`'s `username` to your username.
        2. Not touch your wallpaper: Comment out or delete the `ExecStopPost=` line.
5. Edit `walltaker_reset.sh`
    1. If you are using `wal` and want your wallpaper reset: Edit the location of the image in the command to point to the one you wish.
    2. If you're not using `wal`, but still want your wallpaper reset: Change this file to your preferred wallpaper setting command.
6. copy or move `walltaker.service` and, if you're using it, `walltaker_reset.sh` to `~/.config/systemd/user/`
7. `$ systemctl --user daemon-reload`

## Usage

1. If you want it to run at login: `$ systemctl --user enable walltaker`
2. To start it manually: `$ systemctl --user start walltaker`
3. To stop the service: `$ systemctl --user stop walltaker`
