# Basic Interview Template

Template for structuring user interviews using `vscode_askQuestions`.

## Continuous Interview Pattern (Recommended)

This pattern allows unlimited questions with user control over when to stop.

```yaml
# First round of questions
questions:
  - header: "coreGoal"
    question: "What's the primary goal of this project?"
    allowFreeformInput: true

  - header: "continueAsking"
    question: "Any additional requirements to clarify?"
    options:
      - label: "Yes, I have more to add"
      - label: "No, I'm done answering questions"
        recommended: true
```

**After user responds**:
- If "Yes, I have more to add":
  ```yaml
  questions:
    - header: "followUp1"
      question: "What else should I know?"
      allowFreeformInput: true

    - header: "continueAsking2"
      question: "Anything else?"
      options:
        - label: "Yes, continue asking"
        - label: "No, I'm done"
          recommended: true
  ```

- If "No, I'm done":
  ```
  Summarize and proceed with implementation:
  "Based on your answers, here's what I understand..."
  ```

---

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
      - label: "Python Package/Project"
      - label: "TypeScript/JavaScript"
      - label: "Next.js Application"
      - label: "Other"

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

  - header: "moreDetails"
    question: "Need to ask more questions?"
    options:
      - label: "Yes, I have more requirements"
      - label: "No, that's all for now"
        recommended: true
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

  - header: "continueQuestions"
    question: "Need to clarify anything else?"
    options:
      - label: "Yes, more details"
      - label: "No, I'm done"
        recommended: true
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

  - header: "moreInfo"
    question: "Need to ask more about the issue?"
    options:
      - label: "Yes, ask follow-ups"
      - label: "No, that's enough"
        recommended: true
```

## Usage Pattern: Multi-Round Interview

The continuous interview pattern allows multiple rounds of questions:

**Round 1**:
```python
vscode_askQuestions({
  "questions": [
    {
      "header": "first_question",
      "question": "Your question here?",
      "options": [...],
      "multiSelect": false,
      "allowFreeformInput": false
    },
    {
      "header": "continue_asking",
      "question": "Ready for follow-up questions?",
      "options": [
        {"label": "Yes"},
        {"label": "No"},
      ]
    }
  ]
})
```

**Round 2** (if user said "Yes"):
```python
vscode_askQuestions({
  "questions": [
    {
      "header": "followup_question",
      "question": "Follow-up based on previous answer?",
      "allowFreeformInput": true,
    },
    {
      "header": "continue_asking2",
      "question": "More questions needed?",
      "options": [
        {"label": "Yes"},
        {"label": "No"},
      ]
    }
  ]
})
```

**Continue** as needed until user selects "No" or an equivalent exit option.

## Processing Responses

### For Each Round:

1. **Check for exit option** — Did the user select "No more questions", "I'm done", or equivalent?
   - If YES → Skip to "Finalize Interview"
   - If NO → Continue to step 2

2. **Extract answers** — Document the key information from responses

3. **Identify gaps** — What follow-up would be most valuable?

4. **Ask next round** — Present the follow-up questions with a new continue/exit option

### Finalize Interview:

1. **Document all responses** — Note all key decisions and preferences
2. **Identify any critical gaps** — Are there essential unknowns?
3. **Restate requirements** — "Based on your answers, here's what I understand..."
4. **Propose next steps** — Outline your action plan
5. **Confirm alignment** — "Does that sound right?"
6. **Proceed** — Move to implementation

## Tips

- **Always include an exit option**: Every question set needs a "No more questions" or "I'm done" option
- **Start simple**: Begin with 1-2 core questions; let user control depth
- **Respect user's exit choice**: If they select the exit option, honor it immediately
- **Ask valuable follow-ups**: Each new round should address a specific gap, not repeat questions
- **Keep introductions brief**: "I have a few clarifications..." 
- **Order by importance**: Ask scope before constraints, core before details
- **Use defaults**: Mark recommended options to guide hesitant users
- **Validate assumptions**: "It sounds like you need X—is that right?"
- **Track what you've learned**: Avoid asking the same thing twice across rounds
