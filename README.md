# StructuredAgentFlowKit

A structured workflow for guiding AI coding assistants (like Cursor) through complex software development tasks using persistent planning and state management.

## The Problem

Interacting with powerful AI assistants via standard chat can lead to challenges like:

- **Context Loss:** AI forgetting previous instructions or context in long conversations.
- **Lack of Planning:** Diving into implementation without a clear, agreed-upon strategy.
- **Inconsistent Execution:** AI deviating from the intended steps or hallucinating requirements.
- **Difficulty Tracking Progress:** Hard to know what's done and what's next in a complex task.

This kit aims to address these issues by imposing structure and maintaining state.

## The Solution: Plan-Driven, State-Managed Workflow

This repository provides templates and a methodology based on three core components:

1.  **Structured XML Prompts:** Using XML for prompts provides clear delineation of instructions, context, and goals, helping the AI parse requests accurately and reducing ambiguity (see `generate_plan.md` and `workflow_start_prompt.md`).
2.  **Long-Term Memory (LTM) - The Plan:** An `implementation_plan.md` file, generated upfront using `generate_plan.md`, outlines the detailed, step-by-step plan for the task. This file remains **read-only** during execution, serving as the source of truth.
3.  **Short-Term Memory (STM) - The State:** A dynamic `Implementation_state.md` file tracks the current task, overall progress, completed steps, and any errors encountered. This file is **read before and updated after** each step by the AI, maintaining the workflow's state.

## Key Components

- **`generate_plan.md`:** An XML prompt template used to guide the AI in analyzing a task and generating a detailed `implementation_plan.md`.
- **`Implementation_state.md`:** A Markdown template for tracking the live state of the implementation process (the STM).
- **`workflow_start_prompt.md`:** An XML prompt template used to kick off the execution phase. It instructs the AI to use the LTM (`implementation_plan.md`) and STM (`Implementation_state.md`) to execute tasks sequentially and autonomously, updating the STM after each step.
- **`blog.md`:** A detailed article explaining the rationale, workflow, benefits, and considerations of this approach.

## Benefits

- **Consistency & Reliability:** Reduces AI variability and context drift.
- **Improved Context Management:** Explicit LTM/STM system tackles LLM statelessness.
- **Focus & Decomposition:** AI handles one manageable step at a time.
- **Transparency & Control:** Plan review and state tracking provide oversight.
- **Structured Autonomy:** Balances automation with human intervention points (e.g., on errors).

## Getting Started

1.  **Plan:** Use `generate_plan.md` (potentially referencing your task description and relevant code using `@` mentions in Cursor) to generate the `implementation_plan.md`. Review and refine this plan.
2.  **Initialize:** Create your `Implementation_state.md` file based on the template, pointing to the first task from your plan.
3.  **Execute:** Start a new AI conversation (e.g., in Cursor) using the `workflow_start_prompt.md`, referencing your specific `implementation_plan.md` and `Implementation_state.md` files (again, `@` mentions are useful here). Confirm the first step, and the AI should proceed autonomously, updating the state file after each successful task.
