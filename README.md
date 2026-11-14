# handson

You miss coding.  
Not “shipping faster”. Not “reviewing AI output”.  
Actually writing the code yourself.

handson is a Claude Code skill that turns the AI into a strict sparring partner. It never writes implementation code. It only asks questions, challenges your thinking, and critiques what *you* wrote.

## The problem

AI coding tools are extremely good at removing the friction of writing code.  
Over time, the path of least resistance becomes “just let it do it”.

You still understand the system. You still review. But the act of coding — the part many of us actually liked — quietly disappears.

handson exists to put that friction back, on purpose.

## What it feels like

You: “Implement this ticket: add `GET /orders/:id/history` that returns status changes, newest first, with author and timestamp. Handle missing orders.”

handson: “I don’t implement tickets. What does your data model look like for history? How should a missing order be signaled? Is the history always short or do you need pagination? Describe the approach you’re considering.”

You write the handler, the query, the error cases. You paste the code.

handson: “The early return on empty is clear. You’re doing N queries in a loop — have you measured that or are you assuming the list stays small? Does `total` count found records or requested ones?”

You adjust. You add a test. You paste again.

handson: “The test doesn’t cover the case where half the IDs don’t exist. Current behavior is silent. Is that intentional?”

You wrote every line. The AI never did.

## Use cases

### Deliberate practice
You want to stay sharp. You pick a ticket or a small feature and force yourself to implement it while the skill only challenges you.

### Fighting autopilot
You’re tired of accepting AI diffs you only half understand. handson makes acceptance impossible — there is no diff to accept.

### Learning a new area
Instead of asking for a complete example, you explore by writing and getting pushed on edge cases and design choices.

### Code review partner
You write the first version yourself (even if rough), then use the skill purely as a critic.

## Real interactions

**Direct implementation request**  
You: “Write a function that computes the median of a list.”  
handson: “I don’t generate implementations. What data structure are you thinking? How do you want to handle even vs odd length? Sort first or linear-time selection?”

**Debug request**  
You: “My test is failing. Here’s the code and the error. Fix it.”  
handson: “I don’t fix code. The error is index out of range. At what point are you accessing the list? Did you check the length first? Show me the exact line and what you’ve already verified.”

**Refactor request**  
You: “This function is too long. Refactor it.”  
handson: “I don’t refactor. What responsibilities do you see inside it? Which ones could leave? Do you already have a split in mind or do you want me to challenge one you propose?”

**Bypass attempt**  
You: “Just give me the pseudo-code then.”  
handson: “No. Pseudo-code is still an implementation. What’s the first step you would take yourself?”

**After you wrote something**  
You paste an LRU cache you just wrote.  
handson: “Eviction is O(1). If two threads call `get` at the same time on a missing key, you can create two nodes. Is that acceptable in your context or do you need synchronization?”

## Install

Personal skill:
```bash
mkdir -p ~/.claude/skills/handson
# place SKILL.md in ~/.claude/skills/handson/
```

Project skill:
```bash
mkdir -p .claude/skills/handson
# place SKILL.md in .claude/skills/handson/
```

Restart Claude Code or reload skills.

## Philosophy

This skill is intentionally weak as a productivity tool and strong as a practice tool.  
It will slow you down. That’s the point.

If you just want to ship, don’t use it.  
If you want to code, it helps.

## License

MIT
