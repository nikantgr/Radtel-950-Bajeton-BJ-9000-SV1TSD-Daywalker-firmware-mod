# **⚠️ IMPORTANT WARNINGS — READ BEFORE PROCEEDING**

**⚠️ THERE IS NO GUARANTEE THAT THE FIRMWARE WILL WORK CORRECTLY ON YOUR PARTICULAR RADIO, EVEN IF THE MODEL AND FIRMWARE VERSION APPEAR TO MATCH.**

**⚠️ YOU PROCEED ENTIRELY AT YOUR OWN RISK. YOU ARE RESPONSIBLE FOR VERIFYING YOUR RADIO VERSION, SELECTING THE CORRECT FIRMWARE, MAKING BACKUPS, AND FOLLOWING THE INSTALLATION PROCEDURE.**

**⚠️ I ACCEPT NO LIABILITY OR RESPONSIBILITY FOR ANY DAMAGE, MALFUNCTION, DATA LOSS, BRICKED RADIO, OR OTHER CONSEQUENCES ARISING FROM THE USE OF THIS FIRMWARE, THIS GUIDE, OR THE FLASHING PROCEDURE. DO NOT HOLD ME RESPONSIBLE FOR ANY RESULT.**

**⚠️ RADTEL, BAJETON, RADIODDITY ARE NOT RESPONSIBLE FOR UNOFFICIAL THIRD-PARTY FIRMWARE OR ANY CONSEQUENCES RESULTING FROM ITS INSTALLATION OR USE. THIS IS NOT AN OFFICIAL RADTEL OR BAJETON FIRMWARE RELEASE OR SUPPORT DOCUMENT.**

**⚠️ NO WARRANTY IS PROVIDED. USE OF THIS FIRMWARE IS ENTIRELY VOLUNTARY. BY DOWNLOADING, INSTALLING, OR USING IT, YOU ACCEPT ALL ASSOCIATED RISKS.**

**DO NOT PROCEED UNLESS YOU UNDERSTAND THESE RISKS AND ARE PREPARED TO ACCEPT THE POSSIBILITY OF PERMANENTLY LOSING THE USE OF YOUR RADIO.**


---

## English video: https://youtu.be/elDeHwtF6hM
## Greek video: https://youtu.be/Fa2s6wXo_v0

# SV1TSD Firmware for the Radtel RT-950 Pro / Bajeton BJ9000

Ultra 02 by SV1TSD builds on official Radtel V0.30 and adds faster memory and VFO scanning. Choose the original dark display or the DayWalker green LCD-style display.

🟢 **Want to contribute to the channel?** You can support my work directly at https://www.white-tree.net/donate (100% goes to me), or buy me a coffee at https://www.buymeacoffee.com/SY1EBE ☕

Every bit helps me keep experimenting, building, and sharing! 🙏

## Choose your download

Both editions use the same scan procedure and timings.

| Edition | Display | On-radio signature | Firmware file |
| --- | --- | --- | --- |
| **Dark 02** | Original factory colours | `SV1TSD-2` | [Download Dark 02](RT_950Pro_V0.30_261112-SV1TSD-ultra-02.BTF) |
| **DayWalker 02** | Green LCD-style colours with black lettering | `SV1TSDw2` | [Download DayWalker 02](RT_950Pro_V0.30_261112-SV1TSD-ultra-DayWalker-02.BTF) |

These files are based on **RT_950Pro_V0.30_261112.BTF**. Verify the exact model and hardware revision of your radio before installing. Compatibility with other RT-950 variants, Radioddity Trivox, and other rebrands has not been verified.

## What changed

- Faster scanning through saved memories, with an early signal-strength check to reduce time spent on quiet channels.
- Faster VFO scanning, with approximately 30 ms of programmed waiting per frequency step.
- Memory scanning at SQL 0 also uses the early signal-strength check.
- DayWalker adds a green LCD-style palette, black lettering, lighter active A/B/C and menu selections, darker spectrum indicators, a black spectrum trace, and darker FM broadcast signal bars and antenna icon.

### Scan speed comparison

A millisecond is one thousandth of a second. The times below describe the programmed wait at each channel or frequency after the receiver is ready. Tuning, processing, and pauses on signals add to the time you observe.

