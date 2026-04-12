# mesoamerican_style — Context Pack

**Version:** 1.0.0  
**Purpose:** Provide structured, comprehensive reference context for AI-driven generative outputs (image prompts, shader art, JavaScript generative design, GLSL art). This repo is intentionally *not* an app; it is a context/database repo meant to be mixed with other repos or consumed directly by AI systems.

---

## What to Use This For

- Prompt engineering for Mesoamerican-inspired imagery and symbols
- Visual constraints (culture-specific motifs, composition rules, style signals)
- Color palettes grounded in actual stone, jade, obsidian, cinnabar, maize pigments
- Generative systems mappings (glyph tiling, step-fret geometry, scroll patterns, relief carving)
- Cultural accuracy guidance to distinguish between 8 covered Mesoamerican traditions
- Shader (GLSL/WebGL) module ideas and parameter sets
- JavaScript canvas pattern generators

---

## Cultures Covered

| Culture                      | Primary Focus                                   | Key File                           |
|------------------------------|-------------------------------------------------|------------------------------------|
| **Aztec (Mexica)**           | Codex, calendar, featherwork, stone sculpture   | `cultures/aztec.md`               |
| **Maya (Classic + Post)**    | Hieroglyphs, Long Count, ceramics, corbeled arch| `cultures/maya.md`                |
| **Olmec**                    | Colossal sculpture, jade, were-jaguar           | `cultures/olmec.md`               |
| **Teotihuacan**              | Murals, Tlaloc, city grid, talud-tablero        | `cultures/teotihuacan.md`         |
| **Zapotec**                  | Funerary urns, Monte Albán, Cocijo              | `cultures/zapotec.md`             |
| **Mixtec**                   | Codex strips, gold metalwork, turquoise mosaic  | `cultures/mixtec.md`              |
| **Toltec**                   | Warrior columns, Chac Mool, procession friezes  | `cultures/toltec.md`              |
| **Totonac / Gulf Coast**     | Interlocking scroll, niched pyramid, smiling figurines | `cultures/totonac_gulf_coast.md` |

---

## Recommended Reading Order

1. **`STYLE_GUIDE.md`** — universal visual principles + culture comparison table
2. **`cultures/{target}.md`** — deep reference for your target culture
3. **`motifs/motifs.json`** — motif catalog with culture tags
4. **`palette/palettes.json`** — culture-specific color palettes
5. **`symbols/deities.json`** — deity visual attributes
6. **`symbols/calendars.json`** — calendar systems and cosmological diagrams
7. **`symbols/cosmology.json`** — world model and directional systems
8. **`prompts/prompt_templates.md`** — ready-to-use prompt templates
9. **`prompts/negative_prompts.md`** — what to avoid
10. **`generative/shader_hints.md`** — GLSL/WebGL patterns
11. **`generative/js_visual_patterns.md`** — JavaScript Canvas patterns
12. **`EXAMPLES.md`** — 10 worked generative examples

---

## Additional Reference Files

- **`materials/materials.json`** — stone types, pigments, surface treatments, render hints
- **`architecture/architecture.md`** — temple types, profiles, and decorative patterns
- **`ceramics/ceramics.md`** — ceramic traditions per culture
- **`sculpture/sculpture.md`** — relief carving and sculptural conventions

---

## License Note

This is a creative reference pack based on historical/archaeological knowledge. Avoid copying protected modern artworks 1:1. Academic and creative use encouraged.

---

Pack version: **1.0.0**