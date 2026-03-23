# Image Skills Test

A creative experiment comparing AI image generation across Google Gemini, DALL-E (ChatGPT), and Adobe Firefly — with a focus on what each platform does best and what only Firefly can do.

## Overview

This project started as a test of AI image generation skills in Claude Code and turned into something more personal: designing a mascot (a cute orange coding robot), finding it a home (an enchanted twilight forest), and giving it a friend (a tiny blue robot companion) — all through browser-automated interactions with three different AI image generators.

Along the way, we discovered that Firefly's real power isn't generation — it's *editing*: Generative Fill, Generative Expand, and seamless style-matched inpainting that neither Gemini nor DALL-E can do.

## The Images

| # | File | Generator | What It Is |
|---|------|-----------|------------|
| 1 | `01-sheffield-sunset-trail-gemini.png` | Gemini | Watercolor sketch of a sunset trail run at Endcliffe Park, Sheffield |
| 2 | `02-iowa-city-hickory-hill-dalle.png` | DALL-E | Ink sketch of a sunset trail run at Hickory Hill Park, Iowa City |
| 3 | `03-orange-robot-desk-gemini.png` | Gemini | Photorealistic orange robot coding at a cozy desk |
| 4 | `04-orange-robot-watercolor-dalle-WINNER.png` | DALL-E | Watercolor orange robot with laptop (cover image winner) |
| 5 | `05-enchanted-forest-robot-firefly.png` | Firefly | Orange robot coding in an enchanted twilight forest |
| 6 | `06-expanded-forest-firefly-expand.png` | Firefly | Generative Expand — extended the forest scene to the left |
| 7 | `07-two-robots-forest-firefly-genfill-FINAL.png` | Firefly | Generative Fill — painted a blue robot companion into the scene |

## Key Findings

- **DALL-E** excels at cute, friendly character illustration in watercolor/ink styles
- **Gemini** excels at photorealistic, cinematic imagery with high detail
- **Firefly** can't generate from scratch as well as the others, but its editing tools are unmatched:
  - **Generative Expand** seamlessly imagines what's beyond the image borders
  - **Generative Fill** lets you paint a region and replace it with prompted content, matching the existing style perfectly

## Research

`research_findings_adobe_mcp.md` contains a detailed investigation into the Adobe Firefly / MCP ecosystem, including:
- Official Adobe MCP servers (AEM, Express, Experience Platform)
- Community MCP servers for Creative Suite apps
- Firefly REST API capabilities and pricing
- The Adobe-NVIDIA partnership (GTC 2026) signaling agentic creative workflows ahead

## How It Was Made

Every image was generated through Claude Code's browser automation skills (`/gemini`, `/dall-e`, `/firefly`, `/cover-image`), controlling Chrome tabs to interact with each platform's web UI. The Firefly editing required JavaScript injection into deep Shadow DOM to access prompt fields and buttons — documented in the research file.
