# stsx
Stress Testing Tool for S0/S3/S4

```
Usage: stsx [-mlpuh] <s4|s4k|s3|s3k|s0|s0k|s43|s43k|s30|s30k|s40|s40k|s4simdev|s4simcore|s3simdev|s3simplatform|s3simcore|s4simcpu>

-m    Specifies the maximum of retries.
      Default: 9999999999
-l    Specifies the watchdog server.
      Example: localhost
-p    Specifies the port of the watchdog server
      Default: 1234
-u    The username of the user who owns the GNOME/KDE/XFCE-Session.
      This username is required to disable the auto suspend/blank properly.
      If you don't specify this username, please disable auto suspend/black
      manually.
-h    Displays this message

      Possible deductions:
      simdev fails                 -> no BIOS issue
      simcore passes AND s4k fails -> BIOS issue
      s4simcpu fails               -> no BIOS issue + CPU hotplug bug

      Only use coresim on machines that switch off power to busses in
      ACPI.
```

### Power states
* __S0__
    ```
    State:  Suspend-To-Idle
    ACPI state: S0
    Label: "s2idle" ("freeze")
    ```

* __S3__
    ```
    State: Suspend-to-RAM
    ACPI State: S3
    Label: "deep"
    ```

* __S4__
    ```
    State: Suspend-to-disk
    ACPI State: S4
    Label: "disk"
    ```

### How to disable auto suspend/blank

#### Gnome3
```
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```

#### Gnome2
```
gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
```

#### XFCE
```
xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-ac -n -t uint -s 0
xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-battery -n -t uint -s 0

```
