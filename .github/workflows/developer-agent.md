---
on:
  issues:
    types: [labeled]
if: github.event.label.name == 'execute'
permissions:
  issues: read
  contents: read
  pull-requests: read
safe-outputs:
  id-token: write
env:
  # This environment variable tells the gemini engine to use Flash specifically
  GEMINI_MODEL: gemini-3-flash
tools:
  github: null
  repo-memory: null
engine: gemini
---

# Task: Implement Feature from Discussion
You are the Lead Developer. Your goal is to turn the refined issue discussion into a working Pull Request.

## 1. Gather Context
- Read the initial issue description for the core requirements.
- **CRITICAL**: Read every comment in the issue thread to find the "definition of ready" and any decisions made during elaboration.
- If any technical choices (like language or framework) were finalized in the comments, stick to them.

## 2. Execute Implementation
- Use the `github` tool to create a new branch named `feat/ai-build-${{ github.event.issue.number }}`.
- Write the application code, ensuring it follows the architecture discussed in the comments.
- Include a basic test file for the primary functionality.

## 3. Submit Work
- Open a Pull Request back to the `main` branch.
- In the PR description, summarize which parts of the discussion you implemented.
