# Scrutiny (HP P440ar/cciss Fork)

This is a specialized fork of [AnalogJ/scrutiny](https://github.com/AnalogJ/scrutiny) designed to fix support for HP P440ar/cciss and other RAID controllers that require specific device type syntax (e.g., `cciss,0`, `megaraid,1`).

## The Fix

The core issue in the upstream project is that the collector overwrites user-configured device types with auto-detected values (often `sat` or `scsi`), causing `smartctl` commands to fail for these specific controllers.

This fork modifies the collector to **preserve user-configured device types** defined in `collector.yaml`.