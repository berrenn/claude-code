---
allowed-tools: Bash(gh issue view:*), Bash(gh search:*), Bash(gh issue list:*), Bash(gh issue add-sub:*)
description: Guided feature development planning with codebase understanding and architecture focus
argument-hint: Feature description in a Github issue
---

# Feature Development

You are helping a developer produce an implementation plan of a new feature. Feature description is supplied in a Github issue. Follow a systematic approach: understand the codebase deeply, identify and ask about all underspecified details, design elegant architectures, break down implementation into stages, then document.

## Core Principles

- **Ask clarifying questions**: Identify all ambiguities, edge cases, and underspecified behaviors. Ask specific, concrete questions rather than making assumptions. Wait for user answers before proceeding with implementation. Ask questions early (after understanding the codebase, before designing architecture).
- **Understand before acting**: Read and comprehend existing code patterns first
- **Read files identified by agents**: When launching agents, ask them to return lists of the most important files to read. After agents complete, read those files to build detailed context before proceeding.
- **Simple and elegant**: Prioritize readable, maintainable, architecturally sound code
- **Use TodoWrite**: Track all progress throughout

---

## Phase 1: Discovery

**Goal**: Understand what needs to be built

Initial request: $ARGUMENTS

**Actions**:
1. Create todo list with all phases
2. If feature unclear, ask user for:
   - What problem are they solving?
   - What should the feature do?
   - Any constraints or requirements?
3. Summarize understanding and confirm with user

---

## Phase 2: Codebase Exploration

**Goal**: Understand relevant existing code and patterns at both high and low levels

**Actions**:
1. Launch 2-3 code-explorer agents in parallel. Each agent should:
   - Trace through the code comprehensively and focus on getting a comprehensive understanding of abstractions, architecture and flow of control
   - Target a different aspect of the codebase (eg. similar features, high level understanding, architectural understanding, user experience, etc)
   - Include a list of 5-10 key files to read

   **Example agent prompts**:
   - "Find features similar to [feature] and trace through their implementation comprehensively"
   - "Map the architecture and abstractions for [feature area], tracing through the code comprehensively"
   - "Analyze the current implementation of [existing feature/area], tracing through the code comprehensively"
   - "Identify UI patterns, testing approaches, or extension points relevant to [feature]"

2. Once the agents return, please read all files identified by agents to build deep understanding
3. Present comprehensive summary of findings and patterns discovered

---

## Phase 3: Clarifying Questions

**Goal**: Fill in gaps and resolve all ambiguities before designing

**CRITICAL**: This is one of the most important phases. DO NOT SKIP.

**Actions**:
1. Review the codebase findings and original feature request
2. Identify underspecified aspects: edge cases, error handling, integration points, scope boundaries, design preferences, backward compatibility, performance needs
3. **Present all questions to the user in a clear, organized list**
4. **Wait for answers before proceeding to architecture design**

If the user says "whatever you think is best", provide your recommendation and get explicit confirmation.

---

## Phase 4: Architecture Design

**Goal**: Design multiple implementation approaches with different trade-offs

**Actions**:
1. Launch 2 code-architect agents in parallel with different focuses: minimal changes (smallest change, maximum reuse), or clean architecture (maintainability, elegant abstractions). If user explicitely asks to prioritise one of these focuses then only launch 1 code-architect agent with an appropriate focus.
2. Review all approaches and form your opinion on which fits best for this specific task (consider: small fix vs large feature, urgency, complexity, team context)
3. Present to user: brief summary of each approach, trade-offs comparison, **your recommendation with reasoning**, concrete implementation differences
4. **Ask user which approach they prefer**

---

## Phase 5: Implementation Planning

**Goal**: Break implementation into stages and document

**DO NOT START WITHOUT USER APPROVAL**

**Actions**:
1. Wait for explicit user approval
2. Read all relevant files identified in previous phases
3. Based on the chosen architecture, break down the implementation into several stages, scoping each stage so that each is implementable by an AI coding agent in 20 minutes.
4. Document implementation plan for each stage in a new Github sub-issue under the original feature issue.
5. Each stage implementation plan should be self-contained and include topics from the following areas relevant to that stage:
- **Patterns & Conventions to follow**: Existing patterns with file:line references, similar features, key abstractions
- **Architecture Decisions to follow**: Your chosen approach with rationale
- **Relevant Component Design**: Each component with file path, responsibilities, dependencies, and interfaces
- **Implementation Map**: Specific files to create/modify with detailed change descriptions
- **Data Flow**: Data flow from entry points through transformations to outputs as relevant to this stage
- **Build Sequence**: The stage's implementation steps as a checklist
- **Critical Details**: Error handling, state management, testing, performance, and security considerations
6. Create and document ADR creation and update stages (if needed) before implementation stages that depend on them
7. Follow codebase conventions strictly
8. Update todos as you progress

## Phase 6: Summary

**Goal**: Document what was accomplished

**Actions**:
1. Mark all todos complete
2. Summarize:
   - What was planned
   - Key decisions made
   - Sub-issues created
   - Suggested next steps

---
