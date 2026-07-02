---
name: cinematography-director
description: Professional cinematography and directing knowledge base for AI video generation. Provides shot language vocabulary, lighting setups, composition laws, Stanislavski performance direction, and emotion-visual mapping. Use when making creative decisions about how to shoot a scene, not when generating prompts directly.
---

# cinematography-director: Professional Directing Knowledge Base

> This skill provides the **knowledge foundation** for cinematic video generation.  
> It does NOT generate prompts — use **video-taste** for that.  
> This skill answers: "How should I shoot this scene?" before you write the prompt.

---

## When to Use This Skill

**Trigger scenarios:**
- User asks "How should I shoot this?" or "What shot type works here?"
- Choosing between multiple creative approaches (wide vs close-up, static vs tracking)
- Reviewing a video and diagnosing why it feels "off"
- Planning a multi-shot sequence
- User mentions cinematography terms (三点布光, Rembrandt, OTS, Dutch tilt)

**Do NOT use this skill when:**
- User just wants a prompt generated → use **video-taste** instead
- Technical troubleshooting (API errors, pipeline bugs) → use **viral-agent-lead**

---

## 1. Shot Language Dictionary

### 1.A Shot Sizes (景别)

| English Term | 中文 | Frame Coverage | Use Case |
|---|---|---|---|
| **Extreme Wide Shot (EWS)** | 大远景 | Entire environment, subject tiny | Establishing location, scale, isolation |
| **Wide Shot (WS)** | 远景 | Full body + significant environment | Context, blocking, spatial relationships |
| **Medium Wide Shot (MWS)** | 中远景 | Full body, less environment | Action sequences, walk-and-talk |
| **Medium Shot (MS)** | 中景 | Waist up | Dialogue, natural conversation distance |
| **Medium Close-Up (MCU)** | 中近景 | Chest up | Emotional dialogue, slight intimacy |
| **Close-Up (CU)** | 近景 | Head and shoulders | Emotion focus, reaction shots |
| **Extreme Close-Up (ECU)** | 特写 | Eyes, mouth, hands, objects | Dramatic emphasis, detail revelation |
| **Cowboy Shot** | 牛仔镜头 | Mid-thigh up (gun holster visible) | Western action, confident stance |
| **Over-The-Shoulder (OTS)** | 过肩镜头 | From behind one person toward another | Dialogue, POV intimacy, power dynamics |

### 1.B Camera Angles (机位)

| Term | 中文 | Psychological Effect |
|---|---|---|
| **Eye-Level** | 平视 | Neutral, equal power, natural POV |
| **Low Angle** | 仰拍 | Subject appears powerful, dominant, heroic |
| **High Angle** | 俯拍 | Subject appears vulnerable, weak, overwhelmed |
| **Bird's Eye / Overhead** | 顶拍 | God's eye view, disorientation, pattern emphasis |
| **Dutch Tilt (Canted)** | 倾斜 | Unease, tension, disorientation, stylization |
| **Worm's Eye** | 极低仰拍 | Extreme power imbalance, awe, surrealism |

### 1.C Camera Movement (镜头运动)

| Term | 中文 | Execution | Emotional Effect |
|---|---|---|---|
| **Static** | 固定 | No camera movement | Observation, stability, documentary feel |
| **Push-In (Dolly In)** | 推镜 | Move toward subject | Increasing intimacy, revelation, focus |
| **Pull-Back (Dolly Out)** | 拉镜 | Move away from subject | Context reveal, isolation, emotional distance |
| **Pan** | 摇镜 | Horizontal rotation on axis | Follow action, reveal environment |
| **Tilt** | 俯仰 | Vertical rotation on axis | Scale reveal (low-to-high), inspection |
| **Tracking Shot (Dolly)** | 跟拍 | Move parallel to subject | Follow action, sustained tension, walk-and-talk |
| **Crane / Boom** | 升降 | Vertical movement | God's eye transition, epic scale |
| **Handheld** | 手持 | Natural shake, follows operator | Immediacy, chaos, documentary realism |
| **Steadicam** | 斯坦尼康 | Smooth tracking through obstacles | Fluid pursuit, immersive following |
| **Whip Pan** | 快速摇镜 | Rapid horizontal blur | Time skip, disorientation, energy burst |

### 1.D Lens Characteristics (镜头参数)

