# AGENTS.md - handoff for any AI (Claude, Grok, Codex...)

**What this is:** `pokeplatinum-3ds` is a native New 3DS port of Pokemon Platinum built from the pret/pokeplatinum decompilation (design by GabeSud0, GPL-3.0). Unlike `3ds-platinum` (pspoke-based), this builds NitroSDK/NitroSystem for the 3DS and provides virtual DS hardware (2D renderer, a 3D geometry engine feeding the 3DS GPU, software DS sound, second-CPU services), reading game files from a data pack made from the user's own ROM. HGSS is its stated long-term target; the SoulSilver port (`unowncollectables/Pokemon-Soulsilver-New3ds`, see its AGENTS.md) currently uses pspoke instead and can borrow ideas and code from here.

**Rules:** never commit ROMs, extracted assets, saves or builds (CI fails if game code is uploaded: `tools/check_ci_artifacts.py`); back up saves; work in a branch, PR to main. Read `CONTRIBUTING.md` and `AI_DISCLOSURE.md` (AI assistance must be disclosed).

**Where things are:** `3ds_port/game` the 3DS program + PC runner; `3ds_port/nitro`, `3ds_port/nitrosystem` the Nitro libs; `3ds_port/pak` data-pack reader; `builder/` ROM -> data pack (`verify_rom.py`, `extract_rom.py`, `pack.py`); `patches/` changes over the decomp; `tools/` bootstrap + build scripts (`build_linux.sh`, `build_windows_msys2.sh`) and the WideArt editor; `wideart/`; `docs/` (REMASTER, WIDE_ART, PAK_FORMAT); `upstream.lock` pins pret/pokeplatinum.

**Build:** `python tools/bootstrap.py && make game` (add `make game-cia ROM=...` for a CIA); `make test` runs the PC suites. Details in README.md. Output goes to `sdmc:/3ds/pokeplatinum/`.

**Status:** playable on hardware with remaster display, stereo 3D, 60 fps field (tuning). Wishlist: Wi-Fi, follower, lighting, SoulSilver/HeartGold.
