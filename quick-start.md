# Quick Start Guide

{% method %}

# Upgrade your device's firmware

In order to use po-util with your Photon, P1, Electron, or Redbear Duo, you must first upgrade the system firmware on your device to the version you are using with po-util.

>If you are using a Raspberry Pi or a Core, this step is not necessary as on Raspberry Pi the firmware is managed with particle-agent, and on the Core firmware is monolithic, so you only need to enter DFU mode manually the first time you flash your firmware.

{% sample lang="cpp" %}
```bash
# Run the following with "photon", "P1", "electron", or "duo" instead of "DEVICE_TYPE"

$ po DEVICE_TYPE upgrade
```


{% endmethod %}