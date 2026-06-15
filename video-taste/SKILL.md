---
name: video-taste
description: Anti-slop video generation skill for AI-driven short video pipelines. Applies brief inference, Video Read declaration, and three dials (DRAMA / MOTION / FIDELITY) before writing any image or video prompt. Stops the model from defaulting to generic AI-looking output.
---

# video-taste: Anti-Slop Video Generation Skill

> Adapted from taste-skill (Leonxlnx/taste-skill) for AI video pipelines (Keling / Replicate / Wan2.1).
> Every rule is contextual. Read the source image and brief first. Do not jump to defaults.

---

## 0. VIDEO READ（生成前先读意图）

在写任何 image prompt 或 video prompt 之前，先输出一行 **Video Read**，声明你对这个任务的理解。

### 0.A 读这些信号

1. **模板类型** — 魔法/奇幻、写实人像、产品展示、动作/运动、情绪短片
2. **源图信号** — 人物年龄/性别/表情、服装风格、背景环境、光线质感
3. **情绪关键词** — 用户说的词："神圣感"、"可爱"、"震撼"、"日系"、"电影感"、"爆款"
4. **受众** — 发抖音的（情绪共鸣优先）vs 发小红书的（颜值美感优先）vs 内部测试（技术验证优先）
5. **人脸保真度优先级** — 商业客片（高，必须像本人）vs 创意内容（中，风格化可以）vs 纯效果测试（低）

### 0.B 输出 Video Read（一行）

格式：
> **"Reading this as: [主题类型]，[受众/平台]，情绪基调 [X]，镜头语言倾向 [Y]，人脸保真度优先级 [高/中/低]。"**

示例：
- *"Reading this as: 哈利波特魔法来信，抖音/小红书受众，情绪基调：惊喜+神圣感，镜头语言：慢推近景+光效粒子，人脸保真度优先级：高。"*
- *"Reading this as: 奇幻骑士变身，B站特效受众，情绪基调：热血+震撼，镜头语言：快切+大景别运动，人脸保真度优先级：中。"*
- *"Reading this as: 日系写真风格化，小红书受众，情绪基调：清冷+治愈，镜头语言：固定浅景深，人脸保真度优先级：高。"*

### 0.C 如果信号不足，问一个问题

只问一个，绝不问多个。例：*"这条视频是主打颜值美感还是效果震撼？"*

如果可以从源图推断，**不要问，直接声明 Video Read 并执行。**

### 0.D Anti-Default Discipline（反默认陷阱）

AI 视频生成的默认陷阱，主动绕过：

- ❌ 人物正面直视镜头、僵硬微笑（改：3/4侧脸、自然神情）
- ❌ 纯色或渐变虚化背景（改：有景深层次的真实场景）
- ❌ 光线平淡均匀（改：有方向感的戏剧性打光——侧光、逆光、顶光）
- ❌ 动作幅度极小、"安全感"过强（改：有明确动作弧线）
- ❌ prompt 里堆砌形容词（beautiful, amazing, stunning）（改：具体描述镜头行为）
- ❌ 每张图都用同一套构图（改：根据 DRAMA 旋钮决定景别和构图变化幅度）

---

## 1. 三个旋钮（Three Dials）

Video Read 完成后，设定三个旋钮。所有 prompt 的写法都由这三个值驱动。

```
DRAMA: 7        # 1=纪录片平静, 10=好莱坞大片
MOTION: 6       # 1=静帧微动, 10=高速剪辑+镜头追踪
FIDELITY: 8     # 1=风格化优先, 10=必须和原图人脸完全一致
```

**基准值：7 / 6 / 8**（商业客片默认值）。根据 Video Read 推断实际值。

### 1.A 旋钮推断表

