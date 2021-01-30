---
title: "Calling for Beta-Tester"
tags:
  - iGate
  - LoRa32
author: OE5BPA
---

After months of development I can finally call for beta-testers for the new iGate version (21.04.0-dev).

You can find the code in the github repository in the [developer branch](https://github.com/lora-aprs/LoRa_APRS_iGate/tree/develop). Please feel free to create [bug-tickets](https://github.com/lora-aprs/LoRa_APRS_iGate/issues/new?assignees=peterus&labels=bug%2C+beta&template=bug_report_beta.md&title=) with the correct type.

#### What is new
- a complete re-design of the iGate firmware.
- automatic board detection!
- redesigned the config file for simpler configuration.
- simpler way of showing information on the OLED.
- simpler handling from future tasks because of a task handler.

#### What is NOT new
- no new features - from the user perspective everything should be the same like before.

#### What is tested and what is not tested
- I tested the firmware on a simple TTGO LoRa32 v1 board.
- maybe there are boards which will not work out of the box (Ethernet board will definitely not work I think).
