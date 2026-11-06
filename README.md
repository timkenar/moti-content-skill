# MOTI Content Skill

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)
![Agent Skill](https://img.shields.io/badge/agent-skill-black.svg)

An agent skill that turns AI and deep-tech news into **15-22 second vertical video scripts** (Reels, TikTok, YouTube Shorts) that read like a person wrote them.

Built for **MOTI**, a short-form video brand covering the intersection of AI, society, and deep tech.

---

## What it does

Hand your agent a news link, a pasted article, or a headline. The skill makes it act as MOTI's Executive Producer and return a ready-to-shoot package:

| Section | What you get |
| --- | --- |
| **Story title & strategy** | A working title plus the hook strategy used (A, B, or C) |
| **Visual concept** | A-roll (what's on camera) and B-roll (cutaways, overlays, footage) |
| **Script** | 40-60 spoken words, timed for 15-22 seconds, with the word count shown |
| **Caption** | A story-specific caption, never a recycled template |

## Why it exists

AI-written scripts are easy to spot. They lean on the same tics: *"This isn't X, this is Y."* *"Let that sink in."* Perfectly balanced sentences. The same call to action on every video. Audiences scroll past.

This skill is a rulebook that strips those patterns out and forces variety from one video to the next.

## How it works

### 1. Kill the AI fingerprint

| Rule | What it enforces |
| --- | --- |
| No self-handicapping | Bans defensive filler like *"Believe it or not"* and *"I know it sounds crazy, but"*. Facts are stated directly. |
| No binary clichés | Bans the *"This isn't X... this is Y"* formula and all its variants. |
| Asymmetrical pacing | Short, blunt lines mixed with rapid-fire context. No sing-song symmetry. |
| Format variety | Alternates between clean paragraph scripts and visual-cue heavy scripts. |
| Unique sign-offs | Every CTA is tied to the story. No canned "follow for more". |
| Typography | Clean spacing, no stray tags or code artifacts in the output. |

On top of that, an **extended ban list** blocks common AI tells (*"Here's the thing"*, *"Buckle up"*, *game-changer*, *delve*, em dashes, reflexive lists of three, and more).

### 2. Three hook strategies

Each script uses one of these, and the skill rotates them so consecutive videos never share a structure:

- **A. Cold Open Fact:** drop straight into the action or the data point. No setup.
- **B. Hypocrisy / Conflict:** build the story around two opposing forces or an institutional contradiction.
- **C. Systems View:** zoom out to the physical infrastructure (power lines, shipping lanes, mineral mines) behind the software.

### 3. Built-in guardrails

- **Accuracy:** every number, name, and quote has to come from the source. Stats are never invented or inflated to sharpen a hook.
- **Run-time control:** word count is checked against the 15-22 second window.
- **Self-check:** before replying, the agent runs a checklist covering length, banned patterns, pacing, sign-off, facts, and typography.

## Installation

### Option 1: Skills CLI (works with most agents)

```bash
npx skills add timkenar/moti-content-skill
```

Add `-g` to install it globally for your user instead of the current project.

### Option 2: Manual

Clone the repo, then copy or symlink the skill folder into your agent's skills directory:

```bash
git clone https://github.com/timkenar/moti-content-skill.git
ln -s "$PWD/moti-content-skill/skills/moti-content" ~/.claude/skills/moti-content
```

| Agent | Skills directory |
| --- | --- |
| Claude Code | `~/.claude/skills/` |
| OpenCode | `~/.config/opencode/skills/` or `~/.agents/skills/` |
| Other tools | See your agent's docs for its skills folder |

A symlink means a `git pull` updates the skill everywhere at once.

### Option 3: Chat apps

- **Claude.ai:** zip the `skills/moti-content` folder and upload it as a custom skill in your settings.
- **Apps without skill support:** paste the body of [`SKILL.md`](skills/moti-content/SKILL.md) into a project's custom instructions.

## Usage

The skill loads automatically when you ask for MOTI or short-form tech video content. Example prompts:

```text
Write a MOTI script for this: https://example.com/some-ai-news-story
```

```text
Turn these three headlines into MOTI reels:
1. ...
2. ...
3. ...
```

```text
Give me a Systems View (Approach C) script on this chip export story: <link>
```

```text
Same story, paragraph format this time, and a sharper caption.
```

## Output format

```markdown
### [Story Title]
**Strategy:** [A / B / C], [Approach name]

**Visual Concept**
- A-Roll: ...
- B-Roll: ...

**Script** ([N] words · ~[S]s)

...

**Caption**
...
```

## Repository structure

```text
moti-content-skill/
├── skills/
│   └── moti-content/
│       └── SKILL.md      # The skill: role, rules, workflow, output format, self-check
├── LICENSE
└── README.md
```

## Make it your own

Everything lives in [`skills/moti-content/SKILL.md`](skills/moti-content/SKILL.md). Fork the repo and change:

- the brand name and beat (swap MOTI and "AI, society, and deep tech" for your own),
- the ban list, to match the tics you see in your niche,
- the run-time window and word range,
- the hook strategies.

## License

[MIT](LICENSE) © timkenar
