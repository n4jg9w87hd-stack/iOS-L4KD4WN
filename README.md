# iOS-L4KD4WN
L4KD4WN

# iPhone Lockdown

Apple-supported configuration profile templates for a supervised iPhone.

## Goal

This repository is designed to reduce unwanted network-adjacent configuration and sharing changes:

- Disable AirDrop
- Prevent Bluetooth settings modification
- Disable iPhone Mirroring
- Prevent cellular-plan changes
- Prevent per-app cellular-data setting changes
- Prevent Personal Hotspot setting changes
- Prevent proximity password requests/sharing
- Prevent proximity setup to a new Apple device
- Prevent unpaired external boot/recovery behavior

## Important limitation

This does **not** make an iPhone mathematically impossible to connect to, compromise, or control. iOS security boundaries still apply.

Several restrictions require the iPhone to be **supervised and enrolled in device management**. A normal App Store app cannot enforce these system-wide restrictions.

The Wi-Fi allow-list is intentionally a separate template. Do not deploy it blindly: Apple notes that a device restricted to Wi-Fi networks installed by a Wi-Fi payload can lose management connectivity when the approved network is unavailable.

## Files

- `profiles/lockdown.mobileconfig` - core restrictions.
- `profiles/wifi-allowlist-template.mobileconfig` - optional Wi-Fi template.
- `docs/supervision.md` - supervision notes.
- `docs/limitations.md` - what this project can and cannot enforce.
- `scripts/validate.sh` - basic XML/profile validation.

## Deployment

Use an Apple-supported device-management workflow such as Apple Configurator or an MDM service.

Do not deploy this profile to a device you do not own or administer.

Before applying restrictions, make a backup and verify that you have a recovery/management path.

## Verification

After deployment, verify:

1. iPhone Mirroring is unavailable.
2. AirDrop is unavailable.
3. Bluetooth settings cannot be modified by the user.
4. Cellular-plan settings cannot be modified.
5. Personal Hotspot settings cannot be modified.
6. Proximity password sharing/setup is restricted.

Exact availability depends on the iOS release and whether the device is supervised.
