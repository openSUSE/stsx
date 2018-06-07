# stsx
Stress Testing Tool for S0/S3/S4

###### S0
```
State:  Suspend-To-Idle
ACPI state: S0
Label: "s2idle" ("freeze")
```

###### S3
```
State: Suspend-to-RAM
ACPI State: S3
Label: "deep"
```

###### S4
```
State: Suspend-to-disk
ACPI State: S4
Label: "disk"
```

```
Usage: stsx [-mlp] <s4|s4k|s3|s3k|s0|s0k|s43|s43k|s30|s30k|s40|s40k|s4simdev|s4simcore|s3simdev|s3simplatform|s3simcore|s4simcpu>

-m    Specifies the maximum of retries.
-l    Specifies the watchdog server.
      Example: localhost
-p    Specifies the port of the watchdog server
      Default: 1234

      Possible deductions:
      simdev fails                 -> no BIOS issue
      simcore passes AND s4k fails -> BIOS issue
      s4simcpu fails               -> no BIOS issue + CPU hotplug bug

      Only use coresim on machines that switch off power to busses in
      ACPI.
```
