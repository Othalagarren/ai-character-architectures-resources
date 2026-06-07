# Vivid3 Character Prompting Guides & Techniques

**Curated for Perfecting Advanced, Vivid, Consistent Character Prompting (June 2026)**

"Vivid3" appears to refer to your advanced (version 3) approach to highly vivid, detailed, and consistent character prompting. This combines precise visual description (Danbooru-style tagging for exact anatomy, appearance, outfits, locations), custom artstyle bases (e.g., Incase sensual painterly blended with dark gothic fantasy, magical effects, cinematic lighting, voluptuous idealized forms), behavioral realism, and structured reasoning for immersive roleplay or image generation.

This file curates high-value GitHub resources and extracted techniques focused on:
- Visual consistency via structured "DNA"-style prompts and placeholders.
- Ultra-realistic character behavior with Chain-of-Thought (COT) reasoning.
- Anti-slop, physical realism, authentic reactions, non-verbal cues, and plot progression.
- Integration with SillyTavern-style systems and dynamic variations (wardrobe, hairstyles, etc.).
- Best practices adaptable to your Danbooru tagging + natural language artstyle modules.

These will help refine Vivid3 prompts for greater vividness, fidelity, consistency across scenes/sessions, and resistance to generic or unrealistic outputs.

## 1. SillyTavern DNA System (Visual Consistency via Prompt Engineering)
**Repo**: https://github.com/kainatquaderee/sillytavern-dna-system

**Core Idea**: Achieve strong visual character consistency in image generation (e.g., SillyTavern or compatible tools) using only prompt engineering — no LoRAs, IP-Adapters, or extra models. Defines a reusable "DNA" for core visual identity with placeholders for dynamic elements.

**Key Techniques for Vivid3**:
- **DNA Template Formula** (adapt for your artstyle bases):
  ```
  Professional photography of a [AGE] year old [GENDER] [OCCUPATION/ROLE], (named [CHARACTER_NAME]:1.2-1.35), {clothing}, [FACIAL_STRUCTURE_DETAILS], hair {hairstyle}, (EYE_DESCRIPTION:1.3), [LIPS_AND_MAKEUP], [BODY_TYPE_AND_SKIN], {accessories}, [YOUR_ARTSTYLE_BASE], dramatic cinematic lighting, sharp focus.
  ```
- **Name Emphasis & Weighting**: Use `(named [NAME]:1.2-1.35)` to strongly anchor identity. Weight key features like eyes `(almond-shaped bright blue eyes with thick lashes:1.3)` or other distinctive traits 1.1–1.35 for emphasis without overpowering.
- **Placeholders for Dynamics**: `{clothing}`, `{hairstyle}`, `{accessories}` allow easy swapping (e.g., via wardrobe/barber systems) while preserving core DNA. Perfect for scene variations or character progression (different outfits, hairstyles, accessories in different phases or locations).
- **Facial/Body Specificity**: Include precise structure (heart-shaped face, high cheekbones, sharp jawline, elongated face for elves, pointed ears, etc.), body type, skin, makeup. Combine with your Danbooru tags for exact anatomy/fidelity (e.g., add `detailed eyes, long hair, voluptuous figure, gothic dress`).
- **Integration**: Store in a "DNA-Book" (JSON). Bind to character cards/descriptions with global variables like `{{getglobalvar::name::[Character Name]}}`. Use master prompts that auto-replace placeholders.

**Examples Adapted for Your Style** (Fantasy/Gothic/Sensual):
- Elven Druidess: `Professional photography of a 120 year old female half-elf druid, (named Bryade Nonna:1.3), {flowing gothic-inspired druid robes with vine embroidery}, heart-shaped face with high cheekbones and subtle pointed ears, hair {long wavy auburn hair with flowers}, (large mystical green eyes with golden flecks:1.35), full lips with natural tint, curvaceous athletic figure with smooth fair skin and subtle freckles, {woodland accessories and satyr-like elements if applicable}, [Incase sensual painterly + dark gothic fantasy artstyle base with magical emerald sparks, ethereal particles, volumetric lighting, moody forest palette], intricate details, sharp focus.`
- Similar for Holstaur, Oni, Dragon wife, etc., swapping DNA elements while keeping core identity weights.

**Value for Vivid3**: Enhances visual vividness and consistency. Use alongside your Danbooru tag lists (categorized by body/skin/head/eyes/ears/limbs/pose/clothing/magical effects) as the `{variable}` backbone, then layer your reusable artstyle natural-language prompt on top for painterly, sensual, gothic, magical effects.

## 2. Poppet RP Framework (Ultra-Realism & Structured Reasoning for Character Behavior)
**Repo**: https://github.com/Huzderu/poppet-rp-framework (SillyTavern preset)

**Core Idea**: Comprehensive prompt engineering framework/preset to eliminate common AI writing failures (echoing, omniscience, plot stagnation, generic emotions, melodrama, unrealistic physics/skills) and enforce ultra-realistic, vivid character behavior in roleplay. Uses a mandatory structured Chain-of-Thought (COT) process before every response.

