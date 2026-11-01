# voice-grill

A voice-first interviewer in the spirit of grill-me / grilling. Talk freely through voice input such as Aqua Voice, and it interviews you with rounds of questions to draw out and sharpen your thinking, then carries on to write the article or plan and execute the work. Works with both Claude Code and Codex.

## How it differs from grill-me / grilling

Matt Pocock's [grill-me / grilling](https://github.com/mattpocock/skills) sharpens your thinking by asking one question at a time. That works well when you type short answers. With voice input you can say a lot at once, so one question per turn means many round trips and gets tiring. voice-grill keeps the same idea but rebuilds it as an interview you answer by talking: it draws you out, lets you talk at length, and takes notes.

| | grill-me / grilling | voice-grill |
|---|---|---|
| Questions per turn | 1 | Up to 5, numbered |
| How you answer | One question at a time | Talk through everything at once, no numbers needed |
| Recommended answers | On every question | Only on decisions. Never on experiences or feelings |
| Spoken language | Not considered | Sorts self-corrections, early answers, and tangents; fixes transcription errors |
| Record | grill-me keeps none. grill-with-docs writes a glossary and ADRs | Interview notes that keep your words, the AI's interpretations, and verified facts apart |
| Ending | Ends when the thinking is sharp | Writes the article, or plans and executes |
| Resuming | No | "Continue" picks up where you left off |

A topic that takes 20 questions means 20 round trips with grill-me, and 4–5 with voice-grill.

## Built for voice

- **Handles self-corrections**: after "no, wait" or "actually", it takes the later answer.
- **Fixes transcription errors**: obvious ones are fixed silently; only proper nouns and numbers are checked, once. Words mis-transcribed repeatedly are suggested for your voice input dictionary at the end.
- **Doesn't lead you**: questions about experiences and feelings carry no recommended answer, so the article ends up in your words, not the AI's.
- **No need to look at the screen**: no tables or long code in replies, just short sentences that make sense when heard aloud.
- **Keeps going when you step away**: permissions for commit, push, publishing, and other decisions are gathered up front in the plan, then it runs to the end.
- **Replies in your language**: the prompts are written in English, but it interviews you in whatever language you speak, and writes the notes and the deliverable in that language too.
- **Notes stay out of git**: interview notes live in `.voice-grill/` and are kept from being committed.

## Flow

1. **Interview**: rounds of questions settle the goal, audience, claim, scope, evidence, and constraints.
2. **Summary**: it shows the key points of the interview notes and checks once that it understood you.
3. **Plan and execute**: for an article, it shows the outline as headings, then writes. Otherwise it writes `plan.md`, carries it through within the agreed scope, and reports back.

## Usage

Just start talking:

```
Interview me. Here's what I'm thinking about... (talk as long as you like)
Interview me and turn it into a blog post
Grill me / drill down / let me think out loud
Continue
```

In Claude Code you can also start with `/voice-grill`. Japanese triggers such as 「掘り下げて」 and 「聞き取って記事にして」 work too.

Tips for answering:

- No need to say question numbers. Talk through everything in whatever order it comes to mind.
- Say "yes to all", "yes except 2", or "skip 3" to accept or skip recommendations.
- Say "wrap up" or "write it" to end the interview at any time.

## Install

### Claude Code (per repository)

```sh
claude plugin marketplace add heyk1njo/voice-grill --scope project
claude plugin install voice-grill@voice-grill -s project
```

Along with the skill, this installs two agents: `researcher`, which looks up facts, and `reviewer`, which checks deliverables against the interview notes.

### Codex

```sh
codex plugin marketplace add heyk1njo/voice-grill
codex plugin add voice-grill@voice-grill
```

Codex plugins are installed into `~/.codex`, so they apply to every repository.

### Skill only, per repository

```sh
npx skills add heyk1njo/voice-grill -a claude-code -a codex
```

This installs the skill without the agents. Without them, voice-grill does the research and the checking itself.

## Files

```
skills/voice-grill/
  SKILL.md                     the interview
  references/notes-template.md interview notes format
  references/plan.md           planning and agreement
  references/run.md            execution and report
  references/write.md          writing articles
agents/
  researcher.md                looks up facts (Claude Code)
  reviewer.md                  checks against the notes (Claude Code)
```

## Credits

The approach of sharpening a design through relentless questions comes from grill-me and grilling in Matt Pocock's [mattpocock/skills](https://github.com/mattpocock/skills) (MIT License).

## License

[MIT](LICENSE)
