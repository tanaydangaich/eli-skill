# eli — Claude Code Skill

Got tired of writing "Explain like I'm [X]" so just created this skill to replace writing so much everytime I need a breakdown of certain topics at varying levels of difficulty. 

Personally, I have paired this with caveman (https://github.com/JuliusBrussee/caveman) to get the same result with lesser tokens. All examples below are caveman + eli combined to give this result.

Explain any concept at any age or expertise level. Works as a Claude Code slash command.

## Install

```bash
mkdir -p ~/.claude/skills/eli
cp SKILL.md ~/.claude/skills/eli/SKILL.md
```

Restart Claude Code. `/eli` will appear in your skill list.

## Usage

```
/eli [age] [concept]
/eli5 [concept]
/eli-expert [concept]
/eli phd [concept]
```

## Examples

**`/eli5 wifi`**
> Magic invisible air letters. Router = mailbox in house. Phone ask mailbox for video, mailbox send back through air, video play.

**`/eli 12 gravity`**
> Gravity is like the Earth giving everything a big invisible hug that pulls it down. Drop a ball — that's Earth hugging it toward the ground. The bigger something is, the stronger its hug.

**`/eli 18 database indexing`**
> An index is like a book's table of contents. Without it, the database reads every row to find your data (slow). With it, it jumps straight to the right page. Trade-off: indexes speed up reads but slow down writes since the index must also be updated.

**`/eli expert query optimization`**
> Start with EXPLAIN ANALYZE. Look for seq scans on large tables — add indexes on high-cardinality filter columns. Watch for nested loop joins on unindexed FK columns; a hash join is usually faster past ~10k rows. Avoid functions on indexed columns in WHERE clauses — they prevent index use.

**`/eli phd transformer attention`**
> Scaled dot-product attention: softmax(QKᵀ/√dₖ)V. The √dₖ scaling prevents softmax saturation in high dimensions. Multi-head splits the representation space so different heads can attend to different positional/semantic relationships simultaneously. Key insight from Vaswani et al.: attention is just a differentiable dictionary lookup.

**`/eli 8 gravity AND momentum`**
> **Gravity:** Earth is like a giant magnet for everything. It pulls your feet to the floor so you don't float away like a balloon.
>
> **Momentum:** When your bike is going fast, it wants to keep going fast. That's momentum — moving things want to keep moving.

## Supported formats

| Format | Behavior |
|--------|----------|
| `/eli5 [concept]` | Age 5 |
| `/eli-expert [concept]` | Expert/peer level |
| `/eli [number] [concept]` | Exact age |
| `/eli expert [concept]` | Expert mode |
| `/eli phd [concept]` | PhD/specialist mode |
| `/eli [concept]` (no age) | Defaults to age 18 |
| `/eli` (no concept) | Asks what to explain |
| Multiple concepts with AND | Explains each in sequence |

## Age levels

| Range | Style |
|-------|-------|
| 1–4 | Single sentences, physical analogies only |
| 5–8 | Toy/food/game analogies, zero jargon |
| 9–12 | School subject analogies, simple vocab |
| 13–17 | Some technical terms, always explained |
| 18–22 | Educated non-expert, basic science literacy |
| 23+ | College-level knowledge assumed |
| expert/phd | Field terminology, skip fundamentals |
