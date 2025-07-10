# Alioth Device Configuration Notes

This configuration is set up for building KernelSU-Next kernel for the Xiaomi Mi 11X / Redmi K40 (alioth) device.

## Current Configuration

- **Device**: Alioth (Xiaomi Mi 11X / Redmi K40)
- **Platform**: Snapdragon 870 (SM8250)
- **Kernel Source**: LineageOS/android_kernel_xiaomi_sm8250
- **Branch**: lineage-21 (Android 14)
- **Defconfig**: vendor/alioth_defconfig
- **Kernel Image**: Image
- **KernelSU**: KernelSU-Next

## Potential Issues and Solutions

### Defconfig Name
If the build fails with defconfig not found, try these alternatives in `config.env`:
- `KERNEL_CONFIG=alioth_defconfig`
- `KERNEL_CONFIG=vendor/munch_defconfig` (if alioth shares config with munch)
- `KERNEL_CONFIG=sm8250_defconfig`
- `KERNEL_CONFIG=lineage_alioth_defconfig`

### Branch Name
If the lineage-21 branch doesn't exist, try:
- `KERNEL_SOURCE_BRANCH=lineage-20`
- `KERNEL_SOURCE_BRANCH=lineage-19.1`
- `KERNEL_SOURCE_BRANCH=main`

### KernelSU Integration
The configuration uses KernelSU-Next instead of standard KernelSU:
- Automatically clones from KernelSU-Next/KernelSU-Next repository
- Enables KSU patches for proper integration
- Adds necessary kernel options (kprobes, overlayfs)

## Build Process
1. Fork this repository
2. Verify/adjust configuration in `config.env` if needed
3. Go to Actions tab
4. Run "Build Kernel" workflow
5. Download the AnyKernel3 package from the build artifacts
6. Flash via custom recovery (TWRP/OrangeFox)