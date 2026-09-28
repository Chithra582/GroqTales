---
name: comic-storyboard-sequencer
description: Converts narrative beats into multi-panel comic storyboard layouts with scene descriptions, camera angles, and text captions.
---

# Comic Storyboard Sequencer

## Overview
The `comic-storyboard-sequencer` skill translates narrative prose into sequential art storyboards. It calculates optimal panel splits, defines dynamic cinematography, positions dialogue speech bubbles, and prepares diffusion-ready prompt specifications for image rendering pipelines.

## Core Capabilities
- **Beat Decomposition**: Analyzes narrative paragraphs and segments them into coherent visual moments (3 to 9 panels per page).
- **Cinematic Framing**: Automatically assigns camera angles (wide establishing shot, medium reaction, close-up intensity, low-angle dominance).
- **Dialogue & Caption Placement**: Allocates speech balloons, narration overlays, and sound effects to prevent visual clutter.
- **Visual Prompt Formulation**: Translates scene descriptions into detailed generative diffusion prompts incorporating lighting, environment, and art style.

## Inputs
- `story_text`: Raw prose or script of the narrative chapter.
- `target_panels`: Desired panel count per page (default: 4 or 6).
- `art_style`: Aesthetic style (e.g., `western_comic`, `manga`, `cyberpunk_noir`, `watercolor`).

## Outputs
- `storyboard_layout`: Array of ordered panel specifications with composition guidelines.
- `diffusion_prompts`: Standardized image prompts optimized for visual diffusion models.
- `dialogue_overlays`: Speech balloon text mapped to panel coordinates.
