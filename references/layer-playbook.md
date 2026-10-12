# Layer Playbook

How to coach each layer for a non-technical person. For each layer you get: what it is in plain words, an analogy, the questions to ask them, the artifact you build for them, the done-check, and the common mistake to steer them off.

Always tailor the artifact to **their goal** from `memory.md`. Build the file/folder for them, then explain it in one short paragraph.

---

## 1. Identity - the soul

**Plain words:** A short note that tells the OS who it is, who it helps, and what it must never do. Everything else follows from this.

**Analogy:** The job description and personality you would give a brand-new assistant on day one.

**Ask them (pick 2-3):**
- In one sentence, what is this OS for?
- Who does it serve: just you, your team, or your clients?
- What is one thing it should always do, and one thing it should never do?

**You build:** `CLAUDE.md` in this folder. Keep it lean (aim for under 30 lines). Include: who it is, who it serves, the goal, 2-3 defaults (how it should behave), and 2-3 hard refusals. Write it in their voice, grounded in their answers.

**Make it portable (2026 update).** The same identity should serve any agent, not just one tool. Offer to add a short `AGENTS.md` (read by Codex and other agents) that says the same thing or points to `CLAUDE.md`, so the "brain" lives in the folder, not in one product. Also add two tiny sections at the end of `CLAUDE.md`: `## Self-learning` ("when I correct you, add the lesson as a one-line rule under Lessons before continuing") and an empty `## Lessons`. Corrections then become rules instead of repeated mistakes.

**Done-check:** A stranger could read `CLAUDE.md` and correctly describe what this OS is for and one thing it will refuse to do. Bonus for `solid`: a second agent (e.g. Codex reading `AGENTS.md`) would get the same picture, and `## Lessons` exists.

**Common mistake:** Making it long and generic. Cut until it hurts. A bloated identity confuses the OS.

---

## 2. Substrate / Context - the back of house

**Plain words:** All the real knowledge the OS runs on, gathered in one place and trimmed down so it is easy to use. This is the biggest layer and the one most people skip.

**Analogy:** You cannot cook a great meal in a kitchen full of spoiled food and unlabelled jars. Clean the back of house first.

**Ask them (pick 2-3):**
- What sources hold the knowledge this OS needs (documents, past work, websites, experts you trust)?
- If you could ask this OS one hard question and get a great answer, what would it be? (This tells us what to gather.)
- Is any of this private or sensitive? (So we keep it out of anything shared.)

**You build:** a `substrate/` folder and a plan to fill it. Use these canonical paths (so audits can find them):
- `substrate/sources.md` listing where the raw material will come from,
- `substrate/compendium.md` (the distilled reference the OS will actually read),
- if useful, `substrate/subject-matter-expertise/` with one subfolder per source.
Offer to actually harvest and distill if they have the material ready. Note in `memory.md` what still needs gathering.

**De-identify what they flagged.** If they named any field as sensitive (often the very names or amounts you are tempted to write into the tracker), do not write those values into `substrate/`, `memory.md`, or anywhere else in the folder. Use a stable non-identifying handle instead (initials, "Couple A", "Client 1") and keep the real-value mapping out of the folder. Never write a sensitivity note that says a field is excluded and then list that field anyway, that contradiction is itself a leak. If a handle would make the OS unusable for them, ask before writing real values rather than deciding for them.

**Done-check:** `substrate/compendium.md` exists, is organized rather than a pile, and can answer **every part** of the hard question above with the data actually on hand. If the question has more than one part (for example "what is due soon AND what am I already late on") and a required input is still missing, the layer is `in progress`, not `solid`. Say plainly which part it cannot yet answer and what input would fix it.

**Portable working context (2026 update).** Besides the knowledge, the OS needs to remember *where the work stands* between sessions and between agents. Offer the small set any agent can read before acting: `context/current-state.md` (what is true right now), `tasks/current.md` (what is being done) and `handoffs/latest.md` (the note left at the end of the last session, with a dated copy in `handoffs/history/` that is never overwritten). Explain the rhythm in plain words: read these first when you sit down, write the handoff before you leave or before the conversation gets too long.

**Common mistake:** Trying to dump everything in raw. Distill. A small, clean compendium beats a giant messy one.

---

## 3. Rules & Hooks - the guardrails

**Plain words:** The black-and-white lines the OS must never cross, plus a few automatic reflexes that enforce them without anyone remembering to.

**Analogy:** A rule is a sign that says "do not enter". A hook is a locked door that physically cannot open. Hooks are stronger.

**Ask them (pick 2-3):**
- What is the worst mistake this OS could make? (That becomes a hard rule.)
- Is there anything that should happen automatically every time (a reminder, a check, a backup)?
- Any private data that must never leave this folder or get shared?

**You build:** a `rules/` folder with `always.md` (constraints it must follow) and `never.md` (hard stops), written from their answers. If they named an automatic behavior, note it as a hook to add later and describe what it would guard. If they have private data, add a "never commit or share" rule.

**Fences that learn (2026 update).** Two more pieces, both tiny:
- **Permission levels.** For each kind of action, write how free the OS is: N0 only talks · N1 prepares, the human executes · N2 executes after asking, every time · N3 executes alone and reports · N4 executes alone, silently. Most beginners want reading at N4 and anything that sends, pays or deletes at N1 or N2.
- **A failure log.** `FALHAS.md` (or `failures.md`): one line per real failure, `date | what broke | smallest fix | prompt or infra`. After about ten lines the pattern is obvious and the worst ones graduate into `never.md` or a hook. Add "an existing key or password is not permission to use a paid service" when money is involved.

