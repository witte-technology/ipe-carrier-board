# IPE Carrier Board - Device Tree Overlays

Device Tree Overlays for the **IPE Carrier Board** by Witte Technology, compatible with Toradex Verdin modules.

## Compatibility

| Branch | TorizonOS | Kernel |
|--------|-----------|--------|
| `torizon-7.x_kernel-6.6` | 7.4+ | 6.6.x |

## Supported Modules

- ✅ Verdin iMX8M Mini
- ✅ Verdin iMX8M Plus
- 🔜 Verdin AM62 *(coming soon)*
- 🔜 Verdin AM62P *(coming soon)*
- 🔜 Verdin iMX95 *(coming soon)*

## Available Overlays

### Verdin iMX8M Plus

**verdin-imx8mp_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts**
- MIPI-DSI Display 7"/10.1" (1024x600)
- PWM Backlight
- Goodix GT911 Touch

**verdin-imx8mp_ipe-board_htmg_lvds-native_display_10inch_overlay.dts**
- Native LVDS Display 10.1" (1280x800)
- PWM Backlight
- Goodix GT928 Touch

**verdin-imx8mp_ipe-board_enable-2ndfec.dts**
- Second Ethernet interface (FEC)

**verdin-imx8mp_ipe-board_enable-can.dts**
- CAN interfaces

**verdin-imx8mp_ipe-board_enable-sodimm-56-as-gpio.dts**
- SODIMM 56 as GPIO

### Verdin iMX8M Mini

**verdin-imx8mm_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts**
- MIPI-DSI Display 7"/10.1" (1024x600)
- PWM Backlight
- Goodix GT911 Touch

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
    └── verdin-imx8mm-ipe-board-overlays/
        └── verdin-imx8mm_ipe-board_htmg_mipi-dsi_display_7_to_10inch_overlay.dts
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
git clone -b torizon-7.x_kernel-6.6 https://github.com/user/repo.git device-trees
```

### 3. Clone Toradex Linux kernel

Inside witte directory clone the linux for your target module.

**For iMX8M Mini and iMX8M Plus:**
```bash
git clone -b toradex_6.6-2.2.x-imx git://git.toradex.com/linux-toradex.git linux
```

**For AM62 and AM62P:**
```bash
git clone -b toradex_ti-linux-6.6.y git://git.toradex.com/linux-toradex.git linux
```

### 4. Download TorizonOS image

Download the image for your target module at (inside witte folder):  
https://developer.toradex.com/software/toradex-embedded-software/toradex-download-links-torizon-linux-bsp-wince-and-partner-demos/#torizon-os-7

### 5. Configure tcbuild.yaml

Copy the sample `tcbuild.yaml` file from this repository to the `witte` folder and adjust it according to your target module.

### 6. Splash screen (optional)

Add a 1024x600 PNG image named `custom-splash-screen.png`. If you don't want a custom splash screen, comment out the line in `tcbuild.yaml`:
```yaml
# splash-screen: custom-splash-screen.png
```

### 7. Final structure

```
~/tcbdir/witte/
├── custom-splash-screen.png                              (optional)
├── device-trees/                                         (this repository)
├── linux/                                                (Toradex kernel)
├── tcbuild.yaml
├── torizon-docker-verdin-am62-Tezi_7.4.0+build.28.tar
├── torizon-docker-verdin-am62p-Tezi_7.4.0+build.28.tar
├── torizon-docker-verdin-imx8mm-Tezi_7.4.0+build.28.tar
└── torizon-docker-verdin-imx8mp-Tezi_7.4.0+build.28.tar
```

### 8. Run build

```bash
torizoncore-builder build
```

## License

SPDX-License-Identifier: GPL-2.0-or-later OR MIT

## Contact

**Witte Technology LTDA**  
https://wittetech.com/
