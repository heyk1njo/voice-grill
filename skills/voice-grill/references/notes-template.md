# Interview notes template

Save as `.voice-grill/<YYYY-MM-DD>-<slug>/notes.md`. `<slug>` is the topic in a few lowercase English words joined by hyphens.

The top half (One line through Open questions) is the summary you show at the end of the interview. Rewrite it every round so it can be shown as is at any time. The bottom half is where the raw material goes.

Write the notes in the user's language, including the section headings and status values. Keep the sections in this order so the reviewer and later sessions can find them.

```markdown
# <Topic>

- Started: YYYY-MM-DD
- Producing: <article / plan / decision / implementation …>
- Status: interviewing / summary agreed / plan agreed / running / done

## One line
<The current conclusion in 1–2 sentences>

## Decided
- <decision> (Q3, Q7)

## Assumptions
- <Your interpretations and assumptions. Move to "Decided" once the user confirms> (AI)

## Out of scope
- <What is left out, topics not to write about> (Q9)

## Open questions
- <question not yet decided> (needs: <what must be decided before it can be asked>)

---

## In their own words (verbatim)
- "…" (Q0)

## History and examples
- YYYY-MM: <event> (Q5)

## Verified facts
- <fact> (source: <URL or file:line>, checked YYYY-MM-DD)

## Parked (tangents)
- <topic that may be picked up later> (Q4)

## Glossary (mis-transcription → correct word)
- grill knee → grill-me (confirmed in Q1)
- conversation pan → ? (unconfirmed)

## Log
### R1
- Q1 <question> → <summary of the answer>
- Q2 <question> → <summary of the answer>
```

## How to write it

- Always keep the source: the Q number for the user's words (the first message is Q0), "(AI)" for your interpretations, and the source and check date for verified facts.
- In "In their own words", fix only transcription errors. Don't change words or word order. This is material for the article.
- When an answer changes, delete the old answer and write the new one. If how it changed matters, record that under "History and examples".