| Focal Length | Field of View | Depth Compression | Common Use |
|---|---|---|---|
| **14-24mm (Ultra-Wide)** | 极广 | Deep focus, exaggerated perspective | Architecture, cramped spaces, surrealism |
| **24-35mm (Wide)** | 广角 | Deep focus, mild distortion | Establishing shots, environmental context |
| **50mm (Normal)** | 标准 | Natural perspective, matches human eye | General coverage, natural look |
| **85-135mm (Portrait)** | 中长焦 | Shallow DOF, flattering compression | Portraits, emotional close-ups, isolation |
| **200mm+ (Telephoto)** | 长焦 | Strong compression, very shallow DOF | Sports, wildlife, voyeuristic surveillance feel |

**Depth of Field (DOF) Control:**
- **Shallow DOF** — Subject sharp, background blurred (isolation, focus, glamour)
- **Deep DOF** — Everything sharp (context, complexity, wide shots)

---

## 2. Lighting Setups (布光方案)

### 2.A Three-Point Lighting (三点布光 — 基础)

```
        [Key Light]
           ↓ 45°
         Subject ←——→ [Fill Light]
            ↑ behind
        [Back/Rim Light]
```

| Light | Position | Intensity | Purpose |
|---|---|---|---|
| **Key Light** | 45° front-left/right, above eye level | Brightest (100%) | Primary illumination, defines form |
| **Fill Light** | Opposite side of key, lower intensity | 30-50% of key | Reduces shadow contrast, controls mood |
| **Back/Rim Light** | Behind subject, high angle | 50-75% of key | Separates subject from background, depth |

**Mood Control via Fill Ratio:**
- **High Fill (1:1 ratio)** — Soft, even lighting (comedy, beauty, commercial)
- **Low Fill (8:1 ratio)** — Deep shadows, drama (thriller, noir, horror)

### 2.B Named Lighting Styles

| Style | Setup | Emotion | Example Use |
|---|---|---|---|
| **Rembrandt Light** | Key 45° high-left, creates triangle under eye on shadow side | Dramatic, classical, thoughtful | Portraits, interviews, serious drama |
| **Butterfly Light** | Key directly above and in front, creates butterfly shadow under nose | Glamorous, beauty, high fashion | Fashion, beauty shots, classic Hollywood |
| **Loop Light** | Key 30-45° to side, creates small nose shadow loop toward cheek | Flattering, natural, approachable | General portraiture, corporate headshots |
| **Split Light** | Key 90° to side, lights exactly half the face | Dramatic, mysterious, edgy | Film noir, villain shots, tension |
| **Backlighting (Silhouette)** | Strong light behind subject, no/minimal fill | Mystery, anonymity, romance | Sunset scenes, identity concealment, music videos |
| **High-Key Lighting** | Bright, even, minimal shadows (high fill ratio) | Happy, upbeat, clean | Sitcoms, commercials, optimistic scenes |
| **Low-Key Lighting** | Dark, high contrast, deep shadows (low fill ratio) | Moody, tense, serious | Thrillers, horror, dramatic reveals |

### 2.C Natural Light Qualities

| Light Source | Color Temperature | Quality | Best Use |
|---|---|---|---|
| **Golden Hour (sunrise/sunset)** | 2500-3500K (warm orange) | Soft, directional, flattering | Portraits, romance, nostalgia |
| **Blue Hour (twilight)** | 7000-10000K (cool blue) | Diffused, ethereal | Atmosphere, calm, melancholy |
| **Overcast / Cloudy** | 6500K (neutral) | Soft, shadowless, even | Documentary, natural skin tones |
| **Direct Midday Sun** | 5500K (neutral-cool) | Harsh, top-down, high contrast | Avoid for portraits; use for harsh realism |
| **Window Light (indirect)** | 5000-7000K | Soft directional, wraps around | Intimate portraits, product shots |

### 2.D Practical Lighting (实用光源)

| Source | Emotional Association | Creative Use |
|---|---|---|
| **Candle / Fire** | Warmth, intimacy, danger | Flickers create alive, unpredictable feel |
| **Neon Signs** | Urban, modern, loneliness | Color-motivated lighting, cyberpunk aesthetic |
| **Streetlights** | Isolation, surveillance, noir | Pools of light in darkness, path-marking |
| **Car Headlights** | Tension, reveal, pursuit | Moving light source, crossing beams |
| **Phone / Screen Glow** | Isolation, modern life, secrecy | Underlit face, eerie blue cast |

---

## 3. Composition Laws (构图法则)

### 3.A The Rule of Thirds (三分法)

Divide frame into 9 equal sections (3x3 grid). Place subject/horizon on intersections or lines.

**Why it works:** Creates dynamic tension, avoids dead-center stagnation.

**When to break it:** Symmetry for unease (Wes Anderson), centered power (Stanley Kubrick).

