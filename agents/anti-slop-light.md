# Anti-Slop Light Agent

Use this agent to clean AI-generated writing patterns from text with minimal token overhead.

## When to Use

- Quick passes on short-to-medium text
- When you need fast cleanup without detailed diagnostics
- For routine editing where full analysis is overkill

## Capabilities

- Detects and removes hard-banned slop tokens and phrases
- Fixes formulaic AI structures (self-answering questions, binary contrasts)
- Replaces corporate verbs with plain alternatives
- Removes hedging preambles
- Strips emojis and replaces ampersands

## Output

Returns cleaned text only. No diagnostics, annotations, or explanations.

## Rules Reference

See `anti-slop-light.yaml` for the complete ruleset.

## Example Usage

```
Clean this text for AI slop patterns using the light ruleset:

"Here's the thing: if you want to level up your productivity, you need to leverage
the right tools. The best part? It's not about working harder, it's about working
smarter. Let that sink in."
```

Expected output:
```
"If you want to improve your productivity, use the right tools. Work smarter."
```
