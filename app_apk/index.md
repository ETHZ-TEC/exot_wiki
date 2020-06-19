[:back:](/home)
---

The whole app_apk repository is organised in one AndroidStudio project with following modules:

| Name | Description | Platform tests | 
| ---- | ----------- | -------------- |
| `intentproxy` | [See dedicated page](./intent-proxy) | Dragonboard 810, Samsung Galaxy S5, Sony Xperia Z5 | 
| `libjava`     | Basic java classes with, e.g., intent definitions | - |
| `libnative`   | Includes the app_lib code and provides the basic interface for a service. | - |
| `thermalsc`   | Wrapper for the `miedl-meter` as a simple background service for use in the ExOT measurement automation (experiment execution). | Dragonboard 810, Samsung Galaxy S5, Sony Xperia Z5 | 
| `thermalscui` | Wrapper for the `miedl-meter` for interactive use with an UI. |  Dragonboard 810, Samsung Galaxy S5, Sony Xperia Z5, Fairphone 2, BQ Aquarius X5 Plus, Huawei Nova CAN-L11, Huawei P8Lite ALE-L21, Samsung Galaxy Note 2014 Edition | 