**Done-check:** The worst-mistake answer is written as a clear never-rule, and at least one automatic reflex is identified. For `solid`: the risky actions have a permission level, and a failure log exists.

**Common mistake:** Vague rules ("be careful"). Make them concrete and testable ("never blend two clients' numbers").

---

## 4. Skills - the earned verbs

**Plain words:** The repeatable jobs this OS does, written down so they happen the same way every time. You earn a skill by doing the job by hand a few times first, then capturing the steps.

**Analogy:** A recipe card. The first few times you cook by feel, then you write the recipe so anyone can repeat it.

**Ask them (pick 2-3):**
- What is a task you find yourself repeating that you wish ran the same way every time?
- Walk me through how you do it by hand, step by step.
- How do you know when it is done well?

**You build:** a `skills/` folder, and one subfolder per skill with a simple `SKILL.md` capturing: when to use it, the steps, and what good looks like. Start with ONE skill, their most-repeated job. Tell them a skill is never finished; they will keep improving it.

**Done-check:** One real, repeated job is written as a skill with clear steps and a "what good looks like" line.

**Keep the shelf clean (2026 update).** Every skill needs a clear trigger in its description. If two skills would answer the same request, make one of them run only when called by name. Skills nobody uses move to a reserve folder instead of cluttering the list. If they also use Codex, the skill can live in one source and be linked into both places.

**Common mistake:** Trying to write ten skills at once, or writing a skill for something they have never actually done by hand. Earn it first.

---

## 5. Tools / Connections - the wires out

**Plain words:** How the OS safely reaches real data sources (a bank, a calendar, a spreadsheet, a website). Read-only by default, with nothing secret stored in the folder.

**Analogy:** A window the OS can look through, not a key to the whole house. It can read, but it cannot rummage.

**Ask them (pick 2-3):**
- What outside sources does this OS need to read from to hit your goal?
- For each one, does it only need to look (read), or also to change things (write)?
- Are there secrets involved (passwords, keys)? (Those never go in this folder.)

**You build:** a `tools.md` that lists each connection, what it is for, and read-only versus write, plus a one-line "how to wire it later" note. For each source, help them decide the simplest path: a ready-made skill, a small command-line wrapper, or an existing connector. Keep all secrets out of the folder.

**Done-check:** Every source the goal needs is listed with its access level, and no secrets live in the folder.

**2026 update.** Put the permission level (N0–N4, see Rules) next to each line of `tools.md`. Prefer connections that run on the subscription they already pay for over new paid APIs. If several tools or bots pick an AI model, keep the model name in ONE config file and change it there, never inside each tool.

**Common mistake:** Wiring write-access everywhere. Default to read-only. Add write only where it is truly needed.

---

## 6. Agents - roles with judgment

**Plain words:** A skill is a single verb. An agent is a worker with a role who decides which skills to use and in what order, then runs a check before anything goes out.

**Analogy:** Skills are kitchen tools. An agent is the chef who knows which tool to grab and tastes the dish before it leaves the kitchen.

**Ask them (pick 2-3):**
- Is there a recurring routine where you find yourself stringing several of your skills together by hand?
- What would a trustworthy "manager" of this OS check before letting work go out?
- Should each piece of work be kept separate (for example, one client at a time)?

**You build:** an `agents/` folder with one `AGENT.md` for the first role worth promoting: its job, which skills it orchestrates, and the mandatory review step before output ships. Only create an agent for a routine they actually do by hand today.

**Done-check:** One real orchestrated routine is captured as an agent with a clear review gate.

**2026 update.** When an agent hands work to helpers, it should pick the helper by the job: bulk, mechanical work to a smaller model with closed instructions; decisions stay with the main agent. For anything important, a second reviewer (another agent or another model) attacks the plan before it ships.

**Common mistake:** Building agents before skills exist, or building a "do everything" agent. One agent, one clear role.

---

## Beyond the six layers: long runs (offer only after Agents is solid)

**Plain words:** Letting the OS work for hours on one goal without getting lost.

**Analogy:** Leaving a contractor alone for the day: you agree on what "finished" looks like and how they will prove it, they keep a notebook of where they are, and they call you if they get stuck three times.

**You build (only if asked):** a `longrun/<date>-<slug>/` folder with `goal.md` (one-sentence result + checks written as `command → expected output`, covering it works, nothing else broke, and it did not touch what it should not), `state.md`, `plan.md` and `progress.md`. Stop-and-call-the-human rules: three cycles without measurable progress, repeating "I'll finish and commit" without finishing, or a third context compaction. Full kit: https://inematds.github.io/execucao-longa/guia/

**Done-check:** `goal.md` cannot be satisfied by a shortcut (e.g. "0 failures AND at least N tests AND tests folder untouched", not just "0 failures").

---

## Coaching tips that apply to every layer

- Celebrate each completed layer briefly, then point to the next.
- If they are stuck, give them a concrete example from their own goal, not a textbook one.
- If a layer does not apply to their goal yet, say so honestly and mark it `not started` with a note, rather than inventing work.
- Keep the folder tidy as you go. The folder IS the OS.
