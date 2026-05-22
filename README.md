English | [简体中文](README_CN.md)

# Sticker Kit Assets

This project provides tools to generate **supporting assets** and **collection copy** required for the WeChat Sticker Open Platform, strictly following official guidelines. **It does not include the generation of the sticker images themselves.**

## Core Features

1. **Copywriting Generation**: Generates collection names, introductions, reward prompt texts, and meaning words for each sticker based on the character's traits.
2. **Asset Processing**: Built-in Python script `process_sticker.py` automates the processing of image assets to meet size, format, transparency, and file size limitations.
3. **Guideline Checking**: Provides a detailed design self-check list to ensure assets meet platform review standards.

## Asset Guidelines Overview

| Asset Type | Format | Size (px) | Core Design Requirements |
| :--- | :--- | :--- | :--- |
| **Banner** | PNG | 750 × 400 | **No text**; **Must use colored opaque background**; **Subject or background elements must fill the canvas horizontally, with no blank margins or solid color borders on the sides** |
| **Cover** | PNG | 240 × 240 | **Transparent background**; Front half/full body; No white outlines/jaggies |
| **Icon** | PNG | 50 × 50 | **Transparent background**; Front headshot; No white outlines/jaggies; No square borders |
| **Reward Prompt** | GIF/PNG | 750 × 560 | Consistent style; Prompts user to reward; **Must use colored opaque background**; Text clearly visible |
| **Reward Thanks** | GIF/PNG | 750 × 750 | Consistent style; Inspires sharing; **Must use colored opaque background**; Text clearly visible |

## Script Usage

Use the built-in script `scripts/process_sticker.py` for automated processing:

```bash
# Generate cover image (240x240, PNG, transparent background - default)
python3 scripts/process_sticker.py input.png cover.png 240 240 PNG 500

# Generate banner image (750x400, PNG, colored opaque background - transparency must be disabled)
python3 scripts/process_sticker.py banner_input.png banner.png 750 400 PNG 500 False
```

**Parameters:**
`python3 process_sticker.py <input> <output> <width> <height> <format> <max_kb> [transparent=True] [is_animated=False] [loop_gif=False]`

## Detailed Guide

Please refer to `SKILL.md` for complete copywriting rules, design self-check lists, and image generation prompt guidelines.