**Key Techniques for Vivid3**:
- **Mandatory 10-Section COT Template**: Forces systematic evaluation of realism, character consistency, plot progression, technical writing quality, psychology, world-building, and pacing *before* generating output. This adds depth and vividness by making the model reason explicitly about physical constraints, authentic reactions, and progression.
- **Specialized Anti-Slop & Realism Prompts** (integrate into your prompt modules or decision engine hidden reasoning):
  - **Authentic Reactions (Anti-Melodrama)**: Prevent purple prose or exaggerated responses (e.g., avoid "words hit like a physical blow"; use "Not X but Y" contrasts for grounded emotion).
  - **Physical Realism Constraints**: Enforce realistic body capabilities, physics, fatigue, pain responses. Ties perfectly to vivid sensory descriptions without breaking immersion.
  - **Non-Verbal Communication**: Balance dialogue with body language, micro-expressions, posture, environmental interaction for more vivid, cinematic scenes.
  - **Skill Limitations & Economic Reality**: Characters can't magically solve everything; respect training, resources, consequences.
  - **Natural Humor & Levity**: Even serious characters show appropriate levity to avoid one-note grimdark.
  - **Anti-Convenience Protocol**: Block meta or wish-fulfillment shortcuts that break consistency or plot integrity.
  - **Cultural/Authenticity Checks**: Behavior fits setting (fantasy druid grove, gothic manor, etc.) and character background.
- **Anti-Stagnation & Progression**: Built-in checks for plot movement, user engagement, and avoiding repetitive loops.
- **Adaptability**: Works across modern, historical, fantasy settings — ideal for your gothic fantasy, dying grove, manor progression scenarios.

**Value for Vivid3**: The COT structure adds a reasoning layer that produces more vivid, thoughtful, consistent outputs (aligns with your Decision Engine and hidden reasoning layers). Incorporate the specialized realism prompts into your character prompt modules, system prompts, or post-processing rules. Use COT sections in your internal decision process or as activation triggers for phases/meters (e.g., high estrus or jealousy triggers specific realism/authenticity checks).

**Adaptation Ideas**:
- Add a "Vivid3 Realism COT" section to your character JSON or prompt templates: 1. Physical state check (meters, pregnancy, fatigue). 2. Emotional authenticity. 3. Non-verbal opportunities. 4. Plot/phase progression. 5. Consistency with lore/personality. etc.
- Combine with your user restrictions and phase integrity enforcement.

## 3. Synthesis: Perfecting Your Vivid3 Workflow
Combine the above for maximum vividness and consistency:

1. **Visual Layer (DNA + Danbooru + Artstyle)**: Use DNA-style structured template with weighted name/features + your categorized Danbooru tags (body, head/eyes, clothing, magical effects, pose, location like cave grotto/gothic manor) as the base. Layer your reusable natural-language artstyle prompt (Incase sensual painterly + dark gothic fantasy, corrupted textures, sparks/lightning/ethereal particles, volumetric/rim lighting, glows, soft brush strokes, idealized voluptuous anatomy, ornate biomechanical details, moody palettes) on top. Add dynamic placeholders for variations (outfit changes per phase or scene).

2. **Behavioral/Response Layer (COT + Realism Prompts)**: Embed or reference the 10-section COT and specialized realism prompts (physical constraints, authentic reactions, non-verbal, anti-melodrama) in your system prompt, hidden reasoning/Decision Engine, or character-specific modules. This ensures outputs are vivid in sensory/physical detail while staying grounded and consistent with meters, phases, estrus, pregnancy, jealousy, loyalty, etc.

3. **Dynamic & Modular**: Leverage placeholders/global vars for wardrobe/hairstyle swaps or phase-specific visual/behavioral tweaks without breaking core identity. Tie to your scene mode detection and inter-entity protocols.

4. **Testing & Iteration**: Use long sessions focusing on visual consistency (same character across outfit/phase changes), behavioral realism (reactions feel authentic, not generic or over-the-top), and progression (plot/relationship advancement without stagnation).

**Example Vivid3 Hybrid Prompt Snippet** (for image gen or descriptive output):
`[DNA Visual Base with weights and Danbooru tags for exact appearance] + [Your Incase + gothic fantasy artstyle base with magical effects and lighting] + COT-guided behavioral descriptors: authentic micro-expressions, physical sensations tied to current meters (e.g., lactation, estrus sensitivity), non-verbal cues reflecting phase and relationships, grounded in realistic capabilities and manor/grove setting.`

## Additional Best Practices from Related Prompt Engineering
- **Weighting & Emphasis**: Use (keyword:1.2-1.4) for critical vivid elements (eyes, specific anatomy, emotional state, magical aura). Avoid over-weighting to prevent artifacts.
- **Negative Prompts**: Explicitly counter common failures (blurry, deformed, generic face, melodrama, omniscience, plot armor).
- **Structured Reasoning (COT)**: Always include explicit thinking steps for realism, consistency, and progression before final output — this is the heart of making prompts "vivid3" level.
- **Sensory & Physical Vividness**: Detail touch, scent, temperature, fatigue, arousal (tied to your estrus/lactation systems), micro-movements. Constrain to realistic physics/biology.
- **Consistency Anchors**: Repeated name emphasis, core feature DNA, and cross-references to previous events/memory in prompts.
- **Modularity**: Keep visual DNA/artstyle separate from behavioral COT/realism layers so you can mix-and-match or update independently (aligns with your expandable JSON sections).

## Sources & Further Reading
- SillyTavern DNA System: https://github.com/kainatquaderee/sillytavern-dna-system (visual DNA + placeholders for consistency and dynamics).
- Poppet RP Framework: https://github.com/Huzderu/poppet-rp-framework (COT + ultra-realism prompts for authentic, vivid behavior and anti-slop).
- Ties to prior curation in this repo: SillyTavern/RisuAI character systems, fount modularity, memory architectures, Danbooru tagging workflows, custom artstyle prompt development.

These resources provide concrete, battle-tested patterns to elevate your Vivid3 prompting to the next level of vividness, physical/emotional realism, visual fidelity, and long-term consistency — while integrating cleanly with your existing JSON architectures, decision engines, phases, and multi-entity dynamics.

**All techniques support enthusiastic, consensual, character-driven experiences with strong immersion and boundary respect.**

*Curated and adapted specifically for your advanced character creation workflow.*