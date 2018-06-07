# stsx
Stress Testing Tool for S0/S3/S4

```
Usage: stsx [-mlp] <s4|s4k|s3|s3k|s0|s0k|s4simdev|s4simcore|s3simdev|s3simplatform|s3simcore|s4simcpu>

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