### 3.B Leading Lines (引导线)

Use roads, fences, shadows, architecture to guide viewer's eye toward subject.

**Example:** Railroad tracks converging on a walking figure.

### 3.C Depth Through Layering (景深层次)

- **Foreground** — Create frame-within-frame (doorways, branches, bokeh)
- **Midground** — Subject
- **Background** — Context, separation

**Why it works:** Adds 3D feel to 2D image, prevents flatness.

### 3.D Negative Space (留白)

Empty space around subject. More space = isolation, contemplation, scale.

**Cultural note:** 
- Western: subject often fills frame (energy, intimacy)
- Eastern (Chinese/Japanese): generous negative space (philosophy, breath, solitude)

### 3.E Symmetry vs Asymmetry

| Composition | Emotion | Example Use |
|---|---|---|
| **Symmetry** | Order, perfection, unease (too perfect), authority | Wes Anderson, Kubrick, formal architecture |
| **Asymmetry** | Dynamism, realism, tension | Action sequences, documentary, instability |

### 3.F Headroom and Look Room

- **Headroom** — Space above subject's head. Too much = ungrounded; too little = claustrophobic.
- **Look Room (Nose Room)** — Space in direction subject is looking/moving. More room in front = natural; more behind = tension.

---

## 4. Performance Direction (Stanislavski Method)

### 4.A The Core Principle

**Do NOT direct actors with abstract emotions ("be sad", "look shocked").**

**Instead:** Give **physical actions** and **objectives**.

### 4.B Emotion → Physical Action Translation

| Abstract Emotion | ❌ Vague Direction | ✅ Stanislavski Physical Action |
|---|---|---|
| **Surprise** | "Look surprised" | "You just heard your name called from a dark room. Turn toward the sound." |
| **Joy** | "Be happy" | "You're trying not to laugh during a serious meeting. Bite your lip, shoulders shake." |
| **Grief** | "Be sad" | "You're trying to read a letter, but your eyes keep blurring. Keep wiping them." |
| **Fear** | "Look scared" | "You hear footsteps behind you. Freeze. Listen. Slowly turn your head." |
| **Anger** | "Be angry" | "You're holding back from slamming the door. Grip the handle tighter, breathe through nose." |
| **Nervousness** | "Look nervous" | "You're about to knock on a door. Raise your hand, hesitate, lower it, raise again." |
| **Confidence** | "Be confident" | "You're walking through a crowd. Make eye contact with strangers, don't look down." |

### 4.C Character Objectives (角色目标)

Every action should answer: **"What does the character WANT in this moment?"**

**Example scene:** Character receives a letter.

- ❌ "She's excited and emotional" → Generic, actor doesn't know what to DO
- ✅ "She wants to confirm this is real before she lets herself believe it. She checks the seal three times, holds it up to the light, smells the parchment." → Actor has clear actions.

### 4.D Physical Beats (动作节拍)

Break performance into **sequential physical beats**, not simultaneous actions.

**Example: "Surprised Reaction"**

Bad direction (simultaneous):
```
She gasps, covers her mouth, and steps back while her eyes widen.
```

Good direction (sequential beats):
```
1. She freezes mid-breath.
2. Her eyes track up from the letter to the sender's face.
3. Her mouth opens slightly.
4. She takes a half-step back.
5. One hand rises toward her chest.
```

---

## 5. Emotion-Visual Mapping Table

This table translates **user emotion keywords** into **concrete directorial decisions**.

| User Says | Mood | Shot Size | Camera Move | Lighting | Color | Performance Direction |
|---|---|---|---|---|---|---|
| **震撼 (Shocking)** | Awe, overwhelm | Start wide → push to CU | Slow push-in or crane up | High contrast, rim backlight | Desaturated or golden | Character frozen, then slow realization |
| **神圣感 (Sacred)** | Reverence, awe | Medium → slow pull-back | Static or slow dolly out | Soft top light, god rays | Warm gold, cool blue shadows | Kneeling, gazing upward, arms slowly open |
| **可爱 (Cute)** | Warmth, affection | MCU or CU | Static or gentle push | Soft high-key, butterfly | Pastel, warm | Tilted head, soft smile, eye contact |
| **日系 (Japanese aesthetic)** | Nostalgia, calm | Medium, rule of thirds | Mostly static, subtle drift | Natural window light, soft | Film grain, muted pastels | Contemplative, looking away, minimal expression |
| **电影感 (Cinematic)** | Epic, serious | Wide establishing → CU | Slow tracking or crane | Low-key, Rembrandt, rim | Rich contrast, film LUT | Slow deliberate actions, strong silhouette |
| **爆款 (Viral hit)** | Energy, hook | CU on face or action | Quick push-in or whip pan | Punchy, saturated | High saturation, neon accents | Direct eye contact, quick gesture, surprise reveal |
| **治愈 (Healing)** | Calm, comfort | Wide with negative space | Slow or static | Soft overcast, even | Desaturated greens, blues | Slow movements, gentle touch, peaceful posture |
| **热血 (Hot-blooded)** | Excitement, action | Wide action → quick CU | Fast tracking, handheld | High contrast, motivated | Warm reds, oranges | Dynamic motion, shouting, fist pump |

