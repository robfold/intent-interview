---
name: intent-interview
description: Find out what the user actually wants before building anything, one multiple-choice question at a time. Use when a request is fuzzy, when the user says "interview me", "ask me first", "figure out what I want", or "we keep talking past each other", or when you keep building the wrong thing. Korean triggers "인터뷰해", "만들기 전에 물어봐", "내 의도부터 파악해", "객관식으로 물어봐". Not for stress-testing a plan that is already clear.
---

# Intent Interview

Close the gap between what the user says and what they actually want. Do not ask them to fill in blanks. Show them **scenes** they can pick from. Propose solutions only after the intent is confirmed.

Two habits cause most wrong builds:

- **Open questions hand the hard part to the user.** Many people cannot answer "what do you want?" but can pick the right picture at once.
- **Recommended answers pull.** When every question comes with "I recommend B", the user accepts B and you hear your own guess back. On a question about intent, a recommendation hides the intent.

## Steps

### 1. Read first

Collect what the user has already answered: the conversation, memory, notes, issues, the codebase. Look up every fact yourself. Never ask the user for something you can find.

Done when: you have a list of **settled** and **unknown** items, and every unknown is something only the user can answer.

### 2. Form a hypothesis

Write in one line what you think the user wants. Add your confidence (0–100%) and the axes that are still missing. There are five axes:

- **Outcome** — what is different when this is done
- **Reason** — why this, and why now
- **Success** — what the user will look at to say it worked
- **Limits** — lines that must not be crossed
- **Out of scope** — what we will not do

### 3. Ask one question

Ask one question per round, then wait for the answer. Pick the question whose answer would change the most other answers. Write it so it makes sense on its own, without the surrounding chat.

Use the harness's structured question tool if it has one (for example, `AskUserQuestion` in Claude Code). If it has none, show numbered options in chat and ask for a number.

Options:

- 2–4 options. Picking one rules out the others.
- Options split different **intents**, not feature names.
- Each option says what changes if the user picks it.
- Use plain words a 16-year-old would understand. Spell out internal code names.
- For rules, policies, or contract terms, write a scene: who does what, and when.
- If an option contains a number, say whether it is measured or estimated.

Whether to recommend depends on the question:

- **About what the user wants:** no recommendation. It pulls the answer and hides the intent.
- **About how to reach an intent that is already confirmed:** if you have evidence, put the recommended option first and mark it.

### 4. Read the answer

Record the answer. Update the hypothesis and the confidence. Choose the next question from the new hypothesis.

- **A correction or "stop":** follow it first. The latest words beat earlier answers.
- **"What do you mean?" or "I don't get it":** the question was at fault. Rewrite it as a simpler scene and ask again under the same ID.
- **"I don't know":** split it into smaller choices. If it is a side branch that does not change the result, mark it open and move on.
- **Nice-sounding words ("something that just works", "scalable"):** switch to a question about something that really happened. For example: the last thing they paid for, or the last thing they gave up on.
- **Two rounds of candidates rejected in a row:** stop producing candidates. First ask for the rule that picks them. For a name, ask for the mood. For a product, ask what impression it should leave, and on whom.
- **"You decide":** write down the range you were given and the value you chose inside it. Do not record it as if the user answered.

### 5. Know when to stop

Stop when you can predict the answers to the next three questions and all five axes are filled. If you pass 8 questions and still cannot predict, something underneath is missing. Go up one level and ask there.

### 6. Read back and confirm

Write the five axes, one line each, in the user's own words. Confirm with a multiple-choice question: "Correct", plus one option for each axis to fix. Fix it and ask again until the user picks "Correct".

### 7. Record and hand off

Write the confirmed result where the next step will read it: the issue, the spec, or a file in the repo. Keep the user's answers, your own judgments, and open items apart. The interview confirms intent. It does not approve execution, deploys, or messages to other people. Those keep their own approval steps.

## Credits

Ideas only; the text is new. The hypothesis, confidence, prediction-based stopping, and read-back come from [addyosmani's `interview-me`](https://github.com/addyosmani/agent-skills/tree/main/skills/interview-me). Asking prerequisite decisions first comes from [mattpocock's `grilling`](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling). The question axes come from [devbrother2024's `deep-interview`](https://github.com/devbrother2024/skills/tree/main/deep-interview). Multiple choice, scenes, plain words, and the recommendation split came from corrections by the person this skill was first built for.
