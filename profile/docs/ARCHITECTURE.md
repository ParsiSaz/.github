# ⚙️ ParsiSaz Architecture & Focus Areas

This document outlines the architectural focus areas, technical reverse-engineering pipelines, and typography toolchains maintained by **ParsiSaz**.

---

## 📂 Ecosystem Architecture

```
                             ┌────────────────────────┐
                             │       ParsiSaz         │
                             │  Persian Localization  │
                             └───────────┬────────────┘
                                         │
         ┌───────────────────┬───────────┴───────────┬───────────────────┐
         ▼                   ▼                       ▼                   ▼
  [ Game Patches ]    [ Localization Tools ]  [ System & Typography ] [ Documentation ]
  • Kenshi            • Parsik (GUI Manager)  • RTL Text Shapers      • Terminology Lexicon
  • Project Zomboid   • farsiSaz (Patcher)    • Font Atlas Injectors  • Engine Guides
  • Darkest Dungeon 2 • String Extractors     • ZWNJ Handlers         • Modding Standards
  • Stronghold Series • Archive Unpackers     • Bitmap Font Kerners   • Community Standards
```

---

## 🧩 Core Technical Challenges

Persian video game localization presents unique technical obstacles that require custom reverse-engineering solutions:

1. **Right-to-Left (RTL) Layout & Text Direction**:
   - Most legacy and indie game engines assume left-to-right (LTR) scripts.
   - ParsiSaz builds pre-processing and dynamic in-memory string reversers utilizing bidirectional layout algorithms.
2. **Cursive Connected Shaping**:
   - Persian characters change glyph shape depending on their position (initial, medial, final, isolated).
   - Custom shapers map standard Unicode strings to positional font ligature slots.
3. **Font Atlas & Texture Sheet Injection**:
   - Games with proprietary or rasterized font atlases frequently lack non-Latin character sets.
   - We generate extended TrueType/OpenType and high-DPI bitmap font sheets to inject Persian glyph ranges seamlessly.
4. **Zero-Width Non-Joiner (ZWNJ / نیم‌فاصله)**:
   - Preserving accurate grammatical typography while preventing engine line-break glitches.

---

[← Return to Profile README](../README.md)
