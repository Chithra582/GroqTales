---
name: character-consistency-tracker
description: Maintains persistent character visual embeddings, style descriptors, and narrative traits across comic issues.
---

# Character Consistency Tracker

## Overview
The `character-consistency-tracker` skill manages persistent character identity throughout episodic stories and multi-page comics. It tracks phenotypic visual attributes, outfit palettes, relational histories, and personal motifs to prevent character drift between panel generations.

## Core Capabilities
- **Phenotypic Anchor Management**: Stores facial structure, eye color, hair texture, skin tone, and signature physical markers.
- **Wardrobe & Palette Enforcement**: Maintains canonical clothing sets with color hex codes and accessory definitions.
- **Cross-Panel Consistency Auditing**: Calculates visual similarity indices between newly generated panel prompts and reference character sheets.
- **Relational Memory**: Tracks evolving character relationships, wounds, inventory items, and costume changes across issues.

## Inputs
- `character_id`: Unique character identifier.
- `panel_description`: Target scene description for the character.
- `temporal_context`: Active chapter or issue index.

## Outputs
- `anchored_prompt_fragment`: Character-specific prompt tokens ensuring visual continuity.
- `negative_prompt_fragment`: Negative tokens preventing unwanted stylistic or physical variations.
- `consistency_confidence`: Numerical rating evaluating alignment with canonical character specifications.
