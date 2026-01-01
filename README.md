# Ipê Carrier Board - Device Tree Overlays

Device Tree Overlays for the **Ipê Carrier Board** by Witte Technology, compatible with Toradex Verdin modules.

## Compatibility

| Branch | TorizonOS | Kernel |
|--------|-----------|--------|
| `torizon-6.x_kernel-5.15` | 6.8.x | 5.15.x |

## Supported Modules

- ✅ Verdin iMX8M Plus
- 🔜 Verdin iMX8M Mini *(coming soon)*
- 🔜 Verdin AM62 *(coming soon)*
- 🔜 Verdin AM62P *(coming soon)*

## Available Overlays

### Verdin iMX8M Plus

| Overlay | Description |
|---------|-------------|
| `verdin-imx8mp_ipe-board_panel-cap-touch-7-10inch-dsi_overlay.dts` | MIPI-DSI Display 7"/10.1" (1024x600) with SN65DSI83 bridge, PWM Backlight, Goodix GT911 Touch |
| `verdin-imx8mp_ipe-board_panel-cap-touch-10inch-lvds_overlay.dts` | Native LVDS Display 10.1" (1280x800), PWM Backlight, Goodix GT928 Touch |
| `verdin-imx8mp_ipe-board_audio-codec.dts` | TAS2110 Audio Codec via I2S/SAI1 |
| `verdin-imx8mp_ipe-board_enable-2ndfec.dts` | Second Ethernet interface (FEC) |
| `verdin-imx8mp_ipe-board_enable-can.dts` | CAN interfaces with RS pin control |
| `verdin-imx8mp_ipe-board_enable-sodimm-56-as-gpio.dts` | SODIMM 56 configured as GPIO (disables QSPI) |

## Repository Structure

```
device-trees/
└── ipe-carrier-board/
    └── verdin-imx8mp-ipe-board-overlays/
        ├── display-tdo-ts070wsh02ce_overlay.dtsi
        ├── verdin-imx8mp_ipe-board_audio-codec.dts
        ├── verdin-imx8mp_ipe-board_enable-2ndfec.dts
        ├── verdin-imx8mp_ipe-board_enable-can.dts
        ├── verdin-imx8mp_ipe-board_enable-sodimm-56-as-gpio.dts
        ├── verdin-imx8mp_ipe-board_panel-cap-touch-7-10inch-dsi_overlay.dts
        └── verdin-imx8mp_ipe-board_panel-cap-touch-10inch-lvds_overlay.dts
```

## Quick Setup Guide

### 1. Create directory structure

```bash
# Enter your TorizonCore Builder directory
cd ~/tcbdir

# Create a custom folder for this build
mkdir witte && cd witte
```

### 2. Clone this repository

Inside the `witte` directory:

```bash
git clone -b torizon-6.x_kernel-5.15 https://github.com/user/repo.git device-trees
```

### 3. Clone Toradex Linux kernel

Inside the `witte` directory, clone the Linux kernel for your target module.

**For iMX8M Mini and iMX8M Plus:**

```bash
git clone -b toradex_5.15-2.2.x-imx git://git.toradex.com/linux-toradex.git linux
```

### 4. Download TorizonOS image

Download the TorizonOS 6.x image for your target module (inside the `witte` folder):

https://developer.toradex.com/software/toradex-embedded-software/toradex-download-links-torizon-linux-bsp-wince-and-partner-demos/#torizon-os-6

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
└── torizon-core-docker-verdin-imx8mp-Tezi_6.8.4+build.40.tar
```

### 8. Run build

```bash
torizoncore-builder build
```

## License

SPDX-License-Identifier: MIT

## Contact

**Witte Technology LTDA**  
https://wittetech.com/
