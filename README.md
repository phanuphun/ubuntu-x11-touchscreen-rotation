# README

This repo is a note about how to set the mapping coordinates for a touchscreen.  
In this case I use **X11** instead of **Wayland** because X11 has an X server that centralizes configuration, so mapping the screen is much easier.

### In my case

- I tried **Ubuntu 24.04.3**, but after I mapped the coordinates, problems appeared later: sometimes the touch felt responsive, and sometimes it didn’t.
- On **Ubuntu 22.04 (Jammy Jellyfish)** there is **no problem**.

### Notes

- Check the display server:

  ```bash
  echo $DISPLAY           # check if a display server is available
  echo $XDG_SESSION_TYPE  # check the actual display server type
  ``` 

- If `$XDG_SESSION_TYPE` is not x11, you have to log out first and select “Ubuntu on Xorg” on the login screen instead of the default Ubuntu session.
    - Run xinput or xinput list to show devices
- Run `xinput list-props "<id or name>"` to see details and find the property you want to configure.
- Example for the Coordinate Transformation Matrix:
    - 90 degrees (1): `0 -1 1 1 0 0 0 0 1`
    - 90 degrees (2): `0 1 0 -1 0 1 0 0 1`
-  If there is no warning about Wayland/XWayland, it means the mapping was successfully changed under X11.
- In your home directory you can create a script to set the coordinates every time the system boots or you log in.