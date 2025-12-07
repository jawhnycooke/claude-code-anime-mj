---
name: anime-mj-prompt-builder
description: Generates anime/manga prompts for Midjourney Niji mode with 30+ artist styles, SREF code library
---

# Anime/Manga Prompt Builder Skill

This skill helps users create authentic anime and manga art using Midjourney's Niji mode. It features comprehensive knowledge of 30+ manga artists, 14 anime studios, multiple genres, and technical Niji parameters.

## When to Activate This Skill

Use this skill when users:

1. **Request anime or manga art** - "Create anime art of...", "Draw a manga character..."
2. **Mention anime artists** - "Ghibli style", "like Berserk", "Dragon Ball look"
3. **Ask about Niji mode** - "How do I use Niji?", "Anime settings in Midjourney"
4. **Want specific anime styles** - "magical girl", "shonen action", "cyberpunk anime"
5. **Reference anime studios** - "MAPPA style", "Kyoto Animation look", "Trigger aesthetic"
6. **Describe anime genres** - "seinen dark fantasy", "shoujo romance", "isekai adventure"
7. **Ask about SREF codes** - "What SREF code for Ghibli?", "Anime style reference codes"
8. **Want consistent styling** - "Make it look like...", "Same style as...", "Visual consistency"
9. **Need character consistency** - "Same character in different poses", "Keep my character consistent"
10. **Want reference sheets** - "Create a character sheet", "Multiple views of character"
11. **Ask about --cref** - "How do I use character reference?", "What is --cref?"

## When NOT to Activate

Do not use this skill when:

- Users want photorealistic or non-anime images
- Users are working on code unrelated to image generation
- Users are asking about other AI tools (DALL-E, Stable Diffusion)
- The request is for Western cartoon styles (not anime)

## Core Capabilities

### Supported Artists (30+)

**Foundational**: Osamu Tezuka, Leiji Matsumoto, Go Nagai

**Shonen**: Akira Toriyama, Eiichiro Oda, Masashi Kishimoto, Tatsuki Fujimoto, Hajime Isayama, Gege Akutami, Kohei Horikoshi

**Seinen**: Kentaro Miura, Katsuhiro Otomo, Naoki Urasawa, Junji Ito, Tsutomu Nihei, Takehiko Inoue

**Shoujo/Josei**: Naoko Takeuchi, CLAMP, Rumiko Takahashi, Ai Yazawa

**Directors**: Hayao Miyazaki, Makoto Shinkai, Hideaki Anno, Satoshi Kon, Mamoru Hosoda, Hiroyuki Imaishi

**Modern**: Hirohiko Araki, ONE, Yusuke Murata, Sui Ishida, Yoshitoshi Abe

### Supported Studios (14)

Studio Ghibli, Kyoto Animation, MAPPA, Ufotable, WIT Studio, Bones, Madhouse, Trigger, Shaft, Production I.G, Sunrise, Toei Animation, A-1 Pictures, CloverWorks

### Genres

- **Shonen** - Action, adventure, battles
- **Seinen** - Mature, dark, psychological
- **Shoujo** - Romance, magical girl
- **Slice of Life** - Everyday, school, heartwarming
- **Mecha** - Robots, sci-fi
- **Horror** - Dark, disturbing
- **Isekai** - Fantasy worlds
- **Cyberpunk** - Dystopian, neon

### Niji Parameters

- `--niji 6` (required for anime)
- `--style cute/expressive/scenic/original`
- `--ar` (aspect ratio)
- `--s` (stylize 0-1000)
- `--sref` (style reference)
- `--sw` (style weight 0-1000)
- `--cref` (character reference)
- `--cw` (character weight 0-100)
- `--oref` (omni reference, V7)

### Character Consistency Support

**Reference Sheet Types:**
- Multi-view sheets (front, side, 3/4, back)
- Expression sheets (happy, sad, angry, surprised, neutral)
- Outfit variation sheets (same character, different clothes)
- Turntable/360 views

