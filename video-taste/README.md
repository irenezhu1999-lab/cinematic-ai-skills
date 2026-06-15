# video-taste

> **Anti-slop AI video generation skill.** Turns vague mood words into directorial prompt structures — shot type, camera movement, lighting direction, action beats, and emotional arc.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Models](https://img.shields.io/badge/models-Kling%20%7C%20Sora%20%7C%20Wan2.1%20%7C%20Seedance-blue)
![Claude Code](https://img.shields.io/badge/Claude%20Code-skill-blueviolet)
![Domain](https://img.shields.io/badge/domain-AI%20video%20generation-orange)

Adapted from [taste-skill](https://github.com/Leonxlnx/taste-skill) for video pipelines.

---

## Table of Contents

- [Why](#why)
- [Evidence](#evidence)
- [Core System](#core-system)
  - [0. Video Read](#0-video-read)
  - [1. Three Dials](#1-three-dials)
  - [2. Beat Sheet](#2-beat-sheet)
  - [3. Six-Layer Directorial Structure](#3-six-layer-directorial-structure)
- [Advanced](#advanced)
  - [Emotion–Visual Mapping](#emotionvisual-mapping)
  - [Character Performance](#character-performance)
  - [Multi-Shot & Audio Sync](#multi-shot--audio-sync)
- [Integration](#integration)
- [Quick Start](#quick-start)
- [References](#references)

---

## Why

AI video generation defaults to the same traps every time:

| ❌ Default Trap | ✅ This Skill Does Instead |
|---|---|
| Frontal stare + frozen smile | 3/4 angle, natural expression arc |
| Flat even lighting | Directional key/rim/backlight by DRAMA dial |
| Gradient blur background | Scene with depth layers and environment |
| "beautiful", "emotional", "epic" adjectives | Concrete shot instructions a DP would understand |
| Simultaneous actions → distortion | Sequential beat structure with `;` separators |

**The core insight:** AI video models are time-series generators. They need to know *what happens at t1, t2, t3* — not *what the vibe should be*.

---

## Evidence

Three layers of validation for the structured-prompt approach:

**1. Community benchmark** — 50 prompts tested on Kling v3.0 + Seedance 2.0 ([source](https://cybercorsairs.com/beat-sheets-fix-flat-ai-videos/)):
> Vague prompts: **6.4 retries avg** → Beat Sheet prompts: **1.8 retries** (75% reduction)
> *(Reddit u/_clock_1277_, community test — directionally reliable, not peer-reviewed)*

**2. Platform guidelines** — Sora 2 official best practices (2025, [source](https://skywork.ai/blog/sora-2-prompt-authoring-best-practices-2025/)):
- "One camera idea per shot" — no simultaneous zoom + pan
- Physical details reduce uncanny motion (OpenAI system card 2025)

**3. Academic research** — [EvalVerse](https://arxiv.org/abs/2605.23271) (2026), calibrated with 34 professional filmmakers across 11 models:
- Professional video quality requires **45 sub-dimensions** beyond prompt fidelity
- **Emotional progression** is the #1 differentiator between amateur and cinematic output
- Expert correlation: SRCC +0.74–+0.95, p < 0.05
- Seedance 2.0 ranked best overall for professional-grade output

---

## Core System

### 0. Video Read

Before writing any prompt, output one **Video Read** line:

```
Reading this as: [theme], [platform/audience], emotional tone [X],
shot language [Y], facial fidelity priority [high/mid/low].
```

> *"Reading this as: Harry Potter magic letter arrival, Douyin/Xiaohongshu, emotional tone: surprise + sacred, shot language: slow push-in + volumetric particles, facial fidelity: high."*

If signals are unclear, ask **one question only**.  
If the source image provides enough context, don't ask — declare and proceed.

---

### 1. Three Dials

Set after Video Read. All prompt decisions derive from these values:

```
DRAMA:    7   # 1 = documentary calm   →  10 = Hollywood epic
MOTION:   6   # 1 = static micro-move  →  10 = rapid cuts + tracking
FIDELITY: 8   # 1 = stylization first  →  10 = exact facial match
```

**Defaults: 7 / 6 / 8** (commercial client baseline)

| Dial | Controls | Low (≤4) | Mid (5–7) | High (≥8) |
|------|----------|----------|-----------|-----------|
| **DRAMA** | Composition + Light | Natural light, balanced | Directional light, asymmetry | Rim/backlight, diagonal, VFX |
| **MOTION** | Camera + Action arc | Static or subtle push | Slow dolly, clear beats | Tracking, handheld, speed ramp |
| **FIDELITY** | Facial identity | Stylization OK | Maintain key features | Exact match, lock micro-expressions |

**Dial inference table:**

| Theme | DRAMA | MOTION | FIDELITY |
|---|---|---|---|
| Fantasy / magic | 8–9 | 5–7 | 7–8 |
| Realist portrait / commercial | 5–6 | 3–4 | 9–10 |
| Action / transformation | 9–10 | 8–10 | 5–6 |
| Japanese / soft / healing | 4–5 | 3–4 | 7–8 |
| Viral content test | 7–8 | 6–7 | 6–7 |

---

### 2. Beat Sheet

**The problem:** Static adjectives tell the model *what to feel*, not *what to show*.  
**The solution:** Beat Sheet = micro-screenplay with camera notes.

```
[Subject/Initial State] → [Trigger Event] → [Emotion Shift] →
[Physical Reaction] → [Camera Instruction] → [End Frame] → [Style Constraints]
```

**Rules:**
- **Actions > Adjectives** — not "looks sad", but "stares at phone; breathing slows; fingers curl"
- **One action per beat** — use `;` separator, never `while` / `simultaneously`
- **Name the end frame** — prevents video from drifting in the final seconds
- **Add a turning point** — a sound, light change, or movement that breaks the initial state

```
❌  Character turns around while throwing letter into the air with both arms raised
    as golden light bursts from behind.

✅  Character slowly turns toward camera; pauses; raises both arms;
    letter drifts upward from open palms; golden backlight intensifies.
```

**Why this works:** Sequential instructions match how T2V models generate frames — one dominant change per temporal window. Simultaneous complex actions overload the generation and cause distortion.

---

### 3. Six-Layer Directorial Structure

Write video prompts like briefing a DP on set:

```
[Shot Size] → [Angle] → [Camera Movement] → [Lens/DOF] → [Lighting] → [Action Narrative]
```

| Layer | Use | Avoid |
|-------|-----|-------|
| **Shot Size** | extreme close-up / close-up / medium / wide / extreme wide | vague scale words |
| **Angle** | eye-level / low angle / high angle / dutch tilt / bird's eye | "from below", "正面" |
| **Movement** | push-in / pull-back / pan / tracking / crane up / static | "moving camera" |
| **Lens/DOF** | 85mm portrait / 24mm wide / shallow DOF / deep focus | "blur the background" |
| **Lighting** | key light from left / rim backlight / top light / golden hour side | "good lighting" |
| **Action** | Sequential beats with `;` | static descriptions only |

**Full example:**
```
<<<image_1>>> as opening. Close-up, eye-level, slow push-in toward subject's face.
85mm portrait lens, shallow DOF. Warm amber rim backlight from behind.
Subject stands holding letter; slowly raises gaze toward camera;
breaks into a surprised smile as golden particles drift across frame.
```

---

## Advanced

### Emotion–Visual Mapping

Map user emotion keywords to concrete visual decisions:

| User Says | Lighting | Color | Composition | Camera |
|-----------|----------|-------|-------------|--------|
| Sacred / epic | Top light + backlight particles | Warm gold + desaturated | Symmetrical + low angle | Slow push-in |
| Japanese / healing | Side window + soft diffusion | Cool white + overexposed | Rule of thirds + negative space | Static / subtle push |
| Shocking / adrenaline | Side rim + high contrast | Cool + high saturation | Diagonal + dutch tilt | Tracking + handheld |

---

### Character Performance

AI models cannot "react in the moment" (Meisner). They need **pre-scripted physical triggers** (Stanislavski): describe what the body does, not what the emotion is.

```
❌  Character looks surprised at the letter.
    (Model must infer "surprise" → unpredictable output)

✅  Character sees Hogwarts crest on envelope; pupils dilate;
    mouth opens slightly; body leans back 5 degrees.
    (Model executes explicit physical sequence → consistent output)
```

**Emotion → Action library:**

| Emotion | Physical Actions |
|---------|-----------------|
| Surprise | Eyes widen → head tilts back slightly → mouth opens → 1s pause |
| Sadness | Gaze drops → breathing slows → fingers curl → shoulders sag |
| Joy | Eyes crinkle → cheeks lift → body leans forward → chin tilts up |
| Awe | Head tilts up → mouth parts → hands lower to sides → stillness |

---

### Multi-Shot & Audio Sync

Based on the [EvalVerse](https://arxiv.org/abs/2605.23271) professional benchmark framework. **Not yet implemented** — documented here as the roadmap for when multi-shot T2V models mature.

**Multi-shot sequencing:**
- Logic: scene consistency, spatial continuity, no generation artifacts across cuts
- Rhythm: shot duration rationality, pacing aligned with emotional beats
- Prompt pattern when supported: explicit continuity markers (`same lighting setup`, `character maintains position from previous shot`)

**Audio synchronization:**
- Vocal: acoustic quality matching character profile, lip-sync phoneme alignment
- Soundscape: ambient sound matching environment, musical score sync with visual cuts
- Limitation: Kling / Sora / Wan2.1 currently generate silent video — this layer activates when audio-capable models are widely available

---

## Integration

**Opt-in by default — zero latency overhead unless enabled.**

```python
# Method 1: per-call
orchestrator.template_to_video(
    template_name="owl_letter",
    source_image="photo.jpg",
    enable_video_taste=True,
    user_note="cinematic feel"   # optional signal
)

# Method 2: template-level default
# in templates/owl_letter.json:
{
  "name": "owl_letter",
  "video_taste": {
    "enabled": true,
    "default_dials": {"drama": 8, "motion": 6, "fidelity": 8},
    "theme": "fantasy/magic",
    "target_platform": "douyin/xiaohongshu",
    "anti_defaults": ["no frontal staring", "no flat lighting"],
    "style_anchors": ["amber volumetric light", "shallow DOF", "film grain"]
  }
}
```

| Scenario | Setting |
|----------|---------|
| Batch commercial work (same template, 50+ images) | Off — static prompts are more stable |
| New template debugging | On — Video Read has diagnostic value |
| User provides emotion keywords | On — pass to `user_note` |
| Speed-sensitive production | Off |
| Creative exploration | On — generates varied interpretations |

---

## Quick Start

```bash
# Clone and install
git clone https://github.com/irenezhu1999-lab/Claude-Code-skills-memory.git
cp -r Claude-Code-skills-memory/video-taste ~/.claude/skills/
```

Then in Claude Code:
```
/video-taste [source image] for a "Harry Potter letter arrival" video targeting Douyin
```

See [`SKILL.md`](./SKILL.md) for the full prompt engineering spec and Video Read example library.

---

## References

| Resource | Link |
|----------|------|
| Beat Sheets for AI Video | [cybercorsairs.com](https://cybercorsairs.com/beat-sheets-fix-flat-ai-videos/) |
| Sora 2 Prompt Best Practices | [skywork.ai](https://skywork.ai/blog/sora-2-prompt-authoring-best-practices-2025/) |
| EvalVerse Benchmark (arXiv) | [2605.23271](https://arxiv.org/abs/2605.23271) |
| Original taste-skill | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) |
| text-to-video-gen project | [irenezhu1999-lab](https://github.com/irenezhu1999-lab/text-to-video-gen) |

---

MIT License — built for directors, DPs, and AI video creators who refuse generic output.
