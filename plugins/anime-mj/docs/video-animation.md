# Video/Animation Reference Guide

Comprehensive guide to animating anime images using Midjourney's V1 video model.

> **Important**: Video generation is available on the **Midjourney web app only** (midjourney.com). Discord bot does not support video generation.

## Overview

Midjourney's V1 video model transforms still images into animated clips. The workflow is **image-to-video**: generate your anime image first, then animate it.

### Video Specifications

| Spec | Value |
|------|-------|
| Duration | 5 seconds (extendable to 21 seconds) |
| Resolution | 480p (Standard) / 720p (Pro/Mega plans) |
| Frame Rate | 24 FPS |
| Audio | None |
| Format | MP4, GIF |

## Video Parameters

| Parameter | Description | Usage |
|-----------|-------------|-------|
| `--motion low` | Subtle, gentle movement | Default - cinemagraphs, peaceful scenes, slow motion |
| `--motion high` | Dynamic, energetic movement | Action scenes, big camera motions, combat |
| `--raw` | Reduce AI interpretation | Precise motion control, literal prompt adherence |
| `--loop` | Seamless looping | Start/end frames match automatically |
| `--end` | End frame control | Specify ending state of animation |
| `--bs #` | Batch size | Generate multiple videos at once |

> **Note**: Videos are generated via the web app interface, not through a `--video` parameter.

### Basic Syntax

```
[Image URL] [motion description] --motion low
[Image URL] [motion description] --motion high
```

### With Raw Mode (Precise Control)

```
[Image URL] [motion description] --motion low --raw
```

### With Loop

```
[Image URL] [motion description] --motion low --loop
```

## Motion Styles

### Action Style
High-energy movement with dynamic camera work.

```
[Image URL] dynamic movement, action lines, speed effects --motion high
```

**Best for**: Shonen action scenes, combat, chase sequences

### Slice-of-Life Style
Gentle, natural movement with subtle animation.

```
[Image URL] gentle breeze, hair flowing softly, subtle movement, peaceful --motion low --raw
```

**Best for**: Everyday scenes, character moments, atmospheric shots

### Dramatic Style
Cinematic movement with emotional impact.

```
[Image URL] slow camera push, emotional moment, cinematic --motion low
```

**Best for**: Emotional reveals, character close-ups, pivotal moments

### Combat Style
Fast, impactful action with dynamic effects.

```
[Image URL] fast motion, impact frames, explosive movement --motion high
```

**Best for**: Fight scenes, special attacks, transformation sequences

## Camera Motion Guide

### Pan (Horizontal/Vertical Movement)

| Direction | Keywords | Example |
|-----------|----------|---------|
| Pan Left | "camera pans left", "tracking left" | `[URL] camera pans left, following character --motion low` |
| Pan Right | "camera pans right", "tracking right" | `[URL] camera pans right, revealing scene --motion low` |
| Tilt Up | "camera tilts up", "vertical pan up" | `[URL] camera tilts up, dramatic reveal --motion low` |
| Tilt Down | "camera tilts down", "looking down" | `[URL] camera tilts down, showing ground --motion low` |

### Zoom (In/Out Movement)

| Type | Keywords | Example |
|------|----------|---------|
| Zoom In | "camera pushes in", "zoom to face", "dramatic push" | `[URL] slow zoom to face, emotional moment --motion low` |
| Zoom Out | "camera pulls back", "wide reveal", "zoom out" | `[URL] camera pulls back, revealing environment --motion low` |

### Orbit (Circular Movement)

| Type | Keywords | Example |
|------|----------|---------|
| Full Orbit | "camera orbits around", "360 rotation" | `[URL] camera orbits around character, showcase --motion low` |
| Partial Orbit | "camera arcs around", "semi-circle" | `[URL] camera arcs around, dynamic angle --motion high` |

### Static (Character Animation Only)

| Type | Keywords | Example |
|------|----------|---------|
| Breathing | "subtle breathing", "chest movement" | `[URL] subtle breathing motion, peaceful --motion low --raw` |
| Hair/Cloth | "hair swaying", "cloth flowing" | `[URL] hair gently swaying, soft breeze --motion low` |
| Cinemagraph | "minimal movement", "loop" | `[URL] eyes blinking, subtle movement --motion low --loop` |

## Genre-Specific Motion Presets

### Shonen

High energy, dynamic camera, action-focused.

```
[Image URL] dynamic tracking shot, action lines, high energy, impact frames --motion high
```

**Keywords**: action lines, impact frames, dynamic movement, speed effects

### Seinen

Atmospheric, slow pans, detailed and moody.

```
[Image URL] slow atmospheric pan, cinematic, detailed, moody lighting --motion low
```

