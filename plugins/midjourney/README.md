# Midjourney Prompt Builder Plugin

A Claude Code plugin that generates optimized Midjourney prompts for AI image generation. Supports both standard image prompts (V7) and anime/manga prompts (Niji 6) with styles from prominent anime artists.

## Features

- **Interactive prompt building** with guided questions
- **Multiple image categories**: Portrait, Landscape, Product, Abstract, Anime, Style Transfer
- **Full anime support** via Niji 6 mode
- **Prominent anime artist styles**: Miyazaki, Otomo, Toriyama, Oda, Anno, Miura, Shinkai, and more
- **All V7 parameters**: aspect ratio, stylize, quality, chaos, seed, tile, etc.
- **Reference system support**: style reference (--sref), character reference (--cref), omni-reference (--oref)
- **Personalization support**: --p parameter for custom profiles

## Usage

### Slash Command

```
/midjourney [optional description]
```

**Examples:**
```
/midjourney a mystical forest at twilight
/midjourney Studio Ghibli style witch flying over a city
/midjourney cyberpunk hacker in neon alley
```

### Interactive Flow

1. **Select category** (Portrait/Landscape/Product/Abstract/Anime/Style Transfer)
2. **Describe your subject** (what you want to create)
3. **Choose style options** (for anime: artist style + Niji mode)
4. **Select aspect ratio** (1:1, 16:9, 9:16, etc.)
5. **Set stylization level** (photorealistic to highly artistic)
6. **Optional**: Add exclusions, reference codes, chaos

### Output

The plugin outputs a ready-to-use Midjourney prompt:

```
A young witch flying on a broomstick over a coastal European town at sunset, Studio Ghibli style, Hayao Miyazaki, whimsical, enchanting, lush scenery --niji 6 --style scenic --ar 16:9 --s 500
```

## Supported Anime Artists

| Artist | Style |
|--------|-------|
| **Hayao Miyazaki** | Studio Ghibli, whimsical, enchanting, lush |
| **Katsuhiro Otomo** | Akira, cyberpunk, dystopian, intricate |
| **Akira Toriyama** | Dragon Ball, dynamic action, bold colors |
| **Eiichiro Oda** | One Piece, adventure, exaggerated proportions |
| **Hideaki Anno** | Evangelion, mecha, psychological |
| **Kentaro Miura** | Berserk, dark fantasy, detailed linework |
| **Makoto Shinkai** | Your Name, photorealistic backgrounds |
| **Masashi Kishimoto** | Naruto, ninja, dynamic poses |
| **Yoshitoshi Abe** | Serial Experiments Lain, atmospheric |

## Parameters Reference

### Core Parameters
| Parameter | Description | Values |
|-----------|-------------|--------|
| `--ar` | Aspect ratio | 1:1, 16:9, 9:16, 4:3, etc. |
| `--s` | Stylize | 0-1000 (default 100) |
| `--v` | Version | 5, 6, 6.1, 7 |
| `--no` | Exclude | comma-separated list |
| `--chaos` | Randomness | 0-100 |

### Anime (Niji) Parameters
| Parameter | Description |
|-----------|-------------|
| `--niji 6` | Enable anime mode |
| `--style cute` | Whimsical characters |
| `--style expressive` | Mature, dramatic |
| `--style scenic` | Environmental focus |
| `--style original` | Classic anime |

### Reference Parameters
| Parameter | Description |
|-----------|-------------|
| `--sref [code]` | Style reference |
| `--sw` | Style weight (0-1000) |
| `--cref [URL]` | Character reference |
| `--oref [URL]` | Omni-reference (V7) |
| `--p [code]` | Personalization |

## License

MIT