| 信号 | DRAMA | MOTION | FIDELITY |
|---|---|---|---|
| 魔法/奇幻主题 | 8-9 | 5-7 | 7-8 |
| 写实人像/商业客片 | 5-6 | 3-4 | 9-10 |
| 热血/动作/变身 | 9-10 | 8-10 | 5-6 |
| 日系/小清新/治愈 | 4-5 | 3-4 | 7-8 |
| 爆款内容测试 | 7-8 | 6-7 | 6-7 |
| 纯技术验证 | 5 | 5 | 5 |

### 1.B 旋钮如何驱动 Prompt

**DRAMA 驱动构图和光线描述：**
- DRAMA ≤ 4：自然光，平稳构图，无戏剧性元素
- DRAMA 5-7：有方向感的光线，轻微不对称构图，有前景遮挡
- DRAMA ≥ 8：强侧光/逆光/顶光，大景深对比，特效粒子或光晕

**MOTION 驱动镜头运动描述：**
- MOTION ≤ 3：固定镜头或极慢推镜
- MOTION 4-6：缓慢推镜/拉镜，角色有明确动作弧线
- MOTION ≥ 7：镜头跟随运动，快速切换，有加速/减速感

**FIDELITY 驱动人脸描述权重：**
- FIDELITY ≤ 5：风格化优先，可接受人脸有明显变化
- FIDELITY 6-7：大致保持人脸特征，轻微风格化可接受
- FIDELITY ≥ 8：人脸特征必须精确，prompt 里需加 "preserve facial identity", "exact likeness"

---

## 2. IMAGE PROMPT 规范（四宫格生成）

### 2.A 四宫格布局语言

必须用空间位置描述，不能只用 Panel 1/2/3/4：

| 宫格位置 | 英文描述 | 用途 |
|---|---|---|
| 左上 | top-left panel | 起始帧/全景建立 |
| 右上 | top-right panel | 动作开始/环境特写 |
| 左下 | bottom-left panel | 动作高潮/情绪最强 |
| 右下 | bottom-right panel | 结束帧/情绪落点 |

### 2.B Prompt 结构模板

```
[Identity lock] + [Scene/Setting] + [Four panel layout] + [Lighting] + [Style/Mood] + [Anti-defaults]
```

**Identity lock（FIDELITY ≥ 7 时必须有）：**
```
The subject is [性别+年龄段] with [发色+发型+脸型关键词], preserve exact facial identity throughout all panels.
```

**Four panel layout（按旋钮值写）：**
```
Four-panel 2x2 grid:
- top-left: [起始状态描述]
- top-right: [过渡/动作开始]
- bottom-left: [高潮/特效最强]
- bottom-right: [结尾/情绪落点]
```

**Anti-defaults 注入（每次必加）：**
```
Avoid: frontal staring pose, flat even lighting, symmetrical composition, generic gradient background.
Instead: [根据 DRAMA/MOTION 值选择的具体替代方案]
```

### 2.C 常见主题的 Anti-Default 替代方案

| 主题 | 禁止的默认写法 | 替代写法 |
|---|---|---|
| 魔法/奇幻 | "magical effects around the person" | "shafts of amber light piercing through stone archway, floating parchment letters with wax seals, shallow depth of field on owl wing" |
| 写真人像 | "beautiful portrait with soft background" | "window side light casting half-shadow on face, linen texture visible, slight underexposure in shadow side" |
| 变身/动作 | "person transforming with cool effects" | "mid-air freeze frame, cloak billowing left against wind, motion blur on sword arc, sharp focus on face" |
| 日系写真 | "Japanese style cute girl" | "dappled light through cherry blossom, film grain texture, 35mm lens compression, subject at rule-of-thirds" |

---

## 3. VIDEO PROMPT 规范（Keling / Wan2.1）

### 3.A 导演式六层结构（核心）

**写 video prompt 等于给摄影师下拍摄指令，必须覆盖六层：**

```
[景别] → [机位角度] → [镜头运动] → [镜头参数/景深] → [光线方向] → [动作叙事]
```

每层必须用具体词汇，禁止模糊描述：

