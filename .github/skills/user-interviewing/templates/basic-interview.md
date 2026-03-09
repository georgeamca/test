# Basic Interview Template

Template for structuring user interviews using `vscode_askQuestions`.

## Example 1: Project Type Selection

```yaml
---
title: "Project Initialization"
---

When initializing a new project, ask:

questions:
  - header: "projectType"
    question: "What type of project are you building?"
    options:
      - label: "Python Script"
        recommended: false
      - label: "Python Package/Project"
        recommended: false
      - label: "TypeScript/JavaScript"
        recommended: false
      - label: "Next.js Application"
        recommended: false
      - label: "Other"
        recommended: false

  - header: "frameworks"
    question: "Which frameworks or libraries do you want?"
    multiSelect: true
    options:
      - label: "React"
      - label: "Vue"
      - label: "Angular"
      - label: "Svelte"
      - label: "None"
        recommended: true

  - header: "additionalContext"
    question: "Any other requirements or preferences?"
    allowFreeformInput: true
```

## Example 2: Feature Specification

```yaml
questions:
  - header: "coreGoal"
    question: "What's the primary goal of this feature?"
    allowFreeformInput: true

  - header: "scope"
    question: "Which features are essential?"
    multiSelect: true
    options:
      - label: "User authentication"
      - label: "Real-time data sync"
      - label: "Offline support"
      - label: "Export/Import"

  - header: "priority"
    question: "What's your priority?"
    options:
      - label: "Speed (ship quickly, iterate later)"
        recommended: true
      - label: "Quality (comprehensive, well-tested)"
      - label: "Flexibility (easy to extend)"

  - header: "timeline"
    question: "When do you need this?"
    allowFreeformInput: true
```

## Example 3: Bug/Issue Diagnosis

```yaml
questions:
  - header: "symptom"
    question: "What's happening (what do you see)?"
    allowFreeformInput: true

  - header: "expected"
    question: "What should happen instead?"
    allowFreeformInput: true

  - header: "frequency"
    question: "How often does this occur?"
    options:
      - label: "Always"
      - label: "Sometimes (intermittent)"
      - label: "Once (one-time)"

  - header: "context"
    question: "When did this start?"
    allowFreeformInput: true
```

## Usage Pattern

After you've formulated your interview questions, invoke the tool:

```python
vscode_askQuestions({
  "questions": [
    {
      "header": "first_question_id",
      "question": "Your question here?",
      "options": [...],
      "multiSelect": false,
      "allowFreeformInput": false
    },
    # ... more questions
  ]
})
```

## Processing Responses

After receiving answers:

1. **Document the responses**—note the key decisions
2. **Identify gaps**—anything still unclear?
3. **Restate requirements**—"Based on your answers, here's what I'll build..."
4. **Propose next steps**—outline your action plan
5. **Confirm alignment**—"Does that sound right?"

## Tips

- **Keep introductions brief**: "I have a few quick questions to clarify..."
- **Order by importance**: Ask scope before constraints
- **Use defaults**: Mark recommended options to guide hesitant users
- **Validate assumptions**: "It sounds like you need X—is that right?"
- **Know when to stop**: Once clarified, move to action immediately
