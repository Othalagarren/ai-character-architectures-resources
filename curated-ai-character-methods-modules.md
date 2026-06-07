# Curated AI Character Methods, Modules & Architectures

**Repository Purpose**: A personal collection of proven methods, modular systems, specifications, and best practices from major open-source AI character/roleplay platforms. Use this to inspire, expand, and perfect your custom character JSON architectures, decision engines, memory/continuity systems, lore injection, phase/meter mechanics, and immersive multi-entity roleplay.

All patterns emphasize **consensual, enthusiastic, character-driven** interactions with strong consistency, slow-burn depth, and expandable modular design.

---

## 1. Core Source Projects

### SillyTavern (https://github.com/SillyTavern/SillyTavern)
**~29k stars** | LLM frontend for power users | De facto standard for character cards and roleplay.

**Key Methods & Modules**:
- **Character Cards (v2/v3)**: PNG with embedded JSON. Portable, rich definitions (name, personality/description, scenario, first_mes, mes_example with <START> tags and {{char}}/{{user}} placeholders, creator_notes, tags, extensions object for custom data).
- **World Info / Lorebooks / Character Books**: Modular, trigger-activated knowledge injection. Entries have keys, content, insertion position (System/User/Assistant), order/priority, depth, probability, sticky (N messages), recursive scan, prevent recursion, grouping/weighting.
- **Extensible Plugin System**: Memory tools, scripting, group chat features.
- **Group Chats**: Multi-character sessions.
- **Advanced Prompt Templating**: Variables, conditions, impersonation.

**Specs**:
- v2: https://github.com/malfoyslastname/character-card-spec-v2
- v3: https://github.com/kwaroran/character-card-spec-v3

**Value for Custom Systems**: Standardized portable format + extensions for your phases/meters/custom logic. Lorebook model for efficient modular knowledge without prompt bloat.

### RisuAI (https://github.com/kwaroran/Risuai)
**~1.5k stars** | User-friendly roleplay software with advanced memory.

**Key Methods & Modules**:
- **Lorebook**: Dynamic memory/world info.
- **Long-term Memory**:
  - SupaMemory: Auto-summarization on context full; re-summarizes summaries → near-infinite memory, better past reference & consistency. Simple, no extra infra.
  - HypaMemory V2/V3: Vector/embedding storage + semantic retrieval for relevant history chunks.
- **Regex Scripts**: Post-output modification for style enforcement, custom behaviors, side effects.
- **Plugins**: Agent layers, custom features.
- **Assets**: Embed images/audio/video; emotion/expression images.
- **Group Chats + Broad API + Custom Prompting** (conditions, variables).

**Value**: Battle-tested memory architectures (summarization + vector) to solve long-session drift. Regex for deterministic rules. Plugin model for modularity.

### fount (https://github.com/steve02081504/fount)
**~700 stars** | Programmable modular agent runtime for characters & immersive interactions.

**Key Methods & Modules**:
- **Parts Ecosystem** (highly modular):
  - Characters (agents)
  - **Worlds**: Knowledge/behavior modules — append info, influence decisions, manipulate chat history.
  - Personas, interactive shells.
- **Code-Driven Logic**: Prompts + executable code (JS etc.) for precise state, rules, maintainable complexity.
- **AI-Assisted Generation**: One-sentence description → full persona + logic.
- **Compatibility**: Load SillyTavern/Risu cards via modules.
- **Group Chats**, git-driven parts, community templates, real-time execution, CI for characters.

**Value**: True hybrid prompt+code + modular "Worlds" concept — ideal blueprint for your expandable lore/phase/decision modules and inter-entity protocols. Code layer strengthens Decision Engine and hard rules (time progression, consent, syntax prevention).

### st-memory-enhancement (https://github.com/muyoou/st-memory-enhancement)
**~1.3k stars** | SillyTavern long-term memory plugin.

**Key Methods**: Structured memory tables, prompt injection, user-editable memory, templates for extended consistency.

**Value**: Practical patterns for memory visibility/editing in HUD or continuity systems.

### Supporting Resources
- RisuAI-Agent-plugin (vector DB + agent orchestration)
- Character card generators/editors
- Ecosystem TTS, launchers, themes

---

## 2. Highly Adaptable Patterns

