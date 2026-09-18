# Concise Project Communication

A writing standard for coding agents. It applies to agent responses, follow-up messages, and durable
project records such as commit messages, pull request descriptions, design notes, reviews, and
technical summaries. The standard is distributed as a skill for
[Claude Code](https://code.claude.com/docs/en/skills) and
[Codex](https://developers.openai.com/codex/skills).

## Purpose

Coding-agent communication becomes part of the project record. A later reader often has the code
and saved documents without the conversation that produced them. If an agent reports only the
sequence of its work, the reason for a decision is lost even when the implementation remains.

This standard requires the agent to state the objective, the facts and constraints that govern the
decision, the reasoning that connects them, and the result with its accepted tradeoffs. It aims to
leave enough context for another person or agent to assess the work and continue it correctly.

## Requirements

The complete standard is in [`SKILL.md`](SKILL.md). Its principal requirements are:

- Lead with the result, finding, or blocking issue. Include the reasoning needed to assess it instead
  of a chronological account of tool use.
- When an earlier decision constrains the current work, restate the decision, its reason, the
  accepted consequence, and its effect on the present action.
- Explain a specialized concept from its relevant definitions and causal relationships when it
  affects a decision. Assume technical competence without assuming equal familiarity with every
  field.
- Support claims about completion, correctness, compatibility, and performance with evidence.
  Separate observed results from inference.
- Record each material tradeoff as a choice, the reason it was retained, and the consequence that
  follows.
- Use neutral, professional US English. Remove developer slang, canned framing, advisory language,
  celebratory filler, and metaphors where a direct statement is clearer.

The standard covers technical communication and project artifacts. It excludes marketing and casual
correspondence unless requested.

## Installation

### Claude Code

Install the skill for all projects:

```bash
git clone https://github.com/gadient/concise-project-communication.git \
  ~/.claude/skills/concise-project-communication
```

Install it in one repository:

```bash
git clone https://github.com/gadient/concise-project-communication.git \
  .claude/skills/concise-project-communication
```

Claude Code may apply the skill when the current task matches its description. Use
`/concise-project-communication` to invoke it explicitly. Claude Code detects changes to existing
skill directories during a session. If a newly created skills directory does not appear, restart
Claude Code.

### Codex

Install the skill for all projects:

```bash
git clone https://github.com/gadient/concise-project-communication.git \
  ~/.agents/skills/concise-project-communication
```

Install it in one repository:

```bash
git clone https://github.com/gadient/concise-project-communication.git \
  .agents/skills/concise-project-communication
```

Codex may apply the skill when the current task matches its description. Type
`$concise-project-communication` in a prompt to invoke it explicitly. Codex detects newly installed
skills automatically; restart Codex if the skill does not appear.

## Controlled experiment

A controlled experiment compared two independent runs of the same software build task by the same
coding agent. The task specification was AI generated for the evaluation and described LoadMatch, a
fictitious freight-dispatch product. The specification, working environment, and required artifacts
were held constant. The baseline run received the task specification alone. The second run received
the same specification and this standard as a standing instruction. Both runs produced working code,
passing tests, and the same six types of written artifact. The evaluation covered 12 artifacts and 2
agent responses, totaling 13,487 words.

| Measure | Specification only | Specification and standard |
|---|---:|---:|
| Prohibited wording | 8 instances in 6,208 words | 0 instances in 7,279 words |
| Mean score across 11 dimensions, each scored from 0 to 4 | 3.18 | 3.91 |

Six dimensions improved. Explanation from first principles, tradeoff recording, analytical
structure, and treatment of uncertainty increased from 3 to 4. Audience calibration and wording
increased from 2 to 4. Five dimensions did not change: decision history, evidence and verification,
process narration, and artifact hygiene scored 4 in both runs; result-first structure scored 3 in
both.

The standard was the only deliberate difference between the two runs, and the configured run
conformed more closely to the scoring rubric. The experiment contains one pair of runs, however, so
it does not estimate normal variation between repeated runs. The agents also produced different
implementations from the same specification, which means the evaluated prose did not describe
identical outputs. In addition, the baseline agent inherited general instructions to use plain,
direct English. The result provides evidence for this task and agent configuration; it does not
estimate the standard's expected effect across tasks, agents, or repeated runs.

The evaluation harness, rubric, and run outputs are not published.

## License

Apache License 2.0. See [`LICENSE`](LICENSE).
