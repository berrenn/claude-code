---
allowed-tools: Bash(gh issue view:*), Bash(gh search:*), Bash(gh issue list:*)
description: Guided feature development based on vetted implementation plans
argument-hint: Feature description in a Github issue and the implementation plan of the current implementation stage in a sub-issue
---

# Feature Development

You are helping a developer implement a new feature stage by stage. You are given a feature description in a Github issue and an implementation plan of the current stage in a  sub-issue. Follow a systematic approach: understand the codebase deeply, understand the feature description, understand the current stage implementation plan, then implement the stage strictly according to the implementation plan.

## Core Principles

- **Ask clarifying questions if needed**: The implementation plan is detailed, authoritative, and you must comply with it. However, if you identify any ambiguities, edge cases, and underspecified behaviors then ask specific, concrete questions rather than making assumptions. Wait for user answers before proceeding with implementation. Ask questions early (after understanding the codebase, feature description, and implementation plan, before implementation).
- **Understand before acting**: Read and comprehend existing code patterns first
- **Simple and elegant**: Prioritize readable, maintainable, architecturally sound code
- **Use TodoWrite**: Track all progress throughout

---

## Phase 1: Clarifying Questions

**Goal**: Fill in gaps and resolve all ambiguities before designing

**CRITICAL**: This is important. DO NOT SKIP.

**Actions**:
1. Create todo list with all steps
1. Review original feature request, implementation plan, and source code files mentioned in the implementation plan
3. Identify underspecified aspects: edge cases, error handling, integration points, scope boundaries, design preferences, backward compatibility, performance needs
3. **Present all questions to the user in a clear, organized list**
4. **Wait for answers before proceeding to implementation**

If the user says "whatever you think is best", provide your recommendation and get explicit confirmation.

## Phase 2: Implementation

**Goal**: Build the current stage of the feature

**DO NOT START WITHOUT USER APPROVAL**

**Actions**:
1. Wait for explicit user approval
2. Read all relevant files identified in the previous phase
3. Implement following the implementation plan
4. Follow codebase conventions strictly
5. Write clean, well-documented code
6. Update todos as you progress

---

## Phase 3: Quality Review

**Goal**: Ensure code is simple, DRY, elegant, easy to read, and functionally correct

**Actions**:
1. Launch 3 code-reviewer agents in parallel with different focuses: simplicity/DRY/elegance, bugs/functional correctness, project conventions/abstractions
2. Consolidate findings and identify highest severity issues that you recommend fixing
3. **Present findings to user and ask what they want to do** (fix now, fix later, or proceed as-is)
4. Address issues based on user decision

---

## Phase 4: Summary

**Goal**: Document what was accomplished

**Actions**:
1. Mark all todos complete
2. Summarize:
   - What was built
   - Key decisions made
   - Files modified
   - Suggested next steps

---