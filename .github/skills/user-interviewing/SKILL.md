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

1. **Ask focused questions**: Narrow down scope and intent with 3-5 specific questions
2. **Use the vscode_askQuestions tool**: Provides structured UI for user responses
3. **Infer context**: Don't ask about obvious details; focus on ambiguities
4. **Validate assumptions**: Confirm suspected intent before proceeding
5. **Progress to action**: End interview by restating requirements and proceeding

## Interview Patterns

See [interview-patterns.md](./references/interview-patterns.md) for common questioning strategies and examples.

## Templates

Use [basic-interview.md](./templates/basic-interview.md) as a starting point for your interview questions.

## Procedure

### 1. Analyze the Request
Read the user's request carefully. Identify what's clear and what's ambiguous.

### 2. Formulate Questions
Create 3-5 focused questions that clarify scope, intent, and preferences. Use open-ended questions to understand reasoning, but offer options for faster responses.

**Example questions**:
- What's the primary goal? (open)
- Which of these approaches fits best? (multiple choice)
- Should we prioritize speed or maintainability? (binary choice)
- Do you have existing code to work with? (yes/no)

### 3. Invoke vscode_askQuestions
Use the `vscode_askQuestions` tool to present questions to the user. Structure each question with:
- `header`: Unique identifier (1-2 words)
- `question`: Clear, concise question text
- `options`: Fixed choices (if applicable)
- `multiSelect`: Allow multiple selections (if applicable)
- `allowFreeformInput`: Allow custom answers (if applicable)

### 4. Process Responses
Review the answers to understand:
- What the user actually wants
- Constraints and preferences
- Assumptions to validate
- Next steps to propose

### 5. Restate and Proceed
Summarize the clarified requirements and outline your plan before implementation.

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

- **Be concise**: Users prefer quick interviews. Ask only essential questions.
- **Avoid assumptions**: Don't assume tech stack, naming, or architecture without asking.
- **Offer options**: Multiple-choice questions are faster than open-ended.
- **Show understanding**: Restate key requirements to confirm alignment.
- **Move forward**: Once clarified, act decisively rather than asking more questions.

## When Not to Use

- User provides complete, unambiguous requirements
- Request is a simple, straightforward task with no branching decisions
- User explicitly says "I know what I want" and describes it clearly
