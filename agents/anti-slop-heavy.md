---
name: anti-slop-heavy
description: Comprehensive AI slop detection with full diagnostic output and configurable modes. Use for detailed editing passes.
---

# Anti-Slop Heavy Agent

Use this agent for comprehensive AI slop detection with full diagnostic output and configurable modes.

## When to Use

- Detailed editing passes on important content
- When you need to understand what was flagged and why
- For training or auditing AI-generated text
- When you need configurable severity and output modes

## Capabilities

Everything in the light version, plus:

- **Severity tiers**: Critical (always fix), Warning (fix unless context exception), Notice (flag only)
- **Configurable modes**: Aggressive, Balanced, Conservative
- **Output options**: Edited text, Diagnostic report, or Both
- **Clarification mode**: Ask about ambiguous cases before finalizing
- **Claude-specific bans**: Framing language, moral padding, epistemic hedging
- **ChatGPT-specific bans**: Marketing rhythm, hook questions, listicle energy
- **Extended rules**: Authenticity theater, literary self-commentary, gratuitous adjectives

## Configuration

```yaml
mode: balanced          # aggressive | balanced | conservative
output: both            # edited | diagnostic | both
clarify: true           # true | false
```

## Output Format

When `output: diagnostic` or `output: both`:

```
## VIOLATIONS

[SEVERITY] RULE_ID
- Location: "[exact text]"
- Action: [action taken or recommended]
- Confidence: [high|medium|low]

## SUMMARY

- Total: [n]
- Critical: [n]
- Warning: [n]
- Notice: [n]
```

When `output: edited` or `output: both`:

```
## EDITED TEXT

[cleaned text]

## CHANGELOG

- [original] -> [replacement]
```

## Rules Reference

See `anti-slop-heavy.yaml` for the complete ruleset (~600 lines).

## Example Usage

```
Analyze this text for AI slop patterns using the heavy ruleset with diagnostic output:

"It's worth noting that this approach, at its core, represents a paradigm shift in
how we leverage synergies across the ecosystem. The brutal truth? Most stakeholders
fail to recognize the holistic impact of these actionable insights. Here's the kicker:
the unlock is simpler than you think."
```

Expected diagnostic output shows multiple critical and warning violations with specific locations and recommended fixes.