---

## 6. Common Cinematic Mistakes to Avoid

### 6.A "The Dead Center Trap"

**Mistake:** Subject always dead-center in frame.

**Fix:** Use rule of thirds, shift subject toward edge, balance with negative space.

### 6.B "The Flat Lighting Trap"

**Mistake:** Even, shadowless lighting (looks like surveillance footage).

**Fix:** Add light direction. Even soft setups need KEY light stronger than fill.

### 6.C "The Simultaneous Action Trap"

**Mistake:** Directing multiple actions at once ("turn around while raising arms and gasping").

**Fix:** Break into sequential beats. One clear action per moment.

### 6.D "The Vague Emotion Trap"

**Mistake:** "Make it feel emotional" / "She's heartbroken" without physical action.

**Fix:** Translate to Stanislavski objectives: "She's trying to compose herself before speaking."

### 6.E "The Zoom vs Dolly Confusion"

- **Zoom** — Lens changes, background doesn't move (unnatural, voyeuristic)
- **Dolly** — Camera moves, background parallaxes (natural, immersive)

**AI models struggle with zoom** — always specify "dolly push-in" or "tracking shot", never "zoom in".

---

## 7. Multi-Shot Sequencing (Future Roadmap)

When AI models support multi-shot generation, use these patterns:

### 7.A Shot-Reverse-Shot (对切镜头)

**Use:** Dialogue, two-character interaction.

**Pattern:**
1. Medium shot of Character A (establish)
2. OTS from A's shoulder toward B
3. OTS from B's shoulder toward A
4. Close-up of A (reaction)
5. Close-up of B (response)

### 7.B The Kuleshov Effect (库里肖夫效应)

**Principle:** Meaning comes from **shot juxtaposition**, not individual shots.

**Example:**
- Shot 1: Man's neutral face
- Shot 2: Bowl of soup → Viewer thinks he's hungry
- Shot 2 (alt): Dead child → Viewer thinks he's grieving

**AI application:** Plan shots in pairs, not isolation. A close-up has different meaning depending on what comes before/after.

### 7.C 180-Degree Rule (轴线规则)

**Rule:** Keep camera on one side of action axis, otherwise subjects appear to flip positions.

**When to break:** Intentional disorientation, character power shift.

---

## 8. Integration with video-taste

### 8.A Workflow Separation

```
User asks creative question (e.g., "How should I shoot a magical letter arrival?")
    ↓
cinematography-director provides knowledge
(e.g., "Use slow push-in, Rembrandt lighting, sequential beats")
    ↓
User/Claude calls video-taste to generate actual prompt
    ↓
video-taste uses that knowledge to write structured prompt
```

### 8.B Example Handoff

**User:** "我想拍一个魔法来信的场景，但不知道该用什么镜头。"

**cinematography-director response:**
```
建议方案：

**景别:** 从 Medium Shot 慢推到 Close-Up
- 开场建立环境（人物+信件+周围空间）
- 推进强调情绪高潮（惊喜表情）

**光线:** Rembrandt + 背光粒子
- 主光从左前方45°打 Rembrandt 三角
- 背后加暖色逆光模拟魔法光芒
- 悬浮粒子需要背光才有体积感

**表演:** Stanislavski 三段式
1. 盯着信封上的封印（确认真实性）
2. 慢慢抬头（意识到意义）
3. 嘴角上扬+眼睛发亮（惊喜释放）

避免：正面直视 + 平光 + 同时做多个动作

现在可以用 /video-taste 生成具体 prompt。
```

**Then:** User invokes `/video-taste` with this knowledge in mind.

---

## 9. Reference Library (Quick Lookup)

### 9.A Shot Size by Emotion Intensity

| Emotion Intensity | Recommended Shot Size |
|---|---|
| Subtle, introspective | Wide or Medium (context matters more than face) |
| Moderate, conversational | Medium or MCU (face + body language) |
| Strong, climactic | CU or ECU (face dominates, environment fades) |

