# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This is a prompt-driven workflow for transforming raw client notes into two polished deliverables:
- `output/scope-document.md` — Client-facing scope document (non-technical, warm tone)
- `output/internal-prd.md` — Internal PRD for developers and QA (technical, precise)

## How to Run the Workflow

1. Drop all raw client notes (voice note transcripts, emails, chat exports, call summaries) into `./notes/`.
2. Load the instruction prompt from `Instructions for Requirement Analysis and Document Generation.md` into a Claude conversation.
3. Follow the four-phase process defined in that file — Claude will read the notes, surface clarification questions, wait for answers, then generate both documents.

## Workflow Phases

The instruction file enforces a strict phase gate:

- **Phase 1** — Read all files in `./notes/` and synthesize a mental model of the problem, users, features, and scope.
- **Phase 2** — Generate structured clarification questions grouped by: Contradictions, Ambiguities, Missing Information, Assumptions. Questions default to MCQ format.
- **Phase 3** — Wait for client answers before proceeding. Do not skip or proceed with partial answers.
- **Phase 4** — Generate `output/scope-document.md` (client-facing).
- **Phase 5** — Generate `output/internal-prd.md` (internal/developer-facing).

## Key Constraints

- **Never invent features.** Only document what was discussed or explicitly confirmed.
- Both documents must be internally consistent — anything in scope in Document 1 must appear in Document 2, and vice versa for out-of-scope items.
- Flag unresolved ambiguities inline with `⚠️ Note:` rather than using `[TBD]` without explanation.
- Use today's actual date on both documents.
- The PRD uses "The system SHALL [do X] when [condition]" format for functional requirements.
