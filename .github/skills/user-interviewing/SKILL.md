---
name: user-interviewing
description: 'Systematically interview users to clarify requirements, constraints, and goals. Use when: gathering project requirements, understanding feature scope, validating assumptions, handling ambiguous requests, or collecting preferences before implementation.'
argument-hint: 'Describe the task or feature you need clarity on'
user-invocable: true
---

# User Interviewing Skill

Gather comprehensive requirements and clarify ambiguities through structured questioning. This skill helps agents understand user intent before proceeding with implementation.

## When to Use

- **Ambiguous requests**: User asks for something vague ("create a project", "fix the code")
- **Multiple valid interpretations**: Request could be solved different ways
- **Gathering requirements**: Need to validate scope, priorities, and constraints
- **Feature specifications**: Before building, confirm what's needed
- **Complex tasks**: Multi-step work requiring alignment on approach
- **Clarifying preferences**: Tech stack, naming conventions, patterns

## Core Principles

1. **Ask focused questions**: Start with scope, then gather additional details as needed
2. **Enable user control**: Always offer an "I'm done" or "No more questions" option to exit
3. **Use the vscode_askQuestions tool**: Provides structured UI for user responses
4. **Allow unlimited depth**: Continue asking follow-up questions based on responses
5. **Infer context**: Don't ask about obvious details; focus on ambiguities
6. **Validate assumptions**: Confirm suspected intent before proceeding
7. **Progress to action**: End interview by restating requirements and proceeding

## Interview Patterns

See [interview-patterns.md](./references/interview-patterns.md) for common questioning strategies and examples.

## Templates

Use [basic-interview.md](./templates/basic-interview.md) as a starting point for your interview questions.

## Procedure

### 1. Analyze the Request
Read the user's request carefully. Identify what's clear and what's ambiguous. Determine the most important clarifications needed.

### 2. Formulate Initial Questions
Create 2-3 focused questions that clarify the core intent and scope. Always include an exit option.

**Example questions**:
- What's the primary goal? (open)
- Which of these approaches fits best? (multiple choice)
- Do you have existing code to work with? (yes/no)

### 3. Invoke vscode_askQuestions
Use the `vscode_askQuestions` tool to present questions to the user. **Always include an exit option in every question set**:

Structure each question with:
- `header`: Unique identifier (1-2 words)
- `question`: Clear, concise question text
- `options`: Include "I'm done answering questions" or "No more questions" as the last option
- `multiSelect`: Allow multiple selections (if applicable)
- `allowFreeformInput`: Allow custom answers (if applicable)

### 4. Process Responses
Review the answers to determine:
- Whether the user selected an exit option → Proceed to step 6
- Gaps or ambiguities that need clarification → Continue to step 5
- What follow-up questions would be most valuable

### 5. Ask Follow-up Questions
Based on the responses, formulate additional targeted questions. Options include:
- Deeper dives into specific requirements
- Validation of assumptions
- Constraint discovery (deadlines, budget, team size)
- Technical preferences or priorities

Repeat steps 3-5 as needed. The interview continues until the user selects the exit option or you've gathered sufficient clarity.

### 6. Restate and Proceed
Summarize the clarified requirements and outline your plan before implementation. Ask for final confirmation if needed.

## Example: Vague Request

**Request**: "Create a new workspace"

**Interview Questions**:
```
- What type of project? (TypeScript, Python, etc.)
- Will this be a personal or team project?
- Any specific framework or tools required?
- What's the primary goal of this workspace?
```

**After responses**: Restate the plan and proceed with setup.

## Best Practices

- **Always include an exit option**: Every question set should have "I'm done" or "No more questions" to give users control
- **Start with essentials**: Begin with core scope clarifications, then deeper questions based on responses
- **Ask valuable follow-ups**: Each new question should address a specific gap or assumption
- **Avoid repetition**: Don't ask the same thing twice; track what you've already learned
- **Show understanding**: Restate key requirements regularly to confirm alignment
- **Respect user choice**: If they select the exit option, summarize and proceed immediately
- **Be concise**: Keep questions brief and focused; avoid multiple questions per turn
- **Offer options**: Multiple-choice questions are faster than open-ended when possible

## When Not to Use

- User provides complete, unambiguous requirements
- Request is a simple, straightforward task with no branching decisions
- User explicitly says "I know what I want" and describes it clearly
