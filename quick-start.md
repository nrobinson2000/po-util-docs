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

#Write some firmware

Write your project firmware in `firmware/main.cpp`

Here is some example firmware:

{% sample lang="cpp" %}

```cpp
#include "Particle.h"

void setup() { // Put setup code here to run once
  Particle.publish("Hello World!");
  pinMode(D7, OUTPUT);
}

void loop() { // Put code here to loop forever
  digitalWrite(D7, HIGH);
  delay(500);
  digitalWrite(D7, LOW);
  delay(500);
}
```

{% endmethod %}

{% method %}

# Build and flash your firmware

Using po-util allows you to compile your firmware locally using the GCC ARM toolchain.  You can flash firmware to you device over USB using DFU Utilites, or you can flash it Over-The-Air using particle-cli.

{% sample lang="cpp" %}

```bash
$ po DEVICE_TYPE build # Build your firmware to test if it compiles

$ po DEVICE_TYPE flash # Build and flash your firmware over USB

$ po DEVICE_TYPE ota DEVICE_NAME # Flash firmware Over-The-Air
```






{% endmethod %}
