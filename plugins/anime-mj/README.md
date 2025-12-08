# Anime-MJ: Anime/Manga Prompt Builder

A Claude Code plugin that generates optimized anime and manga prompts for Midjourney's Niji mode. Features 30+ manga artists, 14 anime studios, 40+ curated SREF codes, and comprehensive genre support.

## Features

- **30+ manga/anime artists** with style keywords
- **14 anime studios** with distinct aesthetics
- **40+ curated SREF codes** for consistent visual styles
- **Character consistency workflows** with reference sheet templates
- **Video/animation support** with motion templates and camera guides
- **6 genre categories**: Shonen, Seinen, Shoujo, Slice of Life, Mecha, Horror
- **Full Niji 6 support** with all style modes
- **Interactive prompt building** with guided questions
- **Ready-to-paste output** for Discord/web

## Usage

### Slash Command

```
/anime-mj [description]
```

**Examples:**
```
/anime-mj a warrior in dark armor facing a demon
/anime-mj magical girl transformation sequence
/anime-mj cyberpunk hacker in neon-lit alley
/anime-mj slice of life school scene at sunset
```

### Interactive Flow

1. **Select genre** (Shonen/Seinen/Shoujo/Slice of Life/Mecha/Horror)
2. **Choose artist or studio style**
3. **Describe your subject**
4. **Select Niji style mode** (cute/expressive/scenic/original)
5. **Choose aspect ratio**
6. **Apply SREF code** (optional - for consistent visual style)
7. **Apply character reference** (optional - for character consistency)
8. **Animate image** (optional - for video/animation, web app only)
9. **Output** ready-to-use prompt

## Supported Artists

### Shonen
| Artist | Style |
|--------|-------|
| Akira Toriyama | Dragon Ball, dynamic action, bold colors |
| Eiichiro Oda | One Piece, exaggerated proportions, adventure |
| Masashi Kishimoto | Naruto, ninja themes, dynamic poses |
| Tatsuki Fujimoto | Chainsaw Man, chaotic, horror elements |
| Hajime Isayama | Attack on Titan, dark, dramatic |

### Seinen
| Artist | Style |
|--------|-------|
| Kentaro Miura | Berserk, dark fantasy, hyper-detailed |
| Katsuhiro Otomo | Akira, cyberpunk, dystopian |
| Naoki Urasawa | Monster, psychological thriller |
| Junji Ito | Horror, surreal, disturbing |
| Tsutomu Nihei | Blame!, biomechanical |

### Shoujo/Josei
| Artist | Style |
|--------|-------|
| Naoko Takeuchi | Sailor Moon, magical girl |
| CLAMP | Cardcaptor Sakura, elegant |
| Ai Yazawa | Nana, fashion-forward |

### Directors
| Creator | Style |
|---------|-------|
| Hayao Miyazaki | Studio Ghibli, whimsical |
| Makoto Shinkai | Your Name, photorealistic backgrounds |
| Hideaki Anno | Evangelion, mecha, psychological |
| Hiroyuki Imaishi | Trigger style, kinetic, explosive |

### Modern
| Artist | Style |
|--------|-------|
| Hirohiko Araki | JoJo, dramatic poses, baroque |
| Yusuke Murata | One Punch Man, hyper-detailed action |
| Sui Ishida | Tokyo Ghoul, watercolor-like |

## Supported Studios

| Studio | Aesthetic |
|--------|-----------|
| Studio Ghibli | Hand-painted, magical realism |
| Kyoto Animation | Moe, detailed eyes, fluid |
| MAPPA | Modern, dynamic action |
| Ufotable | CGI integration, vibrant |
| Trigger | Kinetic, exaggerated, colorful |
| Bones | Fluid animation, dynamic |
| Madhouse | Versatile, high quality |
| Shaft | Avant-garde, stylized |

## Niji Parameters

| Parameter | Description |
|-----------|-------------|
| `--niji 6` | Required for anime style |
| `--style raw` | Less stylized, more literal output (optional) |
| `--ar` | Aspect ratio |
| `--s` | Stylize (0-1000) |
| `--sref` | Style reference code |
| `--sw` | Style weight (0-1000) |
| `--cref` | Character reference |
| `--cw` | Character weight (0-100) |
| `--oref` | Omni reference (V7) |
| `--video` | Enable video generation (web app only) |

## SREF Code Library

