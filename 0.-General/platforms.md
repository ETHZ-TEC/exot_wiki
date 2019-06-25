[Back to Home](/home) 
__

## Base configuration
All platforms can be accessed using the username `karajan` and the standard password.
All devices need to be configured to use a [proxy](https://www.ethz.ch/services/de/it-services/katalog/netzwerke-verbindungen/proxy.html).
In unix, add following lines to the `/etc/environment` file:
```bash
http_proxy="http://proxy.ethz.ch:3128/"
https_proxy="http://proxy.ethz.ch:3128/"
ftp_proxy="http://proxy.ethz.ch:3128/"
no_proxy="localhost,127.0.0.1,::1"
```

For Android devices, the proxy can be set in the WiFi settings.
Sometimes the time setting fails, then use following command:
```bash
adb -s [ADB-ID] shell "su 0 toybox date $(date "+%m%d%H%M%Y.%S")"
```
To disable the SELinux layer on Android, use following command:
```bash
adb -s [ADB-ID] shell su root setenforce 0
```

## Usable Platforms
### Bilbo

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Sony Xperia Z5 Dual                                         |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Android 5.1.1                                               |
| Kernel Version      | 3.10.49-perf-g6b847e2                                       |
| MAC-Addresse        | 40:b8:37:c0:44:52                                           |
| IP-Addresse         | 172.31.43.130                                               |
| ADB-ID              | CB5A28J729                                                  |
| ADB-Port            | 51808                                                       |
| Physical Location   | Office ETZ G76                                              |
| Notes               |                                                             |

### Frodo

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Samsung Galaxy S5                                           |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Android 5.0                                                 |
| Kernel Version      | 3.10.9-4521975                                              |
| MAC-Addresse        | 48:5A:3F:85:05:7C                                           |
| IP-Addresse         | 172.31.43.131                                               |
| ADB-ID              | 3208dc2fa4fa518b                                            |
| ADB-Port            | 51808                                                       |
| Physical Location   | Office ETZ G76                                              |
| Notes               |                                                             |

### Merry

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | DragonBoard 810 (pc-10752)                                  |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Android 5.0 developer version                               |
| Kernel Version      |                                                             |
| MAC-Addresse        | 44:1c:a8:1d:cb:c5                                           |
| IP-Addresse         | 172.31.43.132                                               |
| ADB-ID              | 2da22348                                                    |
| ADB-Port            | 51808                                                       |
| Physical Location   | Office ETZ G76                                              |
| Notes               | There is an registered acount for the intrinsyc support     |
|                     | webpage (http://support.intrinsyc.com/login). The support   |
|                     | webpage has several software/documents which may be useful  |
|                     | for us. The login credentials are:                          | 
|                     | username: ethdragon                                         |
|                     | passwd: fingerprinting                                      |

### Pippin

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Ordroid-XU3                                                 |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Ubuntu 18.04.2 LTS                                          |
| Kernel Version      | 4.14.111-158 armv7l                                         |
| MAC-Addresse        | 00:1e:06:61:7a:39                                           |
| IP-Addresse         | 172.31.43.133                                               |
| SSH-Port            | 2237                                                        |
| Physical Location   | Server Room ETZ G60.5                                       |
| Notes               | Console only - no display                                   |

### Gimli
|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |

| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Nvidia Jetson Tegra TX2                                     |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Tegra Ubuntu                                                |
| Kernel Version      | 4.4.38-tegra                                                |
| MAC-Addresse        | 00:04:4b:a7:bf:ea                                           |
| IP-Addresse         | 172.31.43.134                                               |
| SSH-Port            | 51808                                                       |
| Physical Location   |                                                             |
| Notes               | Console only.                                               |

### Pallando

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Thinkpad T460s (nb-10583)                                   |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Ubuntu 16.04 (+VM)                                          |
| Kernel Version      | 4.2.0-42-generic                                            |
| MAC-Addresse        | 28:d2:44:e4:e7:97                                           |
| IP-Addresse         | 172.31.43.135                                               |
| SSH-Port            | 51808                                                       |
| Physical Location   | Office ETZ G76                                              |
| Notes               | Using GUI, used for real attack scenario leaking data from  |
|                     | a VM. VM inside Laptop:                                     |
|                     | Hostname 127.0.0.1 TODO                                     |
|                     | Port 51808                                                  |
|                     | User:     user TODO                                         |
|                     | Password: user                                              |
|                     | This laptop also serves as entry point to all android       |
|                     | devices via adb over USB.                                   |

### Saruman

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Thinkpad T440p (nb-10577)                                   |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Ubuntu 18.04.2 LTS                                          |
| Kernel Version      | 4.15.0-52-generic x86_64                                    |
| MAC-Addresse        | 28:d2:44:b5:bd:9d                                           |
| IP-Addresse         | 172.31.43.136                                               |
| SSH-Port            | 51808                                                       |
| Physical Location   | Server Room ETZ G60.5                                       |
| Notes               | Console only                                                |

### Gandalf

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Thinkpad T440p (nb-10548)                                   |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Ubuntu 16.04.6 LTS                                          |
| Kernel Version      | 4.4.0-148-generic x86_64 (4.9.5+)                           |
| MAC-Addresse        | 28:d2:44:54:00:dc                                           |
| IP-Addresse         | 172.31.43.137                                               |
| SSH-Port            | 51808                                                       |
| Physical Location   | Server Room ETZ G60.5                                       |
| Notes               | Console only                                                |

### Radagast

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
|                     |            |            |

| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Thinkpad T440p (nb-10539)                                   |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Ubuntu 18.04.2 LTS                                          |
| Kernel Version      | 4.15.0-50-generic x86_64 (4.9.5+)                           |
| MAC-Addresse        | 28:d2:44:4f:ef:66                                           |
| IP-Addresse         | 172.31.43.138                                               |
| SSH-Port            | 51808                                                       |
| Physical Location   | Server Room ETZ G60.5                                       |
| Notes               | Console only                                                |

## Old Devices

### Sauron

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
| Not in Service      |    05.2019 |      -     |

| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | Intel(R) Xeon(R) CPU E5-2690 (pc-10476)                     |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Ubuntu 14.04.2                                              |
| Kernel Version      | 3.13.0-55-generic                                           |
| MAC-Addresse        |                                                             |
| IP-Addresse         | 82.130.103.118                                              |
| SSH-Port            | 7820                                                        |
| Physical Location   | Server Room ETZ G60.5                                       |
| Notes               | Console only.                                               |

### Sam (DEAD?)

|  Currently used by  |    from    |    till    |
|:--------------------|:----------:|:----------:|
| Philipp Miedl       |       -    |      -     |


| Characteristic      | Value                                                       |
|:--------------------|:------------------------------------------------------------|
| General Description | DragonBoard 810 (pc-10656)                                  |
| Administrators      | Philipp Miedl (ETZ G76)                                     |
| Operating System    | Android 5.0 developer version                               |
| Kernel Version      |                                                             |
| MAC-Addresse        |                                                             |
| IP-Addresse         | 82.130.102.204                                              |
| SSH-Port            | 51808                                                       |
| Physical Location   | Student Lab                                                 |
| Note                | Disable SELinux: adb -s 414f2238 shell su root setenforce 0 |

