# Claude Code Midjourney Plugin

A Claude Code plugin that generates optimized Midjourney prompts for AI image generation. Features full support for V7, Niji 6 anime mode, and styles from prominent anime artists.

## Installation

### Option 1: From GitHub (Recommended)

```bash
# Add the marketplace
claude plugin marketplace add https://github.com/jawhnycooke/claude-code-midjourney

# Install the plugin
claude plugin install midjourney

# Restart Claude Code
```

### Option 2: Manual Installation

1. Clone this repository:
```bash
git clone https://github.com/jawhnycooke/claude-code-midjourney.git
```

2. Copy the plugin to your Claude Code plugins directory:
```bash
cp -r claude-code-midjourney/plugins/midjourney ~/.claude/plugins/
```

3. Restart Claude Code

## Usage

### Slash Command

```
/midjourney [optional description]
```

**Examples:**
```
/midjourney a mystical forest at twilight
/midjourney Studio Ghibli style witch flying over a city
/midjourney cyberpunk hacker in neon alley, Akira style
```

### Interactive Workflow

The plugin guides you through building the perfect prompt:

1. **Category Selection**
   - Portrait/Character
   - Landscape/Environment
   - Product/Object
   - Abstract/Artistic
   - Anime/Manga
   - Style Transfer

2. **Subject Description** - Describe what you want to create

3. **Style Options** - For anime: choose artist style (Ghibli, Akira, etc.)

4. **Aspect Ratio** - 1:1, 16:9, 9:16, 4:3, 2:1, 3:2

5. **Stylization Level** - Photorealistic to highly artistic

6. **Optional Enhancements** - Exclusions, reference codes, chaos

### Example Output

```
A young witch flying on a broomstick over a coastal European town at sunset, Studio Ghibli style, Hayao Miyazaki, whimsical, enchanting, lush scenery, magical realism --niji 6 --style scenic --ar 16:9 --s 500
```

## Features

### Image Categories
- **Portrait/Character** - People, faces, character designs
- **Landscape/Environment** - Scenes, nature, architecture
- **Product/Object** - Items, products, still life
- **Abstract/Artistic** - Patterns, concepts, experimental
- **Anime/Manga** - Japanese animation styles via Niji 6
- **Style Transfer** - Apply reference styles

### Anime Artist Styles

| Artist | Style Description |
|--------|-------------------|
| **Hayao Miyazaki** | Studio Ghibli, whimsical, enchanting, lush scenery |
| **Katsuhiro Otomo** | Akira, cyberpunk, dystopian, intricate machinery |
| **Akira Toriyama** | Dragon Ball, dynamic action, bold colors |
| **Eiichiro Oda** | One Piece, adventure, exaggerated proportions |
| **Hideaki Anno** | Evangelion, mecha, psychological drama |
| **Kentaro Miura** | Berserk, dark fantasy, detailed linework |
| **Makoto Shinkai** | Your Name, photorealistic backgrounds, emotional |
| **Masashi Kishimoto** | Naruto, ninja themes, dynamic poses |
| **Yoshitoshi Abe** | Serial Experiments Lain, atmospheric, surreal |

### Supported Parameters

#### Core Parameters
| Parameter | Description | Values |
|-----------|-------------|--------|
| `--ar` | Aspect ratio | e.g., 16:9, 1:1, 9:16 |
| `--s` / `--stylize` | Artistic interpretation | 0-1000 |
| `--v` | Model version | 5, 6, 6.1, 7 |
| `--no` | Exclude elements | comma-separated |
| `--chaos` | Randomness | 0-100 |
| `--seed` | Reproducibility | 0-4294967295 |
| `--tile` | Seamless patterns | flag |
| `--q` / `--quality` | Detail level | 0.25, 0.5, 1 |

#### Anime (Niji) Parameters
| Parameter | Description |
|-----------|-------------|
| `--niji 6` | Activate Niji anime model |
| `--style cute` | Whimsical characters |
| `--style expressive` | Mature, dramatic |
| `--style scenic` | Environmental focus |
| `--style original` | Classic anime look |

#### Reference Parameters
| Parameter | Description | Weight |
|-----------|-------------|--------|
| `--sref` | Style reference | `--sw 0-1000` |
| `--cref` | Character reference (V6) | `--cw 0-100` |
| `--oref` | Omni-reference (V7) | `--ow 0-1000` |
| `--p` | Personalization profile | code |

## Repository Structure

```
claude-code-midjourney/
├── plugins/
│   └── midjourney/
│       ├── .claude-plugin/
│       │   └── plugin.json      # Plugin manifest
│       ├── commands/
│       │   └── midjourney.md    # Main slash command
│       ├── skills/
│       │   └── SKILL.md         # Autonomous skill
│       └── README.md            # Plugin documentation
├── README.md                    # This file
└── LICENSE                      # MIT license
```

## Prompt Best Practices

1. **Be Specific** - Detailed prompts produce better results
2. **Front-load Keywords** - Most important elements go first
3. **Keep It Concise** - Under 60 words is optimal
4. **Use --no Wisely** - Better than negative phrasing
5. **Match Parameters to Goal**:
   - Photorealism: `--s 50-100`
   - Artistic: `--s 500-1000`
   - Anime: Always use `--niji 6`

## Example Prompts

### Landscape
```
Ancient moss-covered temple ruins in a misty forest, volumetric fog, cinematic lighting, fantasy concept art, lush vegetation --ar 16:9 --v 7 --s 500
```

### Portrait
```
A young woman with flowing auburn hair, soft golden hour lighting, shallow depth of field, portrait photography --ar 3:2 --v 7 --s 200
```

### Anime (Ghibli)
```
A young witch flying on a broomstick over a coastal town, Studio Ghibli style, Hayao Miyazaki, whimsical, enchanting --niji 6 --style scenic --ar 16:9 --s 500
```

### Anime (Cyberpunk)
```
A hacker in a neon-lit alley with holographic interfaces, Akira style, Katsuhiro Otomo, cyberpunk, rain reflections --niji 6 --style expressive --ar 21:9 --s 750
```

## Future Roadmap

- [ ] Video prompt support (--motion, camera verbs)
- [ ] Character consistency workflows (--oref)
- [ ] Batch prompt generation
- [ ] SREF code library

## License

MIT License - see [LICENSE](LICENSE)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Related Resources

- [Midjourney Documentation](https://docs.midjourney.com/)
- [Midjourney Parameter List](https://docs.midjourney.com/hc/en-us/articles/32859204029709-Parameter-List)
- [Niji Mode Guide](https://www.aiarty.com/midjourney-prompts/midjourney-niji-prompts.htm)
