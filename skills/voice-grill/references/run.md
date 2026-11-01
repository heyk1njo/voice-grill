# Run

Carry the agreed `plan.md` through to the end without stopping. The user may have stepped away.

## How to proceed

- Work through the steps from the top and check each one off in `plan.md` as it finishes. Set the notes' status to "running" (in the notes' language).
- When unsure, make an assumption based on what the notes say is decided and assumed, record it under "Assumptions" in `plan.md`, and keep going. Don't stop to ask.
- Perform irreversible operations (push, publish, send, delete, overwrite, anything that costs money, deploying to production) only within what the plan permits. Collect anything not permitted and ask about it at the end.
- When something fails, find the cause and fix it. If it fails at the same point after two fixes, skip that step, record it, and finish the other steps first.
- Put out-of-scope ideas on a "later" list. Don't add them to the plan.

## Verify

- Check each done-when item using the plan's "How to verify". Say so for anything you couldn't verify.
- For writing, designs, and other deliverables where drifting from the notes matters, ask the voice-grill reviewer agent to check them if available (`voice-grill:reviewer` in Claude Code). Otherwise compare them against the notes yourself.

## Report

At the end, report briefly in this order. Avoid tables and long code; use sentences that make sense when heard aloud.

1. Outcome (finished or not, and what was produced)
2. What was done
3. What was verified (and what couldn't be)
4. Assumptions made
5. What remains (operations awaiting permission, skipped steps, the "later" list)
6. Words worth adding to the voice input dictionary (if any)

After reporting, set the notes' status to "done".