| 层 | 可用词汇 | 禁止写法 |
|---|---|---|
| **景别** | extreme close-up / close-up / medium shot / wide / extreme wide | "近景"、"远景" |
| **机位** | eye-level / low angle / high angle / dutch tilt / bird's eye | "正面"、"从下面" |
| **镜头运动** | push-in / pull-back / pan left / tracking shot / crane up / static | "移动镜头" |
| **镜头参数** | 85mm portrait lens / 24mm wide / shallow DOF / deep focus | "虚化背景" |
| **光线** | key light from left / rim backlight / top light / golden hour side light | "光线很好" |
| **动作叙事** | 三段弧：起始状态 → 过渡动作 → 结尾状态 | 只写静态描述 |

**完整示例：**
```
<<<image_1>>> as opening. Close-up shot, eye-level, slow push-in toward subject's face,
85mm portrait lens with shallow depth of field, rim backlight from behind with warm amber glow.
Subject stands still holding letter; then slowly raises gaze toward camera; finally breaks into 
a surprised smile as golden particles drift across frame.
```

### 3.B 顺序动作规则（防 Distortion）

AI 视频对**同时发生的多个动作**处理最差，必须拆成先后顺序：

❌ 错误写法：
```
Subject turns around while simultaneously throwing the letter into the air with both arms raised.
```

✅ 正确写法：
```
Subject slowly turns around; then raises both arms; letter drifts upward from open palms.
```

**拆分原则：**
- 用分号 `;` 分隔动作阶段，不用 `while` / `simultaneously` / `at the same time`
- 每个阶段只有一个主动作
- 配合镜头运动也要分阶段（先建立构图，再开始运动）

### 3.C Prompt 完整结构模板

```
[Image reference hook] + [导演六层结构] + [动作三段弧] + [Atmosphere/FX] + [Negative prompt]
```

**Image reference hook（Keling Omni 多图参考模式，panels_only / source_first 时必须有）：**
```
<<<image_1>>> as opening, following the sequence <<<image_2>>>, <<<image_3>>>, <<<image_4>>>
```

**镜头运动（按 MOTION 值选）：**
- MOTION ≤ 3：`static camera, subtle breathing motion only`
- MOTION 4-6：`slow push-in from wide establishing shot, ending in medium close-up`
- MOTION ≥ 7：`handheld tracking shot following subject, with natural camera shake and momentum`

**动作叙事弧（按 DRAMA 值选深度）：**
- DRAMA ≤ 5：`Subject [静态动作]; gaze shifts [方向]; subtle [情绪表现].`
- DRAMA 6-8：`Subject begins [起始]; transitions through [过渡，拆分动作]; arrives at [高潮状态].`
- DRAMA ≥ 9：`[环境建立]; Subject [起始动作]; [特效出现，用分号分段]; [情绪落点 + 最终构图].`

**Negative prompt（必须加）：**
```
low quality, blurry face, distorted features, morphing identity, unnatural body proportions,
flickering, abrupt cuts, color inconsistency between frames, simultaneous contradictory motions
```

### 3.D 模型特性差异

| 模型 | 强项 | Prompt 侧重 |
|---|---|---|
| **Keling Omni** | 人物物理表现、运动真实感 | 重点写动作叙事 + 光线，人脸细节交给 FIDELITY dial |
| **Wan2.1** | 风格化美术、插画质感 | 重点写风格词汇 + 色调，动作叙事可以抽象 |
| **Minimax** | 情绪表达、镜头语言 | 重点写情绪状态 + 叙事节奏 |

---

## 4. 模板 JSON 规范

每个模板 `templates/*.json` 应包含 `video_taste` 字段：

```json
{
  "name": "模板名称",
  "video_taste": {
    "default_dials": {
      "drama": 8,
      "motion": 6,
      "fidelity": 8
    },
    "theme": "fantasy/magic",
    "target_platform": "douyin/xiaohongshu",
    "anti_defaults": [
      "no frontal staring pose",
      "no flat even lighting",
      "no generic gradient background"
    ],
    "style_anchors": [
      "amber volumetric light",
      "shallow depth of field",
      "film grain texture"
    ]
  },
  "image": { ... },
  "video": { ... }
}
```

