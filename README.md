# cinematic-ai-skills

> Production-ready Claude Code skills for AI video generation.  
> Stop generating generic AI-looking videos — apply directorial prompt structures backed by community benchmarks, platform guidelines, and academic research.

![Claude Code](https://img.shields.io/badge/Claude%20Code-skills-blueviolet)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Domain](https://img.shields.io/badge/domain-AI%20video%20generation-orange)
![Models](https://img.shields.io/badge/models-Kling%20%7C%20Sora%20%7C%20Wan2.1%20%7C%20Seedance-blue)

---

## Why This Exists

AI video models default to the same traps:
- ❌ Frontal stare + frozen smile
- ❌ Flat even lighting, gradient backgrounds
- ❌ Vague adjectives the model can't interpret ("beautiful", "epic")
- ❌ Simultaneous actions causing distortions

**These skills fix that** by treating video generation like briefing a DP and actor on set — you specify shot type, camera movement, lighting direction, action beats, and emotional arc.

**Evidence:** Community benchmark shows structured prompts reduce retry rate from 6.4 to 1.8 (75% reduction). Sora 2 official guidelines and EvalVerse academic benchmark (34 filmmakers, SRCC +0.74–+0.95) validate the same principles.

---

## Skills

| Skill | Description | Status |
|-------|-------------|--------|
| **[video-taste](./video-taste/)** | Anti-slop cinematic prompt engineering<br>• Video Read intent inference<br>• Three dials: DRAMA / MOTION / FIDELITY<br>• Beat Sheet (7-step micro-screenplay)<br>• Six-layer directorial structure<br>• Emotion-visual mapping | ✅ **v1.1.0** |
| **cinematography-director** | Professional cinematography knowledge base<br>• Shot language vocabulary<br>• Performance direction (Stanislavski)<br>• Composition law library<br>• Lighting setup templates | 🚧 **Coming soon** |

---

## Quick Start

### Install

```bash
/plugin marketplace add irenezhu1999-lab/cinematic-ai-skills
/plugin install video-taste@cinematic-ai-skills
```

### Example

**Before (generic prompt):**
```
A magical video of a girl receiving a Hogwarts letter. Make it emotional and epic.
```
→ Model outputs: frontal stare, flat lighting, vague "surprised" expression

**After (video-taste structured prompt):**
```
Video Read: Harry Potter letter arrival, Douyin audience,
emotional tone: surprise + sacred, shot language: slow push-in + volumetric particles,
facial fidelity: high.

Dials: DRAMA 8 / MOTION 5 / FIDELITY 9

Close-up, eye-level, slow push-in from medium to close-up.
85mm portrait lens, shallow DOF. Warm amber rim backlight intensifying.
Subject holds envelope; notices Hogwarts crest and pauses;
eyes widen and mouth opens; breaks into surprised smile
as golden particles drift left to right.
```
→ Model outputs: directional lighting, sequential action beats, natural expression arc

---

## Core Methodology

**The insight:** AI video models are time-series generators. They need *what happens at t1, t2, t3* — not *what the vibe should be*.

### video-taste approach

1. **Video Read** — declare understanding (theme, platform, tone, shot language, fidelity priority)
2. **Three Dials** — set values that drive all decisions (DRAMA / MOTION / FIDELITY)
3. **Beat Sheet** — sequential micro-screenplay (Initial → Trigger → Emotion → Reaction → Camera → End → Style)
4. **Six-Layer Structure** — shot size → angle → movement → lens → lighting → action
5. **Stanislavski Performance** — concrete physical actions, not abstract emotions

Full methodology: [video-taste/README.md](./video-taste/README.md)

---

## Evidence Base

| Source | Finding | Link |
|--------|---------|------|
| **Community benchmark** | Structured prompts: 1.8 retries avg vs 6.4 for vague prompts (75% reduction) | [Cyber Corsairs](https://cybercorsairs.com/beat-sheets-fix-flat-ai-videos/) |
| **Sora 2 guidelines** | "One camera idea per shot", physical details reduce uncanny motion | [Skywork AI](https://skywork.ai/blog/sora-2-prompt-authoring-best-practices-2025/) |
| **EvalVerse (academic)** | 45 sub-dimensions, emotional progression is #1 differentiator, expert correlation SRCC +0.74–+0.95 | [arXiv:2605.23271](https://arxiv.org/abs/2605.23271) |

---

## Roadmap

- [x] video-taste v1.1.0 — Beat Sheet + six-layer directorial structure
- [ ] cinematography-director v1.0.0 — shot language dictionary, composition laws, lighting templates
- [ ] Integration examples — Runway, Pika, Claude API workflows
- [ ] Multi-shot sequencing extension (when T2V models support)
- [ ] Audio sync layer (when audio-capable models mature)

---

## Contributing

Open to:
- Video Read examples for the example library
- Emotion-visual mapping table expansions
- Bug reports and prompt structure improvements

---

## Citation

If you use these skills in research or production:

```bibtex
@software{video_taste_2026,
  title  = {video-taste: Anti-slop AI video generation skill},
  author = {Irene Zhu and Claude Sonnet 4.6},
  year   = {2026},
  url    = {https://github.com/irenezhu1999-lab/cinematic-ai-skills}
}
```

---

## Credits

- **video-taste** adapted from [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
- Beat Sheet methodology from [Cyber Corsairs](https://cybercorsairs.com/beat-sheets-fix-flat-ai-videos/)
- Evaluation framework aligned with [EvalVerse](https://arxiv.org/abs/2605.23271)

---

**MIT License** — Built for directors, DPs, and AI video creators who refuse generic output.
