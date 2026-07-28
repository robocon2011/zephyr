.. _esp32_2432s028:

ESP32-2432S028 (Cheap Yellow Display)
#####################################

Overview
********

Community-made Zephyr board support for the "Cheap Yellow Display" (CYD),
a low-cost ESP-WROOM-32 board with an integrated 2.8" 240x320 ILI9341 SPI
LCD, XPT2046 resistive touch controller, microSD slot, discrete RGB LED,
and a PWM-driven piezo buzzer.

Verified peripherals
*********************

- RGB LED (plain GPIO, active-low)
- ILI9341 LCD over SPI2 (HSPI) via the MIPI-DBI mode C wrapper
- XPT2046 touch controller via bitbang SPI (GPIO-based), since its pins
  do not share a physical bus with the LCD or SD card
- microSD card over SPI3 (VSPI), FAT filesystem, automounted at ``/SD:``
- PWM buzzer via the LEDC peripheral (GPIO26)
- BOOT button (gpio-keys)

Not yet ported
***************

- Light sensor / LDR (if present on your revision)
- On-board flash-based storage (some board revisions omit external flash)

Programming and Debugging
**************************

Flash over the CH340 USB-to-UART bridge (either the Micro-USB or Type-C
port, depending on revision):

.. code-block:: console

   west build -b esp32_2432s028/esp32/procpu samples/hello_world
   west flash

References
**********

Board revisions in this family vary (flash presence, USB connector type,
RGB channel order). Always verify pin mapping against your physical unit
before relying on this configuration.
