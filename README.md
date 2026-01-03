# IPE Carrier Board - Device Tree Overlays

Device Tree Overlays for the **IPE Carrier Board** by Witte Technology, compatible with Toradex Verdin modules.

## Compatibility

| Branch | TorizonOS | Kernel |
|--------|-----------|--------|
| `toradex_6.6-2.2.x-imx` | 7.4+ | 6.6.x |

## Supported Modules

- ✅ Verdin iMX8M Mini
- ✅ Verdin iMX8M Plus


## Available Overlays

### Verdin iMX8M Plus

| Overlay | Description |
|---------|-------------|
| `verdin-imx8mp_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts` | MIPI-DSI Display 7"/10.1" (1024x600), PWM Backlight, Goodix GT911 Touch |
| `verdin-imx8mp_ipe-board_htmg_lvds_display_10inch_overlay.dts` | Native LVDS Display 10.1" (1280x800), PWM Backlight, Goodix GT928 Touch |
| `verdin-imx8mp_ipe-board_audio-codec.dts` | TAS2110 Audio Codec via I2S/SAI1 |
| `verdin-imx8mp_ipe-board_enable-2ndfec.dts` | Second Ethernet interface (FEC) |
| `verdin-imx8mp_ipe-board_enable-can.dts` | CAN interfaces with RS pin control |
| `verdin-imx8mp_ipe-board_enable-sodimm-56-as-gpio.dts` | SODIMM 56 configured as GPIO (disables QSPI) |
| `verdin-imx8mp_ipe-board_disable-dev-board-devices.dts` | Disable all overlay not present in IPE carrier board |

### Verdin iMX8M Mini

| Overlay | Description |
|---------|-------------|
| `verdin-imx8mm_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts` | MIPI-DSI Display 7"/10.1" (1024x600), PWM Backlight, Goodix GT911 Touch |
| `verdin-imx8mm_ipe-board_enable-can.dts` | CAN interfaces with RS pin control ¹ |
| `verdin-imx8mm_ipe-board_enable-sodimm-56-as-gpio.dts` | SODIMM 56 configured as GPIO (disables QSPI) |
| `verdin-imx8mm_ipe-board_disable-dev-board-devices.dts` | Disable all overlay not present in IPE carrier board |

> ¹ **Note:** The Verdin iMX8M Mini Quad 2GB Wi-Fi / Bluetooth IT (No CAN) **PN: 0068** does NOT have CAN support.

## Repository Structure

```
device-trees/
└── ipe-carrier-board/
    ├── verdin-imx8mp-ipe-board-overlays/
    │   ├── verdin-imx8mp_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts
    │   ├── verdin-imx8mp_ipe-board_htmg_lvds-native_display_10inch_overlay.dts
    │   ├── verdin-imx8mp_ipe-board_enable-2ndfec.dts
    │   ├── verdin-imx8mp_ipe-board_enable-can.dts
    │   └── verdin-imx8mp_ipe-board_enable-sodimm-56-as-gpio.dts
    |   └── verdin-imx8mp_ipe-board_disable-dev-board-devices.dts
    └── verdin-imx8mm-ipe-board-overlays/
        └── verdin-imx8mm_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts
        └── verdin-imx8mm_ipe-board_enable-can.dts`
        └── verdin-imx8mm_ipe-board_enable-sodimm-56-as-gpio.dts
        └── verdin-imx8mm_ipe-board_disable-dev-board-devices.dts
```

## Quick Setup Guide

### 1. Create directory structure

```bash
# enter in you toradex core builder directory
cd ~/tcbdir
# create an custom folder for this compilation
mkdir witte && cd witte
```

### 2. Clone this repository

Inside witte directory:
```bash
cd ~/tcbdir/witte
git clone -b toradex_6.6-2.2.x-imx git@github.com:witte-technology/ipe-carrier-board.git device-trees
```

### 3. Clone Toradex Repository

Inside witte directory clone the linux for your target module.

**Linux kernel for iMX8M Mini and iMX8M Plus:**

```bash
cd ~/tcbdir/witte
git clone -b toradex_6.6-2.2.x-imx git://git.toradex.com/linux-toradex.git linux
```

**Default overlays for iMX8M Mini and iMX8M Plus:**

```bash
cd ~/tcbdir/witte/device-trees
git clone -b toradex_6.6-2.2.x-imx git://git.toradex.com/device-tree-overlays.git
```

### 4. Download TorizonOS image

Download the image for your target module at (inside witte folder):  
https://developer.toradex.com/software/toradex-embedded-software/toradex-download-links-torizon-linux-bsp-wince-and-partner-demos/#torizon-os-7

### 5. Configure tcbuild.yaml

Copy the sample `tcbuild_imx8mm.yaml` or `tcbuild_imx8mp.yaml`  file from this repository to the `witte` folder and adjust it according to your target module. Also rename the file to `tcbuild.yaml` to be recognize as default by build command.

### 6. Splash screen (optional)

Add a 1024x600 PNG image named `custom-splash-screen.png`. If you don't want a custom splash screen, comment out the line in `tcbuild.yaml`:
```yaml
# splash-screen: custom-splash-screen.png
```

### 7. Final structure

```
~/tcbdir/witte/
├── custom-splash-screen.png                              (optional)
├── device-trees/                                         
|   ├── overlays/                                         (Toradex overlays)
|   └── ipe-carrier-board/                                (this repository)
├── linux/                                                (Toradex kernel)
├── tcbuild_imx8mm.yaml
├── tcbuild_imx8mp.yaml
├── torizon-docker-verdin-imx8mm-Tezi_7.4.0+build.28.tar
└── torizon-docker-verdin-imx8mp-Tezi_7.4.0+build.28.tar
```

### 8. Run build

```bash
cd ~/tcbdir/witte
torizoncore-builder build
```
You can specify the file name like below:
```bash
torizoncore-builder build --file tcbuild_imx8mm.yaml
```
Another option is specify the location:
```bash
torizoncore-builder build --file device-trees/ipe-carrier-board/tcbuild_imx8mp.yaml
```

## License

SPDX-License-Identifier: MIT

## Contact

**Witte Technology LTDA**  
https://wittetech.com/