**Character Weight Guide:**
- `--cw 100`: Full character (face + hair + clothes)
- `--cw 50`: Moderate similarity (different outfit, same character)
- `--cw 0`: Face only (complete costume change)

### SREF Code Library (40+ Curated Codes)

**Categories:**
- **Ghibli/Soft**: Warm, nostalgic (codes: 3408846050, 918084796, 3161604773...)
- **Shonen/Dynamic**: Bold, action-oriented (codes: 3730983883, 910384726...)
- **Seinen/Dark**: Moody, atmospheric (codes: 416523183, 229704573...)
- **Shoujo/Elegant**: Sparkles, soft lighting (codes: 2178024008...)
- **Retro**: 80s/90s aesthetic (codes: 16809792746, 4292182277...)
- **Modern/Clean**: Contemporary look (codes: 65, 20...)

**Full library**: See `docs/sref-library.md` for complete reference.

## Interaction Pattern

### Step 1: Identify Genre
Determine if the request is shonen, seinen, shoujo, slice of life, mecha, or horror.

### Step 2: Match Artist/Studio
Suggest relevant artists or studios based on the genre and description.

### Step 3: Gather Details
Ask about character, scene, action, and atmosphere.

### Step 4: Technical Options
Determine Niji style mode and aspect ratio.

### Step 5: Style Reference (Optional)
Offer SREF codes from the curated library based on genre.

### Step 6: Character Reference (Optional)
Ask if user needs character consistency:
- Create new character → offer reference sheet templates
- Use existing reference → get URL and suggest --cw weight
- Skip for single images

### Step 7: Build Prompt
Construct and output the ready-to-use Niji prompt.

## Example Outputs

### Ghibli Style
```
A young adventurer discovering a hidden forest spirit, Studio Ghibli style, Hayao Miyazaki, whimsical, enchanting, lush vegetation, magical realism --niji 6 --style scenic --ar 16:9 --s 500
```

### Dark Fantasy
```
A lone warrior facing a demon in a gothic cathedral, Berserk style, Kentaro Miura, dark fantasy, hyper-detailed linework, atmospheric --niji 6 --style expressive --ar 2:3 --s 800
```

### Magical Girl
```
A magical girl mid-transformation with sparkles and ribbons, Sailor Moon style, Naoko Takeuchi, magical girl, pastel colors, cosmic background --niji 6 --style cute --ar 9:16 --s 600
```

### Cyberpunk
```
A courier on a motorcycle through neon-lit streets, Akira style, Katsuhiro Otomo, cyberpunk, rain reflections, intricate machinery --niji 6 --style expressive --ar 21:9 --s 750
```

### With SREF Code (Ghibli)
```
A girl walking through a sunlit meadow, magical realism, soft lighting --niji 6 --style scenic --ar 16:9 --sref 3408846050 --sw 300
```

### With SREF Code (Dark)
```
A knight before an ancient demon gate, dark fantasy, gothic atmosphere --niji 6 --style expressive --ar 2:3 --sref 416523183 --sw 400
```

### Character Reference Sheet
```
character reference sheet, young female sorcerer with long silver hair and purple eyes wearing a dark cloak, multiple views, front view, side view, three-quarter view, back view, clean white background, full body, anime style --niji 6 --ar 16:9
```

### Using Character Reference
```
A young sorcerer casting a spell in a magical forest, purple energy swirling, dramatic lighting --niji 6 --style expressive --ar 16:9 --cref https://cdn.discordapp.com/attachments/... --cw 100
```

## Key Principles

1. **Always use --niji 6** for anime generation
2. **Front-load artist names** - they strongly influence output
3. **Match style mode to genre**:
   - Cute: Shoujo, kawaii, slice of life
   - Expressive: Shonen, seinen, action
   - Scenic: Ghibli, landscapes, backgrounds
   - Original: Retro, classic anime
4. **Keep prompts under 60 words** for best results
5. **Use genre keywords** to reinforce the aesthetic
