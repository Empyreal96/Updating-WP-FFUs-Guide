# Updating W10M FFUs (Unofficial method)

This guide will let you update your stock W10M FFU to a higher OS build

## Notes:
- Created FFUs are **unsigned** so an **Unlocked Bootloader** will be required to flash them
- WP8 FFUs are **not* supported with updating to W10M. (Updating WP 8.1 FFUs to GDR2 will hopefully come soon)
- You will need filtered cabs for your device already stored on your PC.
- [WPInternals](), [Windows Phone Common Tools]() and [thor2]() are **required**.
- To make an FFU on the latest build you may need to make several runs of this guide, first to update to 14393, then mount the new 14393 FFU and update that to 15254. You will only need to flash the 15254 FFU.

## Creating the new image:

1. Extract [WP_Tools.7z](), open Command Prompt as Admin in extracted the folder.
2. Run following commands in order:
   - `wpimage mount "path to ffu"`
   (*take note of the PhysicalDrive it is mounted at, Mine was PhysicalDrive1*)
   - `updateapp install "path to filtered update cabs"`
   - `wpimage dismount -physicalDrive \\.\PhysicalDrive1 -imagePath "path to output ffu" -noSign`

## Flashing the new image:

1. Plug phone into PC while it's booted
2. Navigate to where 'thor2' is located (usually `C:\Program Files (x86)\Microsoft Care Suite\Windows Device Recovery Tool\`)
3. Type: `thor2 -mode rnd -bootflashapp`
4. Type: `thor2 -mode uefiflash -ffufile "path to output ffu"` (you can append with -erase_data if you wish but it won't have an effect in this guide)
5. Type: `thor2 -mode rnd -reboot`
*(You will reboot back into Flash Mode, this is expected)*
6. Unlock Bootloader with WPInternals
*(First Boot will freeze on boot, wait until WPInternals tells you the unlock was successful)*
7. Hold the power button to reboot, and perform a reset

Your device should now boot to the updated build