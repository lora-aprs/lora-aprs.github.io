---
title: "New iGate release: v21.10.0"
tags:
  - iGate
  - LoRa32
author: OE5BPA
---

After months of development I can finally say that the new iGate version arrived today (21.10.0).

You can find the code in the github repository in the [master branch](https://github.com/lora-aprs/LoRa_APRS_iGate). Please feel free to create [bug-tickets](https://github.com/lora-aprs/LoRa_APRS_iGate/issues/new?assignees=peterus&labels=bug&template=bug_report_beta.md&title=) with the correct type.
Thanks to all bug reporters! Please keep the good work :)

#### What is new
- a complete re-design of the iGate firmware.
- automatic board detection!
- redesigned the config file for simpler configuration.
- simpler way of showing information on the OLED.
- simpler handling from future tasks because of a task handler.
- removed Digi mode as it will move into his own repository/project.

#### What is NOT new
- no new features - from the user perspective everything should be the same like before.

#### What is tested and what is not tested
- I tested the firmware on a simple TTGO LoRa32 v1 board and on my Ethernet Board.