| Scan situation | Original V0.30 scan timing | Ultra 02, both editions |
| --- | --- | --- |
| Saved memory, clearly low signal strength | Coarse two-count timer, approximately 100–200 ms | About **10 ms** before the next scan decision |
| Saved memory, borderline or strong signal | Same coarse timer | **10 ms** initial check plus **10 ms** more, about **20 ms total** |
| Saved memory with SQL 0 | Same coarse timer, with squelch open | Same **10 / 20 ms** signal-strength method |
| VFO, any SQL setting | Same coarse timer | About **30 ms** per frequency step |

During continuous scanning, about 200 ms per step is the stock timing estimate used in the analysis. This corresponds to roughly five steps per second before other overhead.

| Quiet-scan comparison | Stock timing estimate | Ultra 02 timing ceiling |
| --- | --- | --- |
| Memory scan using the 10 ms path | Roughly **5 channels/second** | Up to **100 channels/second** from the wait alone |
| VFO scan | Roughly **5 steps/second** | Up to **33 steps/second** from the wait alone |

**These figures are theoretical timing comparisons. They are not measured scan rates.** Actual scanning will be slower because the radio must tune and process each step.

### How your squelch setting affects scanning

With **SQL 1–9**, including SQL 3, the early signal-strength check chooses between the shorter and longer wait. The normal squelch check then decides whether the scanner should advance or begin holding on activity.

With **SQL 0**, a memory with clearly low signal strength is skipped after the early check. A memory that passes the check gets the full 20 ms wait and can enter the normal open-squelch hold behavior.

Strong interference can pass the signal-strength check. Weak or short transmissions can be missed with faster scanning. If the receiver-ready check times out, the scanner uses the full delay for that mode after the timeout.

### DayWalker display

| Screen element | Dark 02 | DayWalker 02 |
| --- | --- | --- |
| General appearance | Factory dark theme | Classic green LCD-style theme |
| Main lettering | Factory colours | Black |
| Selected A/B/C bank and menu row | Factory highlight | Lighter green highlight |
| Spectrum RSSI indicators | Factory colours | Dark green |
| Spectrum trace | Factory colours | Black |
| FM broadcast signal bars and antenna | Factory colours | Black |

## Installation

**BEFORE INSTALLING: Back up your channels and settings. Make sure the battery is sufficiently charged. Verify the firmware version and hardware version shown by the radio. Keep a known-good official firmware file and the recovery instructions for your unit available.**

1. Choose the Dark 02 or DayWalker 02 file for your compatible RT-950 Pro / BJ9000.
2. Connect the radio to your Windows PC using its programming cable. Close other programs using the cable.
3. Open the RT-950 updater, select the cable's COM port, and load your chosen BTF file.
4. Follow the updater and radio manufacturer's procedure for entering update mode and starting the transfer.
5. Keep the radio powered and connected until the updater finishes. Restart the radio and check its build signature.
6. Check reception and scanning using your usual memory list and squelch setting.

**DO NOT DISCONNECT THE CABLE, SWITCH OFF THE RADIO, OR INTERRUPT THE PROCESS WHILE THE FIRMWARE IS BEING WRITTEN.**

If the radio fails to boot, use its documented recovery flash procedure with the known-good official firmware.

**IMPORTANT: Recovery is not a guarantee that every failed flash can be repaired. A radio may become unresponsive or unrecoverable. Do not rely on the Recovery function as protection against every possible failure.**

## Verification and test status

Both V0.30 images passed offline file verification and simulated scan checks. Each retains the original V0.30 file size. Boot, display appearance, and on-air behavior of these V0.30 builds still require confirmation on a physical radio. Earlier V0.29 test results do not establish V0.30 hardware compatibility.

| Edition | Size | SHA-256 |
| --- | --- | --- |
| Dark 02 | 394,216 bytes | `c70b263e0638aad3b8eb4a1ab4cfd3df6d9c1122a9571c599a09a35b1a15b836` |
| DayWalker 02 | 394,216 bytes | `5ec36784fb0f83b903d481a68c1d52f4b53dc3b6724077c4b5b01b3f7f0700f7` |


## Copyright and Licensing

Copyright © 2026 Nikos Kantarakias.

Unless explicitly stated otherwise, all original contributions, modifications, documentation, and other materials created by me in this repository are reserved by their respective copyright holder(s).

No permission is granted to redistribute, modify, commercially exploit, or create derivative works from my original materials without prior written permission.

This repository may contain original firmware components, manufacturer-provided firmware, or other third-party materials. Such materials remain the property of their respective copyright holders and are not relicensed by this project.

This is an unofficial, independent project. It is not affiliated with, endorsed by, or supported by any manufacturer or other third-party rights holder whose products or materials may be referenced here.