### 9.B Camera Movement by Narrative Purpose

| Narrative Purpose | Movement |
|---|---|
| Reveal environment | Pull-back or crane up |
| Build tension | Slow push-in |
| Follow action | Tracking shot or Steadicam |
| Disorientation / chaos | Handheld or whip pan |
| Observation / documentary | Static |

### 9.C Lighting by Genre

| Genre | Lighting Style |
|---|---|
| Horror / Thriller | Low-key, shadows, practicals (candles, single bulbs) |
| Romance | Golden hour, soft backlight, high fill |
| Sci-Fi | Cool tones, motivated neon, high contrast |
| Comedy | High-key, even, bright |
| Drama | Rembrandt, naturalistic window light, controlled shadows |

---

## 10. Conversation Style

When this skill is active:

- **Be consultative, not prescriptive.** Present 2-3 options with tradeoffs, not "you must do X."
- **Translate vague requests into concrete choices.** If user says "make it emotional," ask "Intimate emotion (close-up, soft light) or overwhelming emotion (wide shot, high contrast)?"
- **Cite this knowledge base.** Say "According to Rembrandt lighting principles..." or "Stanislavski method suggests..." to establish authority.
- **Hand off to video-taste when decisions are made.** Don't write prompts yourself — that's video-taste's job.

---

## 11. Example Conversations

### Example 1: Shot Selection

**User:** "我不知道该用什么景别拍一个人收到信的镜头。"

**Response:**
```
取决于你想强调什么：

**选项 A — Wide Shot (远景)**
- 强调：环境、孤立感、信件在人物生活中的"闯入"
- 适合：信件是意外、打破日常的转折点
- 情绪：客观、距离感

**选项 B — Medium Shot → Push to Close-Up (中景推近景)**
- 强调：情绪变化的过程（从好奇到惊喜）
- 适合：情绪是重点，需要看到表情细节
- 情绪：亲密、代入感（推荐用于商业短视频）

**选项 C — Extreme Close-Up on hands opening letter (特写手部)**
- 强调：动作细节、悬念感
- 适合：信件内容很神秘，延迟揭示
- 情绪：紧张、好奇

你的场景是哪种情绪优先？
```

### Example 2: Lighting Choice

**User:** "我想要那种电影感的光线，但不知道怎么描述。"

**Response:**
```
"电影感"通常指 **Low-Key Lighting with Directional Light**（低调布光+方向性光线）。

具体方案：

**Rembrandt Lighting（推荐）**
- Key light 从左前方45°打下来
- 脸的一侧亮，另一侧暗，暗侧眼睛下方有个三角形光斑
- 适合：严肃对话、戏剧性场景、角色内心戏

**Split Lighting（更极端）**
- Key light 从正侧面90°打
- 脸的一半全亮，一半全暗
- 适合：神秘角色、道德两难、film noir 风格

**避免的陷阱：**
- ❌ "beautiful cinematic lighting" → 太模糊，AI 会给平光
- ✅ "Rembrandt lighting from camera-left, warm key light, cool fill, rim backlight separating from dark background" → 具体可执行

需要我帮你写进 video-taste 的 prompt 吗？
```

### Example 3: Performance Direction

**User:** "我想让角色看起来很惊讶，但 AI 老是生成那种僵硬的表情。"

**Response:**
```
问题出在 "look surprised" 这种抽象指令。AI 不知道"惊讶"该做什么动作。

用 **Stanislavski 物理动作法** 改写：

❌ 原写法：
"Character looks surprised and excited"

✅ 改写（拆分成物理动作）：
"Character freezes mid-motion; eyes track upward from letter to camera; mouth opens slightly; takes a small step back; one hand slowly rises toward chest"

**为什么有效：**
- 每个动作都是具体的、可拍摄的
- 有先后顺序（freeze → eyes → mouth → step → hand）
- 避免"同时做五个动作"导致的畸变

video-taste 的 FLUIDITY dial 会自动加这种动作分解，要不要试试？
```

---

## Credits & Evolution

- **Stanislavski Method** — Constantin Stanislavski, *An Actor Prepares* (1936)
- **EvalVerse Benchmark** — 45-dimension video evaluation framework (2025)
- **Community cinematography patterns** — aggregated from film school curricula, ASC manuals, and practical AI video testing

This skill will expand with:
- Audio sync layer (when models support)
- Multi-shot sequencing patterns (when models support 10+ sec continuous)
- Cultural-specific shot language (e.g., Chinese period drama conventions, Bollywood musical grammar)

---

**Use this skill to THINK like a director. Use video-taste to WRITE like a prompter.**
