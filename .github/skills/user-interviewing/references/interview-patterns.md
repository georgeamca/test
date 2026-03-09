# Interview Patterns

Common questioning strategies for different scenarios.

## Pattern 0: Continuous Interview with Exit Option

Use for any interview where users should control depth and duration.

**Key feature**: Every question set includes an exit option like "I'm done answering questions" or "No more questions".

**Flow**:
```
Q1: Core requirement with exit option
  → User answers → Continue
  → User selects exit → Summarize & proceed

Q2: Follow-up based on Q1 response with exit option
  → User answers → Continue
  → User selects exit → Summarize & proceed

Q3+: Additional clarifications as needed
```

**Implementation**:
```yaml
questions:
  - header: "requirement1"
    question: "What's the primary goal?"
    allowFreeformInput: true
  
  - header: "continue1"
    question: "Any other details to clarify?"
    options:
      - label: "Yes, I have more details"
      - label: "No, I'm done answering questions"
        recommended: true
```

**After response**:
- If "No, I'm done" → Restate requirements and proceed
- If "Yes" → Ask targeted follow-up questions

---

## Pattern 1: Scope Clarification

Use when request is vague about what should be included.

**Questions**:
1. What's the core feature or requirement? (Open)
2. What are the must-haves vs. nice-to-haves? (Open)
3. Are there any exclusions—things explicitly NOT needed? (Open)
4. What's the priority: breadth (many features) or depth (few features well)? (Choice)

**Example**: User says "Build a chat app"
- Clarify: Single user, 1-to-1 chat, group chat, multiple protocols?
- Clarify: Real-time or polling? Text-only or media?
- Clarify: Persistent history or ephemeral?

## Pattern 2: Technology Stack

Use when implementation approach is unclear.

**Questions**:
1. Do you have existing tech preferences or constraints? (Open)
2. Should we use [Option A] or [Option B]? (Multiple choice)
3. Are there team/company standards we should follow? (Yes/No)
4. Performance/scalability requirements? (Open)

**Example**: User says "Add database"
- Clarify: SQL or NoSQL?
- Clarify: Local development vs. cloud services?
- Clarify: Migration from existing system?

## Pattern 3: Constraint Discovery

Use when request might have hidden constraints.

**Questions**:
1. Are there deadlines or time constraints? (Open)
2. Budget or cost limitations? (Open)
3. Team size/skill level available? (Open)
4. Existing systems we need to integrate with? (Open)

## Pattern 4: Validation & Preference

Use when you've made assumptions and need to confirm.

**Questions**:
1. I'm thinking about [Approach X]—does that align with your intent? (Yes/No)
2. Would you prefer [Option A] or [Option B]? (Choice)
3. Should we prioritize [X] or [Y]? (Choice)
4. Any other concerns or requirements I missed? (Open)

## Pattern 5: Phased Approach

Use when request is complex and might benefit from MVP thinking.

**Questions**:
1. What's the minimum viable version (MVP) for this? (Open)
2. What features come in phase 2, 3, etc.? (Open)
3. Should we aim for 80% functionality quickly, or 100% comprehensively? (Choice)
4. What's your timeline for each phase? (Open)

## Question Type Guidelines

| Type | Best For | Example |
|------|----------|---------|
| Open-ended | Understanding reasoning, exploring options | "How should we handle X?" |
| Multiple choice | Fast decisions, narrowing scope | "Option A, B, or C?" |
| Yes/No | Quick binary decisions | "Do we need real-time?" |
| Ranked | Priority decisions | "Rank these by importance" |

## Avoid

- Leading questions ("You want TypeScript, right?")
- Too many questions (aim for 3-5)
- Question about obvious details
- Assumptions dressed as questions

## Structure for Success

1. **Lead with the biggest uncertainty** → Scope or approach
2. **Follow with constraints** → Time, budget, team
3. **End with validation** → Restate and confirm alignment
