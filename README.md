# cjktty-patches

Patches from [Gentoo-zh/linux-cjktty](https://github.com/Gentoo-zh/linux-cjktty) with minor changes.

- Starting with 5.10 the kernel config option `CONFIG_FONT_16x16_CJK` has been renamed to `CONFIG_FONT_CJK_16x16`.
- To have a larger font on high resolution screens, you probably want to apply 32x32 font data patch.
- The patch built-in fonts expect to work with 8x16 or 16x32 fonts. When changing to other font sizes, characters may not display correctly.

## Changes

### 2022.08.01 / 5.19

- Resync for linux-5.19.y
- Update font data to GNU Unifont 14.0.04
- Update double width tables to Unicode 14.0.0
- Fix cutoff issue for double width glyphs from Unifont (e.g.`①  ②  ③ `)
- Avoid unnecessary check of characters width
- Remove workaround from [Gentoo-zh/linux-cjktty@6caf83a](https://github.com/Gentoo-zh/linux-cjktty/commit/6caf83a638886220d1e1880c92e8b18243c3965a)

### 2022.05.23 / 5.18

- Resync for linux-5.18.y
- Fix build warnings with GCC 12 (`-Wbidi-chars=unpaired`)

### 2022.03.21 / 5.17

- Resync for linux-5.17.y
- Update font data to GNU Unifont 14.0.02
- Revert scroll acceleration code (upstream)
  - [torvalds/linux@1148836](https://github.com/torvalds/linux/commit/1148836fd3226c20de841084aba24184d4fbbe77)

### 2022.01.10 / 5.16

- Resync for linux-5.16.y
- Remove scroll acceleration code (upstream)
  - [torvalds/linux@b3ec8cd](https://github.com/torvalds/linux/commit/b3ec8cdf457e5e63d396fe1346cc788cf7c1b578)

### 2021.09.17 / 5.14.5

- Replace original 16x16 font with GNU Unifont for better unicode support
- Update font data to GNU Unifont 14.0.01

### 2021.02.22 / 5.11

- Resync for linux-5.11.y
- Update CJK 32x32 font data to GNU Unifont 13.0.06
- Reduce checkpatch.pl complaints
- Remove charcount changes since it has been implemented (upstream)
  - [torvalds/linux@4ee5730](https://github.com/torvalds/linux/commit/4ee573086bd88ff3060dda07873bf755d332e9ba)
  - [torvalds/linux@a1ac250](https://github.com/torvalds/linux/commit/a1ac250a82a5e97db71f14101ff7468291a6aaef)

### 2020.12.14 / 5.10

- Resync for linux-5.10.y
- Update glyphs for some Chinese punctuation marks
- Support display rotation
- Support `setfont` (Note: different font size can cause issues with this patch which expects to work with 8x16 / 16x32 font)
- Fix display for some single width characters
- Fix line wrap for double width characters (<https://github.com/zhmars/cjktty-patches/issues/1>)
- Workaround from [Gentoo-zh/linux-cjktty@6caf83a](https://github.com/Gentoo-zh/linux-cjktty/commit/6caf83a638886220d1e1880c92e8b18243c3965a)
- Support 32x32 font size for high resolution screens (experimental, make sure the font data patch is applied)

### 2020.09.18 / 5.8.10

- Resync for linux-5.8.10
- Remove soft scrollback code (upstream)
  - [torvalds/linux@5014547](https://github.com/torvalds/linux/commit/50145474f6ef4a9c19205b173da6264a644c7489)

## Credits

- [youbest](http://blog.chinaunix.net/uid/436750.html) for [original univt patches](https://github.com/zhmars/univt-patches/tree/master/v2.6)
- [Gentoo-zh/linux-cjktty](https://github.com/Gentoo-zh/linux-cjktty) for original cjktty patches
- [AOSC-Dev/aosc-os-abbs](https://github.com/AOSC-Dev/aosc-os-abbs) for some univt's modifications
- [GNU Unifont](https://unifoundry.com) for font data
- [Terminus Font](http://terminus-font.sourceforge.net) for font data