Curated SREF codes for consistent anime visual styles. See [docs/sref-library.md](./docs/sref-library.md) for full library.

### Quick Reference

| Category | Code | Name |
|----------|------|------|
| Ghibli | `3408846050` | Ghibli Vibes |
| Ghibli | `918084796` | Anime Serenity |
| Dynamic | `3730983883` | Dynamic Comic |
| Dark | `416523183` | Anime Vampire |
| Dark | `229704573` | Dark Warrior |
| Shoujo | `2178024008` | Iridescence |
| Retro | `16809792746` | 80s Retro |
| Modern | `65` | Neo-Noir |

### SREF Usage

```
# Basic usage
--sref 3408846050

# With style weight
--sref 3408846050 --sw 300

# Blend two codes
--sref 3408846050 918084796

# Weighted blend
--sref 3408846050::2 918084796::1
```

## What You Say → What You Get

The plugin builds detailed prompts from simple inputs. Here's what that looks like:

### Simple Request
**You say**: "magical girl transformation, Sailor Moon style"
**You get**:
```
A magical girl mid-transformation with sparkles and ribbons spiraling around her, Sailor Moon style, Naoko Takeuchi, kawaii, adorable expression, big sparkling eyes, soft pastel colors, cosmic background --niji 6 --ar 9:16 --s 600
```

### Dark Fantasy
**You say**: "warrior facing a demon, Berserk style"
**You get**:
```
A lone warrior in black armor facing a massive demon in a gothic cathedral, Berserk style, Kentaro Miura, dark fantasy, dramatic, intense expression, hyper-detailed linework --niji 6 --ar 2:3 --s 800
```

### With Style Reference
**You say**: "peaceful meadow scene, Ghibli style, add a matching SREF"
**You get**:
```
A young girl walking through a sunlit meadow filled with wildflowers, Studio Ghibli style, magical realism, cinematic, soft golden hour lighting --niji 6 --ar 16:9 --sref 3408846050 --sw 300
```

### Character Reference Sheet
**You say**: "create a character sheet for my mage character"
**You get**:
```
character reference sheet, [your character description], multiple views, front view, side view, three-quarter view, back view, clean white background, full body --niji 6 --ar 16:9
```

## Character Consistency

Create consistent characters across multiple images using reference sheets and the `--cref` parameter.

### Reference Sheet Types

| Type | Description |
|------|-------------|
| Multi-view | Front, side, 3/4, back views |
| Expression | Happy, sad, angry, surprised, neutral |
| Outfit | Same character, different clothes |
| Turntable | 360-degree rotation views |

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
| V7 | `--oref` | Preferred in V7 |
| V7 | `--cref` | Still works but may be deprecated |

## Video/Animation

Animate your anime images using Midjourney's V1 video model. See [docs/video-animation.md](./docs/video-animation.md) for full guide.

> **Note**: Video generation requires the Midjourney **web app** (midjourney.com). Discord bot does not support video.

### Motion Styles

| Style | Description |
|-------|-------------|
| Action | Dynamic movement, speed effects, high energy |
| Slice-of-life | Gentle breeze, subtle movement, peaceful |
| Dramatic | Slow zoom, emotional moments, cinematic |
| Combat | Fast motion, impact frames, explosive |

### Camera Motion

| Motion | Description |
|--------|-------------|
| Pan | Horizontal/vertical tracking movement |
| Zoom | Push in or pull out |
| Orbit | Circular movement around subject |
| Static | Subtle character animation only |

### Animation Examples

```
# Action scene
[Image URL] dynamic camera tracking, speed lines, impact frame, high motion --video

# Peaceful moment
[Image URL] gentle breeze, hair flowing, subtle movement, low motion --video --raw

# Seamless loop
[Image URL] seamless loop, soft breathing, subtle --video loop --raw
```

## Documentation

- [SREF Code Library](./docs/sref-library.md) - Full curated library with 40+ anime style codes
- [Video/Animation Guide](./docs/video-animation.md) - Complete animation reference
- [Reference Index](./docs/README.md) - Documentation index

## External Resources

- [sref-midjourney.com](https://sref-midjourney.com/style/niji) - 5,500+ SREF codes
- [Midlibrary.io](https://midlibrary.io/) - 2,800+ curated codes
- [promptsref.com/niji-6](https://promptsref.com/version/niji-6) - Niji-specific collection

## License

MIT