---

## 5. 工作流程

```
用户传入：源图 + 模板名称（可选：情绪词/平台/受众）
    ↓
Step 0: 读源图 + 模板 → 输出 Video Read（一行）
    ↓
Step 1: 根据 Video Read → 推断三旋钮值（DRAMA / MOTION / FIDELITY）
    ↓
Step 2: 根据旋钮值 → 动态生成 image prompt（四宫格布局 + Anti-Default 注入）
    ↓
Step 3: 调用 GPT Image API 生成四宫格
    ↓
Step 4: 根据旋钮值 → 动态生成 video prompt（镜头语言 + 动作弧线 + 负向 prompt）
    ↓
Step 5: 提交 Keling 任务
```

---

## 6. Video Read 示例库（供 Claude 参考）

```
owl_letter 模板 + 20多岁女性源图 + 无额外信息：
→ "Reading this as: 哈利波特魔法来信，小红书/抖音受众，情绪基调：惊喜+神圣感，
   镜头语言：慢推近景+光效粒子，人脸保真度优先级：高。"
→ DRAMA: 8 / MOTION: 5 / FIDELITY: 9

alicorn 模板 + 全身照 + 用户说"要震撼"：
→ "Reading this as: 独角飞马奇幻骑行，B站/抖音受众，情绪基调：震撼+史诗感，
   镜头语言：大景别运动+跟随镜头，人脸保真度优先级：中。"
→ DRAMA: 9 / MOTION: 8 / FIDELITY: 6

quidditch 模板 + 全身照 + 无额外信息：
→ "Reading this as: 魁地奇追球，游戏/体育受众，情绪基调：热血+紧张感，
   镜头语言：高速追踪+运动模糊，人脸保真度优先级：中高。"
→ DRAMA: 9 / MOTION: 9 / FIDELITY: 7
```

---

## 7. 和 text-to-video-gen 的集成方式

### 7.A 按需触发（默认关闭，不增加等待时长）

video-taste 是**可选增强层**，不是强制路径。有两种触发方式：

**方式 1 — 调用时手动开启：**
```python
orchestrator.template_to_video(
    template_name="owl_letter",
    source_image="photo.jpg",
    enable_video_taste=True,   # 显式开启，增加 ~2s Claude 调用
    user_note="要有电影感"       # 可选，传给 Video Read 的额外信号
)
```

**方式 2 — 模板级默认开启：**
在 `templates/*.json` 里加 `"video_taste": true`，该模板每次都自动走 Video Read 流程：
```json
{
  "name": "owl_letter",
  "video_taste": true,
  ...
}
```

**默认行为（不传参、模板也没设）：跳过 video-taste，直接用静态 prompt，零额外耗时。**

### 7.B 触发后的流程

```
enable_video_taste=True
    ↓
Claude 调用（~1-2s，~500 token）
输入：源图描述 + 模板名 + user_note
输出：Video Read 一行 + DRAMA/MOTION/FIDELITY 三值 + 动态 image_prompt + 动态 video_prompt
    ↓
动态 prompt 覆盖模板 json 里的静态 prompt
    ↓
正常走 GPT Image → Keling 流程
```

### 7.C 什么时候值得开

| 场景 | 建议 |
|---|---|
| 批量商业客片（同模板跑几十张）| 关闭，静态 prompt 更稳定可控 |
| 新模板调试，想看 AI 怎么理解 | 开启，Video Read 本身有调试价值 |
| 用户有明确情绪词（"震撼"、"日系"）| 开启，把信号传给 user_note |
| 快速出片、对等待时长敏感 | 关闭 |
| 想尝试更有创意的 prompt 变体 | 开启 |
