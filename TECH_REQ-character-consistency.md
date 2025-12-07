# Technical Requirements Document: Character Consistency Workflows

**Created**: 2025-12-07
**Version**: 1.0
**Complexity**: Simple
**PRD Reference**: PRD-character-consistency.md

---

## Executive Summary

Add character consistency workflow support to the anime-mj plugin, enabling users to create consistent characters across multiple images using `--cref` (Character Reference), `--oref` (Omni Reference), and `--cw` (Character Weight) parameters, plus reference sheet generation templates.

## Architecture

### Pattern
**Content Extension** - Adding workflow sections and templates to existing Claude Code plugin files. No new file structure needed.

### Component Structure
```
plugins/anime-mj/
├── commands/
│   └── anime-mj.md          # Add character consistency workflow
├── skills/
│   └── SKILL.md             # Add character reference capability
└── README.md                # Update feature list
```

### Data Flow
1. User invokes `/anime-mj` for character art
2. Plugin asks: "New character or existing reference?"
3. **New character path**:
   - Offer reference sheet templates (multi-view, expressions, outfits)
   - User generates sheet → uploads to Discord → gets URL
   - Plugin provides `--cref [URL]` template for subsequent prompts
4. **Existing reference path**:
   - User provides image URL
   - Plugin appends `--cref [URL]` to prompt
5. Plugin guides `--cw` weight selection based on use case

## Technology Stack

### File Format
**Markdown** - Native Claude Code plugin format, no external dependencies

### Content Organization
- **commands/anime-mj.md**: Character workflow step + reference sheet templates
- **skills/SKILL.md**: Character reference capability description

## Integration Points

### New Workflow Step (after SREF step)

```markdown
### Step 6: Character Reference (Optional)

Ask: "Do you want to maintain character consistency across images?"
Options:
- Create new character (generate reference sheet first)
- Use existing reference (provide image URL)
- Skip (single image, no consistency needed)

**If Create New Character:**
Offer reference sheet type:
- Multi-view sheet (front, side, 3/4, back)
- Expression sheet (happy, sad, angry, surprised, neutral)
- Outfit variation sheet (same character, different clothes)

**If Use Existing Reference:**
- Ask for image URL
- Ask about character weight (--cw)
```

### Reference Sheet Templates

**Multi-View Character Sheet:**
```
character reference sheet, [character description], multiple views, front view, side view, three-quarter view, back view, clean white background, full body, anime style --niji 6 --ar 16:9
```

**Expression Sheet:**
```
expression sheet, [character description], multiple expressions, happy, sad, angry, surprised, neutral, head shots, clean white background --niji 6 --ar 16:9
```

**Outfit Variation Sheet:**
```
outfit variation sheet, [character description], same character different outfits, casual, formal, combat, sleepwear, clean white background --niji 6 --ar 16:9
```

**Turntable/360 View:**
```
character turntable, [character description], 360 rotation, multiple angles, clean white background, full body --niji 6 --ar 21:9
```

### Using Character Reference

**Basic Usage:**
```
[scene description] --niji 6 --cref [URL] --ar [ratio]
```

**With Character Weight:**
```
[scene description] --niji 6 --cref [URL] --cw [0-100] --ar [ratio]
```

**Multiple References:**
```
[scene description] --niji 6 --cref [URL1] [URL2] --ar [ratio]
```

### Parameter Reference Table

| Parameter | Description | Values |
|-----------|-------------|--------|
| `--cref [URL]` | Character reference image | Discord image URL |
| `--cw [weight]` | Character weight | 0-100 (default: 100) |
| `--oref [URL]` | Omni reference (V7) | Discord image URL |

### Character Weight Guide

| Weight | Effect | Use Case |
|--------|--------|----------|
| `--cw 100` | Full character (face + hair + clothes) | Same outfit, different pose |
| `--cw 50` | Moderate similarity | Different outfit, same character |
| `--cw 0` | Face only | Complete costume change |

### V6/V7 Compatibility

| Version | Parameter | Notes |
|---------|-----------|-------|
| V6 / Niji 6 | `--cref` | Primary method |
| V7 | `--oref` | Preferred in V7, replaces --cref |
| V7 | `--cref` | Still works but may be deprecated |

## Files to Modify

| File | Changes |
|------|---------|
| `plugins/anime-mj/commands/anime-mj.md` | Add Step 6 character workflow, reference sheet templates, parameter guide |
| `plugins/anime-mj/skills/SKILL.md` | Add character reference capability |
| `plugins/anime-mj/README.md` | Update feature list |

## Implementation Plan

### Phase 1: Update command file
1. Add Step 6: Character Reference workflow (after SREF step)
2. Add reference sheet template section
3. Add character parameter reference table
4. Add --cw weight guide
5. Add V6/V7 compatibility notes
6. Add example prompts with --cref

### Phase 2: Update skill file
1. Add character reference trigger conditions
2. Add character workflow to interaction pattern
3. Add example outputs with --cref

### Phase 3: Update README
1. Add character consistency to feature list
2. Add quick reference for --cref/--cw/--oref

## Example Outputs

### Creating Reference Sheet
```
character reference sheet, young female sorcerer with long silver hair and purple eyes wearing a dark cloak, multiple views, front view, side view, three-quarter view, back view, clean white background, full body, anime style --niji 6 --ar 16:9
```

### Using Reference in Scene
```
A young sorcerer casting a spell in a magical forest, purple energy swirling, dramatic lighting --niji 6 --style expressive --ar 16:9 --cref https://cdn.discordapp.com/attachments/... --cw 100
```

### Outfit Change (Lower Weight)
```
A young sorcerer in casual modern clothes at a coffee shop, relaxed pose --niji 6 --style cute --ar 16:9 --cref https://cdn.discordapp.com/attachments/... --cw 50
```

## Out of Scope

- Real photo to anime character conversion (unreliable results)
- Automatic URL handling (user must upload to Discord manually)
- Custom character database/storage
- Automatic character extraction from complex images

## Success Criteria

- [x] Plugin offers character reference sheet generation workflow
- [x] Plugin explains `--cref` vs `--oref` usage
- [x] Plugin guides `--cw` weight selection based on use case
- [x] Reference sheet templates included (multi-view, expression, outfit)
- [x] Example prompts for character consistency workflow
- [x] V6/V7 compatibility documented

## Best Practices to Document

1. **Generate reference with Midjourney first** - Works better than external images
2. **Use clean white backgrounds** - Easier for Midjourney to extract character
3. **Front-facing, well-lit source images** - Better recognition
4. **Single character per reference** - Avoid confusion
5. **High-resolution source** - More detail to reference
6. **Consistent style in reference** - Match Niji mode to Niji generation

## Next Steps

1. Review & approve this TRD
2. Run `/epcc-code` to implement (no explore needed - simple content addition)
3. Finalize with `/epcc-commit`

---

**End of TRD**
