# Writing Style Layer - Anti-Slop Agents

Subagents for Claude Code that detect and remove AI-generated writing patterns ("AI slop").

## What These Agents Do

AI models produce recognizable patterns: corporate verbs, formulaic structures, hedging preambles, and artificial enthusiasm markers. These agents identify and clean those patterns while preserving your intended meaning.

## Light vs Heavy

| Feature | Light | Heavy |
|---------|-------|-------|
| Lines | ~120 | ~600 |
| Token cost | Low | Higher |
| Diagnostics | No | Yes |
| Severity tiers | No | Critical/Warning/Notice |
| Configurable modes | No | Aggressive/Balanced/Conservative |
| Claude-specific rules | No | Yes |
| ChatGPT-specific rules | No | Yes |
| Output | Cleaned text only | Configurable |

**Use Light** for quick passes on routine text.

**Use Heavy** for detailed editing, auditing, or when you need to understand what was flagged.

## Installation

### Global Setup (All Projects)

Copy the agent definitions to your global Claude Code config:

```bash
# Create agents directory if it doesn't exist
mkdir -p ~/.claude/agents

# Copy agent definitions
cp agents/anti-slop-light.md ~/.claude/agents/
cp agents/anti-slop-heavy.md ~/.claude/agents/

# Copy rule files to a location Claude can reference
cp anti-slop-light.yaml ~/.claude/
cp anti-slop-heavy.yaml ~/.claude/
```

### Project-Specific Setup

Copy files to your project's `.claude/` directory:

```bash
mkdir -p .claude/agents
cp agents/*.md .claude/agents/
cp *.yaml .claude/
```

## Usage

Once installed, invoke the agents in Claude Code:

```
Clean this text using the anti-slop-light agent:
[your text here]
```

```
Analyze this text with anti-slop-heavy in diagnostic mode:
[your text here]
```

## What Gets Flagged

### Hard Bans (Always Removed)
- Tokens: unlock, vibes, synergy, paradigm, stakeholder, bandwidth, learnings, actionable, impactful, holistic, robust, scalable, ecosystem, etc.
- Phrases: "here's the thing", "at the end of the day", "the brutal truth", "let that sink in", "move the needle", etc.
- All emojis in prose
- Ampersands (replaced with "and")

### Structure Patterns
- Self-answering questions: "The best part? You already know."
- Binary contrasts: "It's not about X, it's about Y"
- Negation-affirmation: "No fluff. No hype. Just results."
- Importance announcements: "Here's what matters:"
- Imagine openings: "Picture this..."

### Corporate Verbs
- leverage -> use
- utilize -> use
- facilitate -> help
- implement -> build
- showcase -> show

### Hedging Language
- "It's worth noting"
- "I would argue that"
- "Needless to say"

## Heavy-Only Features

### Severity Tiers
- **Critical**: Unmistakable AI slop. Always fix.
- **Warning**: Strong AI signal. Fix unless context justifies.
- **Notice**: Mild tendency. Flag for awareness.

### Model-Specific Rules
- **Claude**: Framing language, moral padding, epistemic hedging, synthesis sentences
- **ChatGPT**: Marketing rhythm, authenticity signaling, hook questions, listicle energy

## License

MIT
