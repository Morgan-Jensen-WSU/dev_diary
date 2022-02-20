# Customizing i3 Window Manager

## What is i3
i3 is a tiling window manager. This means that as windows are opened, they automatically fill a predefined space
on the desktop. When one window is open, it will fill the entire desktop, leaving no wasted space. As more windows
are added, they will either split the space vertically or horizontally, depending on the current settings.
This creates an efficient environment with little user overhead.

## How to cusomize i3

### Where to customize
i3 is controlled by a `config` file, usually found at `~/.config/i3`. If no config file is found at this location, i3
will prompt the user to create one automatically.

### Wallpaper
To set the wallpaper, I used a program called `nitrogen`. Nitrogen is a wallpaper manager that can be started in the
i3 config file. After installation, open nitrogen, add the directory of your wallpaper, and select the wallpaper you 
want. This should set the wallpaper on your desktop.

Now that you have set one, go to your i3 config file. Somewhere in the file, add the line 
```
exec --no-startup-id nitrogen --restore
```
this will start nitrogen on start up and restore the last selected wallpaper.

### Gaps
To set gaps between windows, to my knowlege, you need to install `i3-gaps` instead of vanilla i3wm. i3-gaps is a fork
off of i3 that is kept in parallel with i3. The main difference is it allows you to set gaps between windows.

To set the gaps once you have i3-gaps, add these lines of code 
```
for_window [class="^.*"] border pixel 2  # i3 gaps does not support the command bars at the top of windows
# you can also set border pixel to 0, but i like it at 2, so it is still easy to tell which window is selected
gaps inner 10  # sets the boarder to 10 between windows
smart_borders on # option for smart borders. Check i3-gaps github for info.
```

### Navigatoin
By default, i3 has navigation tied to j, k, l, ;, in addition to using arrow keys.
I personally prefer using the same key bindings as vim (h, j, k, l). To change this, 
find the lines that say `bindsym $mod+[j/k/l/semicolon] focus [left/down/up/right]` and change them
to be `bindsym $mod+[h,j,k,l] focus [left/down/up/right]`

This can also be changed in the area that looks like this:
```
mode "resize" { 
    ...
}
```

