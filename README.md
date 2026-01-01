# IPE Carrier Board - Device Tree Overlays

Device Tree Overlays for the **IPE Carrier Board** by Witte Technology, compatible with Toradex Verdin modules.

## ⚠️ Important: Select the Correct Branch

This repository uses **separate branches** for each TorizonOS version. The `master` branch contains only this documentation.

### Available Branches

| Branch | TorizonOS | Kernel | Status |
|--------|-----------|--------|--------|
| [`torizon-7.x_kernel-6.6`](../../tree/torizon-7.x_kernel-6.6) | 7.x (Scarthgap) | 6.6.x | ✅ Active |
| [`torizon-6.x_kernel-5.15`](../../tree/torizon-6.x_kernel-5.15) | 6.x (Kirkstone) | 5.15.x | ✅ Active |

## Quick Start

### 1. Check your TorizonOS version

On your Verdin module, run:

```bash
cat /etc/os-release | grep VERSION_ID
```

### 2. Clone the correct branch

**For TorizonOS 7.x:**

```bash
git clone -b torizon-7.x_kernel-6.6 https://github.com/user/repo.git device-trees
```

**For TorizonOS 6.x:**

```bash
git clone -b torizon-6.x_kernel-5.15 https://github.com/user/repo.git device-trees
```

### 3. Follow the setup guide

Each branch contains a complete README with:

- Available overlays for your TorizonOS version
- Step-by-step setup instructions
- Sample `tcbuild.yaml` configuration
- Pin mapping reference

## Supported Modules

| Module | TorizonOS 7.x | TorizonOS 6.x |
|--------|:-------------:|:-------------:|
| Verdin iMX8M Plus | ✅ | ✅ |
| Verdin iMX8M Mini | ✅ | 🔜 |
| Verdin AM62 | 🔜 | 🔜 |
| Verdin AM62P | 🔜 | 🔜 |

## Why Separate Branches?

Device Tree Overlays are **kernel-specific**. Using an overlay built for kernel 6.6 on a system running kernel 5.15 (or vice-versa) will cause errors or unexpected behavior.

By maintaining separate branches:

- ✅ Each overlay is tested for its specific kernel version
- ✅ You always get compatible code for your system
- ✅ Updates to one version don't break another

## License

SPDX-License-Identifier: MIT

## Contact

**Witte Technology LTDA**  
https://wittetech.com/
