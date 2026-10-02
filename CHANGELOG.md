# Changelog (OctoWoW build) – XPerl_Options

Differences from upstream [Redbu11dev/X-Perl-UnitFrames](https://github.com/Redbu11dev/X-Perl-UnitFrames) (folder `XPerl_Options`). Changed places in the code are marked with `[patch]`.

## Releases

Version scheme: `<upstream version>-octo.<n>`. Each release is a git tag `v<version>`; older versions can be downloaded from the tag page on GitHub.

### 1.9.6.1-octo.1 – 2026-10-03
- First tagged release with the changes listed below.

## Changes

### XPerl_FrameOptions.lua
- **Slider fallback:** OctoWoW's FrameXML does not provide `OptionsFrame_DisableSlider`/`EnableSlider`, so XPerl_Options crashed on every load. It now falls back to a built-in copy of the original implementation.
- **Character list sorted:** `pairs()` has no fixed order in Lua 5.0. The list was built twice (menu and click), so clicking one character could load another character's settings. It is now sorted, `MyIndex` is determined afterwards and preselected when opening.
- **"Copy settings" fixed:** deep copy instead of linking sub-tables; the new table is also stored in the per-character slot; positions are saved first and applied afterwards. Requires the matching XPerl core (`XPerl_DeepCopy`, `XPerl_GlobalSlot`, `XPerl_CapturePositions`, `XPerl_ApplyPositions`).
