# Updating WP 8.1 FFUs to GDR2



This guide will let you update your stock WP 8.1 FFU to GDR2, it uses the "official" way that is demonstrated in MS Documentation


## Notes:


- Created FFUs are **unsigned** so an **Unlocked Bootloader** will be required to flash them
- WP8 FFUs are **not** supported with updating to W10M.

- Download the GDR2 cabs and filter them for your device as described here: https://youtu.be/xSK-RiMDenM
- [WPInternals](https://github.com/ReneLergner/WPinternals), [WP8 Common Tools](https://github.com/Empyreal96/Updating-WP-FFUs-Guide/blob/main/WP8_Tools.7z?raw=true) and [thor2/Windows Device Recovery Tool](https://support.microsoft.com/en-us/windows/windows-device-recovery-tool-faq-2b186f06-7178-ed11-4cb6-5ed437f0855b) are **required**.
- A special XML file is also **Required**, to make this easy I wrote [UpdateInput Generator](https://github.com/Empyreal96/Updating-WP-FFUs-Guide/blob/main/UpdateInputGen.7z?raw=true) to make this super easy

- I strongly recommend to make a copy of the stock FFU before doing this.


## Creating the new image:


1. Extract [WP8_Tools.7z](https://github.com/Empyreal96/Updating-WP-FFUs-Guide/blob/main/WP8_Tools.7z?raw=true) and [UpdateInput Generator](https://github.com/Empyreal96/Updating-WP-FFUs-Guide/blob/main/UpdateInputGen.7z?raw=true) to a folder of your choice. 
*(you can place UpdateInput Gen in the same folder as WP8 Tools if you wish)*

2. Open Command Prompt as Admin and navigate to UpdateInput Generator's folder, then run this command:
   - `UpdImageGen.exe -i "Path to filtered cabs" -o "Path to output folder"`

*Keep note of where you saved the UpdateInput.xml file*

3. in the WP8 Tools folder run the command:
   - `imageapp.exe "path to ffu" /UpdateInputXML:"Path to UpdateInput.xml"`

*It may seem stuck as several places but just wait, it will take some time*


## Flashing the new image:


1. Plug phone into PC while it's booted

2. Navigate to where 'thor2' is located (usually `C:\Program Files (x86)\Microsoft Care Suite\Windows Device Recovery Tool\`)
3. Type: `thor2 -mode rnd -bootflashapp` *(alternatively you can use WPInternals to do this)*
4. Type: `thor2 -mode uefiflash -ffufile "path to ffu"` *(you can append with -erase_data if you wish but it won't have an effect in this guide)*
5. Type: `thor2 -mode rnd -reboot`

*(You will reboot back into Flash Mode, this is expected*

6. Relock Bootloader with WPInternals



Your device should now boot to the updated build
