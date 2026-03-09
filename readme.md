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

The skill follows a dynamic multi-round interview process:

1. **Analyze the Request** — Identify what's clear and what's ambiguous
2. **Ask Initial Questions** — Start with core clarifications (usually 2-3 questions)
3. **Include Exit Option** — Every question set has "I'm done" or "No more questions"
4. **Process Responses** — Check if user wants to continue or exit
5. **Ask Follow-ups** — If continuing, ask targeted clarification questions
6. **Repeat** — Continue rounds until user selects the exit option
7. **Restate & Proceed** — Summarize requirements and outline the plan

#### 4. Question Types

The skill uses different question formats:

| Type | Use Case | Example |
|------|----------|---------|
| Open-ended | Understand reasoning | "What's the primary goal?" |
| Multiple choice | Fast decisions | "TypeScript or JavaScript?" |
| Yes/No | Binary decisions | "Do you need real-time sync?" |
| Multiple select | List priorities | "Which features are essential?" |
| Exit option | User control | "Any more details to add?" |

### Example Interview Session

**User Request**: "Create a new project"

**Agent Round 1**:
```
I need a few clarifications before setting up:

1. What type of project?
   → Python Script / Python Project / TypeScript / Next.js / Other

2. Any more requirements to clarify?
   → Yes, I have more details
   → No, I'm done answering questions
```

**If user selects "Yes"**, Agent Round 2:
```
3. Which frameworks or tools?
   → [options]

4. Ready to proceed?
   → Yes, I've given enough info
   → No, more questions
```

**If user selects "No more questions"**, Agent Summary:
```
Perfect! Based on your answers, here's what I'll create:
- A [TypeScript] project
- Using [Next.js] framework
- For [personal] use
- With focus on [speed/quality/flexibility]

Ready to proceed?
```

### Key Interview Patterns

The skill includes 11 core interview patterns:

1. **Continuous Interview with Exit Option** — User controls how many rounds; every question set includes an exit
2. **Scope Clarification** — Define must-haves, nice-to-haves, and exclusions
3. **Technology Stack** — Determine tech preferences and constraints
4. **Constraint Discovery** — Uncover deadlines, budgets, team size
5. **Validation & Preference** — Confirm assumptions and gather preferences
6. **Phased Approach** — Break complex work into MVP and future phases
7. **User Experience/UX Focus** — Understand user-facing requirements and design
8. **Technical Requirements** — Gather technical specifications and constraints
9. **Testing and Quality Assurance** — Define testing needs and quality metrics
10. **Deployment and Environment** — Clarify deployment and infrastructure needs
11. **Security and Privacy** — Address security requirements and data handling

See [interview-patterns.md](.github/skills/user-interviewing/references/interview-patterns.md) for detailed patterns.

### Best Practices

✅ **Do**:
- Always include an exit option ("I'm done") in every question set
- Start with 2-3 core questions, then add follow-ups based on responses
- Ask valuable follow-up questions that address specific gaps
- Show understanding by restating key requirements
- Respect user's exit choice and proceed immediately
- Track what you've learned to avoid repeating questions
- Use multiple-choice questions for faster responses

❌ **Don't**:
- Ask leading questions
- Repeat questions across interview rounds
- Ask about obvious details
- Disguise assumptions as questions
- Force more questions if user has selected the exit option
- Ask more than 3-4 questions per round

### Files

- **SKILL.md** — Main skill definition and procedure
- **references/interview-patterns.md** — 5 interview patterns with examples
- **templates/basic-interview.md** — Code templates for structuring questions

### Integration

This skill is available to agents via the `.github/skills/user-interviewing/` directory and integrates with the `vscode_askQuestions` tool for presenting structured interviews to users.

---

**Location**: `.github/skills/user-interviewing/`