**Keywords**: atmospheric, cinematic, slow pan, moody, subtle

### Shoujo

Soft, sparkly, romantic movement.

```
[Image URL] sparkle effects, soft focus, flowing hair, gentle movement, dreamy --motion low
```

**Keywords**: sparkle effects, soft focus, flowing, dreamy, gentle

### Slice of Life

Natural, peaceful, everyday movement.

```
[Image URL] gentle breeze, natural movement, peaceful atmosphere --motion low --raw
```

**Keywords**: gentle breeze, natural, peaceful, subtle

### Mecha

Mechanical precision, transformation sequences.

```
[Image URL] mechanical movement, precise motion, transformation, metallic --motion high
```

**Keywords**: mechanical, precise, transformation, metallic, hydraulic

### Horror

Unsettling, creeping movement, building tension.

```
[Image URL] creeping motion, shadows moving, subtle unease, slow zoom --motion low
```

**Keywords**: creeping, shadows, unease, slow, tension

## Loop Animation

Create seamless looping animations where the end frame matches the start.

### Basic Loop

```
[Image URL] gentle breathing, subtle movement --motion low --loop
```

### Cinemagraph-Style Loop

```
[Image URL] cinemagraph, single element moving, hair swaying, rest still --motion low --loop --raw
```

### Perfect Loop Tips

- Keep motion simple and cyclical
- Use `--raw` for more control
- Use `--loop` parameter (not text in prompt)
- Subtle movements loop better than dramatic ones
- Hair, cloth, and breathing work well
- Circular/orbital motions create natural loops

## Integration with Anime-MJ Features

### With Artist Styles

Generate image with artist style, then animate:

```
# Step 1: Generate image
A warrior in dark armor, Kentaro Miura style, Berserk, dark fantasy --niji 6 --ar 16:9

# Step 2: Animate (on web app)
[Generated Image URL] cape flowing dramatically, wind effect, atmospheric --motion low
```

### With SREF Codes

SREF codes apply to image generation, not video. Generate styled image first:

```
# Step 1: Generate with SREF
A magical forest spirit, ethereal glow --niji 6 --ar 16:9 --sref 3408846050

# Step 2: Animate
[Generated Image URL] magical particles floating, gentle movement, ethereal --motion low
```

### With Character Reference

Character reference is used during image generation, not video animation:

```
# Step 1: Generate image with character reference
A mage casting a spell --niji 6 --ar 16:9 --cref [reference URL] --cw 100

# Step 2: Animate the generated image
[Generated Image URL] magical energy swirling, dramatic lighting --motion low
```

## Motion Level Guide

| Parameter | Effect | Best For |
|-----------|--------|----------|
| `--motion low` | Subtle, gentle movement | Cinemagraphs, peaceful scenes, character portraits, slow pans |
| `--motion high` | Dynamic, energetic movement | Action scenes, combat, dramatic moments, fast camera |

### Specifying Motion Level

Use the `--motion` parameter:

```
# Low motion (default, subtle)
[URL] subtle breathing, minimal movement, peaceful --motion low --raw

# High motion (dynamic, energetic)
[URL] explosive action, dynamic movement, high energy --motion high
```

## Example Prompts

### Action Scene

```
[Image URL] dynamic camera tracking, speed lines effect, impact frame --motion high
```

### Peaceful Moment

```
[Image URL] gentle breeze through hair, soft fabric movement, peaceful atmosphere --motion low --raw
```

### Dramatic Reveal

```
[Image URL] slow cinematic zoom to face, emotional intensity, dramatic lighting --motion low
```

### Character Showcase

```
[Image URL] camera slowly orbits around character, full body rotation, showcase pose --motion low
```

### Seamless Loop

```
[Image URL] hair gently swaying, soft breathing motion --motion low --loop --raw
```

### Combat Impact

```
[Image URL] fast motion blur, impact frame, explosive energy, dynamic camera shake --motion high
```

## Tips for Better Animation

1. **Composition matters**: Images with clear subjects animate better
2. **Use --raw for control**: Reduces AI interpretation, follows prompt more closely
3. **Match motion to mood**: Action scenes need high motion, peaceful scenes need low
4. **Simple loops work best**: Complex motion is harder to loop seamlessly
5. **Front-facing works well**: Characters facing camera animate more naturally
6. **Consider aspect ratio**: Wider ratios (16:9, 21:9) suit cinematic motion
7. **Clean backgrounds help**: Busy backgrounds can create distracting movement

## Platform Note

Video generation is **only available on the Midjourney web app** at midjourney.com. You cannot generate videos through the Discord bot.

**Workflow**:
1. Generate anime image (Discord or web)
2. Copy image URL or use web app's "Animate" button
3. Create animation on web app
4. Download MP4 or GIF
