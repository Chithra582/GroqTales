---
name: narrative-branching-generator
description: Generates multi-choice interactive story chapters, plot arcs, and character dialogues with ultra-fast Groq LPU latency.
---

# Narrative Branching Generator

## Overview
The `narrative-branching-generator` skill ingests high-level story concepts, genre parameters, and character rosters to generate episodic narrative chapters, branching decision trees, and immersive dialogue interactions powered by high-throughput LPU inference.

## Core Capabilities
- **Plot Structure Generation**: Formulates structured three-act narrative arcs (Setup, Confrontation, Resolution) tailored to selected genres.
- **Dynamic Branching Nodes**: Produces distinct narrative choice points allowing readers to steer storylines toward divergent outcomes.
- **Dialogue Scripting**: Generates voice-tailored character speech reflecting distinct dialects, emotional states, and subtext.
- **Pacing Optimization**: Analyzes narrative momentum and maintains sentence variety to optimize engagement.

## Inputs
- `premise`: Core story concept or conflict description.
- `genre`: Target literary genre (`scifi`, `fantasy`, `cyberpunk`, `mystery`, `slice_of_life`).
- `characters`: Array of participating characters and their motivations.
- `branching_depth`: Number of interactive decision paths to construct.

## Outputs
- `chapter_text`: Formatted story prose ready for reading or comic panel conversion.
- `branching_options`: Array of decision options with corresponding narrative consequences.
- `pacing_score`: Numerical score assessing action-dialogue equilibrium.
