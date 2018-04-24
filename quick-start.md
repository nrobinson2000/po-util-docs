# Quick Start Guide

Here is the guide to get start with po-util in five minutes or less.

{% method %}

#Create a project

When using po-util, your code is organized into project repositories that follow a standardized structure.

{% sample lang="cpp" %}

```bash
$ po DEVICE_TYPE init PROJECT_NAME
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
