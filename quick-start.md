# Quick Start Guide

Here is the guide to get start with po-util in five minutes or less.

{% method %}

# Upgrade your device's firmware

In order to use po-util with your Photon, P1, Electron, or Redbear Duo, you must first upgrade the system firmware on your device to the version you are using with po-util.

>If you are using a Raspberry Pi or a Core, this step is not necessary as on Raspberry Pi the firmware is managed with particle-agent, and on the Core firmware is monolithic, so you only need to enter DFU mode manually the first time you flash your firmware.

{% sample lang="cpp" %}
```bash
$ po DEVICE_TYPE upgrade
```

Replace `DEVICE_TYPE` with: `photon`, `P1`, `electron`, or `duo`


{% endmethod %}


{% method %}

#Create a project

When using po-util, your code is organized into project repositories that follow a standardized structure.

{% sample lang="cpp" %}

```bash
$ po init DEVICE_TYPE PROJECT_NAME
```

This creates a project repository called `PROJECT_NAME` in the current working directory.

{% endmethod %}



{% method %}

#Write your firmware

Write your project firmware in `firmware/main.cpp`

{% sample lang="cpp" %}

```cpp
#include "Particle.h"

void setup() { // Put setup code here to run once

}

void loop() { // Put code here to loop forever

}
```

This is the boilerplate code for Particle firmware.
{% endmethod %}
