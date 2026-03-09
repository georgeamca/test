# Skills Documentation

## User Interviewing Skill

### Description

The **user-interviewing** skill helps systematically clarify requirements and ambiguities through structured questioning before implementation. It's designed for agents to gather comprehensive information about user intent, preferences, and constraints.

**Use this skill when**:
- User requests are vague or ambiguous
- Multiple valid interpretations exist
- Gathering project requirements and scope
- Understanding feature specifications
- Handling complex tasks requiring alignment
- Clarifying technical preferences or naming conventions

### How to Use

#### 1. Automatic Loading

The skill is automatically loaded by the agent when it detects:
- Ambiguous requests (e.g., "create a project", "fix the code")
- Multiple possible interpretations of a task
- Unclear scope or requirements

#### 2. Manual Invocation (Slash Command)

Type `/` in the chat and search for "user-interviewing" to manually trigger the skill:

```
/user-interviewing
```

Then describe the task or feature you need clarity on.

#### 3. Interview Structure

The skill follows a standard 5-step interview process:

1. **Analyze the Request** — Identify what's clear and what's ambiguous
2. **Formulate Questions** — Create 3-5 focused questions
3. **Ask Questions** — Present structured questions to the user
4. **Process Responses** — Review answers to understand intent
5. **Restate & Proceed** — Summarize requirements and outline the plan

#### 4. Question Types

The skill uses different question formats:

| Type | Use Case | Example |
|------|----------|---------|
| Open-ended | Understand reasoning | "What's the primary goal?" |
| Multiple choice | Fast decisions | "TypeScript or JavaScript?" |
| Yes/No | Binary decisions | "Do you need real-time sync?" |
| Multiple select | List priorities | "Which features are essential?" |

### Example Interview Session

**User Request**: "Create a new project"

**Agent Interview**:
```
I need a few clarifications before setting up:

1. What type of project?
   → Python Script / Python Project / TypeScript / Next.js / Other

2. Will this be personal or team-based?
   → Personal / Team / Company

3. Any frameworks or tools required?
   → React, Vue, Angular, Svelte, None, or specify

4. What's the primary goal?
   → [Open-ended response]
```

**Agent Summary** (after responses):
```
Based on your answers, here's what I'll create:
- A [TypeScript] project
- Using [Next.js] framework
- For [personal] use
- With focus on [speed/quality/flexibility]

Ready to proceed?
```

### Key Interview Patterns

The skill includes 5 core interview patterns:

1. **Scope Clarification** — Define must-haves, nice-to-haves, and exclusions
2. **Technology Stack** — Determine tech preferences and constraints
3. **Constraint Discovery** — Uncover deadlines, budgets, team size
4. **Validation & Preference** — Confirm assumptions and gather preferences
5. **Phased Approach** — Break complex work into MVP and future phases

See `.github/skills/user-interviewing/references/interview-patterns.md` for detailed patterns.

### Best Practices

✅ **Do**:
- Ask focused questions (3-5 total)
- Use multiple-choice questions for faster responses
- Restate requirements for alignment
- Move forward decisively once clarified
- Avoid unnecessary questions about obvious details

❌ **Don't**:
- Ask leading questions
- Ask too many questions (aim for 3-5)
- Ask about obvious details
- Disguise assumptions as questions
- Continue interviewing after clarity is reached

### Files

- **SKILL.md** — Main skill definition and procedure
- **references/interview-patterns.md** — 5 interview patterns with examples
- **templates/basic-interview.md** — Code templates for structuring questions

### Integration

This skill is available to agents via the `.github/skills/user-interviewing/` directory and integrates with the `vscode_askQuestions` tool for presenting structured interviews to users.

---

**Location**: `.github/skills/user-interviewing/`