### A. Character Definition (Card-like JSON)
Adopt nested, extensible structure for tooling compatibility and complexity:

```json
{
  "name": "...",
  "description": "Personality + background...",
  "personality": "...",
  "scenario": "...",
  "first_mes": "...",
  "mes_example": "<START>\n{{user}}: ...\n{{char}}: *action* \"dialogue\"...",
  "character_version": "3",
  "creator_notes": "...",
  "tags": ["..."],
  "character_book": { /* lore entries */ },
  "extensions": {
    "phases": [...],
    "meters": {...},
    "memory_log": [...],
    "pregnancy": {...},
    "estrus": {...},
    "jealousy_matrix": {...},
    "inter_entity_protocol": {...},
    "decision_engine_overrides": {},
    "scene_modes": {...}
  }
}
```

**Tips**: Use placeholders. Nest for hierarchies. Extensions = perfect home for your custom systems. YAML for human editing + converters.

### B. Modular Lore / Knowledge Injection
Model after Lorebooks/Worlds:
- Entries: triggers/keys, content, priority/order, depth, probability, sticky, recursion controls, groups.
- Activation: keyword scan in recent (or recursive) context → intelligent injection (e.g. character lore prioritized).
- Your Adaptation: `lore_modules` array in JSON. Scanning/injection logic in prompt builder or Decision Engine. Add phase-specific or meter-gated modules.

### C. Long-Term Memory & Continuity
- **Summarization (SupaMemory)**: Threshold-based or periodic AI summary of recent + prior summaries. Tag with phase, entities, emotion. Store in memory_log.
- **Vector Retrieval (HypaMemory)**: Embed key events; retrieve semantically relevant for "you did this before" or relationship callbacks.
- **Hybrid + Structured Tracking**: Entities, states (pregnancy, affection levels), relationships.
- **Editing**: User-viewable/editable memory for control.
- **Integration**: Phase/mode/meter aware retrieval and injection. Enforce via your Decision Engine priorities and user restrictions.

### D. Decision Engines & Agentic Behavior
- **Hybrid**: LLM for natural response + code/rules for hard constraints (phase transitions, meter updates, time progression, consent, no meta/syntax commands).
- **Modular Influencers**: "Worlds"-style modules that bias output, update state, or rewrite context based on current conditions.
- **Priority Stacking**: Personality + scene mode + active lore + retrieved memory + meters + inter-entity state.
- **Post-Processing**: Regex/script-like hooks for formatting, style, side-effects (log, update state).
- **Scene/Mode Detection**: Auto or enforced modes affecting pacing, allowed actions, output style.

### E. Extensibility, Safety & Multi-Entity
- Hook/plugin system for optional modules (e.g. estrus behaviors).
- Logic layer (reasoning/memory/decision) vs display layer.
- Highest priority: user restrictions, consistency guards, phase integrity.
- Group dynamics: awareness, turn protocols, selective memory sharing.
- Inter-entity: observation and interaction rules between characters.

---

## 3. Recommendations for Your Character JSON Evolution
- Add/expand sections: `lorebook` or `lore_modules`, `memory_summaries`, `active_modules`, `decision_weights`, `scene_mode`.
- Implement Memory Pipeline in your continuity system: log events → summarize periodically → relevance filter (phase/mode aware) → inject.
- Strengthen Decision Engine with lore triggers, memory hits, module states, and deterministic rules.
- Maintain strict separation of concerns and hard enforcement of boundaries/time/phase.
- Version character defs and memory snapshots.
- Continue Danbooru visual fidelity; consider asset extensions for state-dependent appearances.

These will help you maintain perfect consistency, deep lore fidelity, slow-burn loyalty, complex poly dynamics, and all your custom mechanics while scaling to richer scenarios.

---

## 4. How to Use This Collection
- Reference while designing or refactoring character JSONs.
- Copy/adapt structures, entry formats, memory patterns, and module ideas directly.
- Add your own refined implementations, example full JSONs, or new findings to this repo.
- Star the original projects for updates and deeper code.
- This is a living reference — expand it as your systems evolve.

**Everything here supports enthusiastic, wanted, character-driven experiences with clear boundaries.**

*Curated June 2026 from active GitHub projects.*