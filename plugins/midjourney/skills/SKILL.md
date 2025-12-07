---
name: midjourney-prompt-builder
description: Generates optimized Midjourney prompts for AI image generation, including anime/Niji styles
---

# Midjourney Prompt Builder Skill

This skill helps users create effective Midjourney prompts for AI image generation. It supports both standard image prompts (V7) and anime/manga prompts (Niji 6).

## When to Activate This Skill

Use this skill when users:

1. **Ask about Midjourney prompts** - "How do I write a Midjourney prompt?", "Help me create an image prompt"
2. **Want to generate AI art** - "Create an image of...", "Generate a picture of..."
3. **Request specific image styles** - "Make me a cyberpunk scene", "Create anime art"
4. **Need anime/manga images** - "Studio Ghibli style", "Anime character", "Niji prompt"
5. **Ask about Midjourney parameters** - "What does --stylize do?", "How do I use --sref?"
6. **Want consistent style/characters** - "How do I keep the same style?", "Character consistency"

## When NOT to Activate

Do not use this skill when:

- Users are working on code unrelated to image generation
- Users need help with other AI tools (DALL-E, Stable Diffusion, etc.)
- Users are asking general questions not related to image generation
- The conversation is about analyzing existing images (not creating new ones)

## Core Capabilities

### Supported Image Types
1. **Portrait/Character** - People, faces, character designs
2. **Landscape/Environment** - Scenes, nature, architecture
3. **Product/Object** - Items, products, still life
4. **Abstract/Artistic** - Patterns, concepts, experimental
5. **Anime/Manga** - Japanese animation styles via Niji mode
6. **Style Transfer** - Applying reference styles

### Anime Artist Styles
The skill knows how to craft prompts in the style of:
- **Hayao Miyazaki** - Studio Ghibli, whimsical, enchanting
- **Katsuhiro Otomo** - Akira, cyberpunk, dystopian
- **Akira Toriyama** - Dragon Ball, dynamic action
- **Eiichiro Oda** - One Piece, adventure
- **Hideaki Anno** - Evangelion, mecha
- **Kentaro Miura** - Berserk, dark fantasy
- **Makoto Shinkai** - Your Name, photorealistic backgrounds
- **Masashi Kishimoto** - Naruto, ninja themes
- **Yoshitoshi Abe** - Serial Experiments Lain, atmospheric

### Parameters Understood
- `--ar` (aspect ratio)
- `--s` / `--stylize` (0-1000)
- `--v` (model version: 5, 6, 6.1, 7)
- `--niji 6` (anime mode)
- `--style` (cute, expressive, scenic, original)
- `--no` (exclusions)
- `--sref` / `--sw` (style reference)
- `--cref` / `--cw` (character reference)
- `--oref` / `--ow` (omni-reference V7)
- `--p` (personalization)
- `--chaos` (randomness)
- `--seed` (reproducibility)
- `--q` / `--quality`
- `--tile` (seamless patterns)

## Interaction Pattern

### Step 1: Understand the Request
Listen to what the user wants to create. Extract:
- Subject matter
- Desired style/mood
- Any specific requirements

### Step 2: Ask Clarifying Questions
Use **AskUserQuestion** to gather:
- Image category (if unclear)
- Anime style (if anime requested)
- Aspect ratio preference
- Stylization level
- Any exclusions needed

### Step 3: Build the Prompt
Construct following best practices:
1. Subject first (most important)
2. Scene/environment details
3. Style descriptors
4. Parameters at the end

### Step 4: Output
Present the final prompt in a code block:

```
[Ready-to-use Midjourney prompt]
```

Explain parameter choices briefly.

## Example Outputs

### Standard Image
```
A majestic snow leopard on a rocky mountain peak at golden hour, wildlife photography, dramatic lighting, shallow depth of field, nature documentary style --ar 16:9 --v 7 --s 200
```

### Anime (Ghibli Style)
```
A young girl discovering a secret garden filled with glowing flowers, Studio Ghibli style, Hayao Miyazaki, whimsical, enchanting, lush vegetation, magical realism, soft lighting --niji 6 --style scenic --ar 16:9 --s 500
```

### Anime (Cyberpunk)
```
A hacker in a neon-lit alley accessing holographic interfaces, Akira style, Katsuhiro Otomo, cyberpunk, rain reflections, intricate machinery --niji 6 --style expressive --ar 21:9 --s 750
```

## Key Principles

1. **Specificity wins** - Detailed prompts produce better results
2. **Front-load importance** - First words have most weight
3. **Keep it concise** - Under 60 words optimal
4. **Match parameters to intent** - Low stylize for realism, high for art
5. **Always use --niji 6 for anime** - Don't mix with --v parameters
6. **Default to V7** - Latest model unless specified otherwise
