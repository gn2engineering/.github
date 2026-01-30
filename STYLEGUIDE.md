# gn2engineering Python Style Guide

## Purpose

This document defines the authoritative Python coding standards for gn2engineering projects. The goal is to produce code that is:

- Clear and predictable to read
- Easy to test and refactor
- Explicit in intent
- Simple rather than clever

These standards apply to all Python code unless explicitly documented otherwise.

---

## Guiding Principles

- Prefer clarity over cleverness
- Keep code simple, direct, and maintainable
- Optimize for long-term readability, not short-term brevity
- Make intent obvious through structure and naming

---

## Language & Version

- All Python code must target **Python 3.12**.
- Deprecated APIs must not be used.
- Rely on the standard library where practical.

---

## Type Hinting

Type hints are **mandatory**, not optional.

- All functions and methods must specify:
  - Parameter types
  - Return types
- Prefer built-in generics:
  - `list[str]`, `dict[str, int]`, `tuple[int, int]`
- Use `typing` constructs when necessary:
  - `Callable`, `Protocol`, `TypeVar`, `Literal`
- Type hints should improve clarity, not obscure it.

---

## Documentation Standards

### File-Level Documentation (Required)

Every Python file must begin with a **2–4 sentence introductory comment** describing:

- What the file contains
- Its primary responsibility
- Any important assumptions or constraints

This comment exists to orient readers quickly and is considered **documentation**, not inline commentary.

### Docstrings (Required)

- Every public class, function, and method must have a docstring.
- Docstrings must use **Google format**.
- Docstrings should describe:
  - Purpose
  - Parameters
  - Return values
  - Important side effects or constraints

### Markdown Documentation

- When generating Markdown documentation, do not use emojis or emoticons.
- Keep documentation factual and concise.

---

## Comments

- Comments should be **rare and intentional**.
- Avoid comments that restate what the code already expresses.
- Use comments only to explain:
  - Non-obvious logic
  - Domain-specific constraints
  - Complex algorithms
  - Regular expressions

In general:
> If a comment explains *what* the code is doing, reconsider the code.  
> If it explains *why* the code exists or behaves a certain way, it is likely appropriate.

---

## Code Architecture Principles

All code should adhere to the following principles:

- **KISS**: Prefer the simplest solution that works.
- **DRY**: Eliminate duplicated logic via reusable helpers.
- **YAGNI**: Do not add speculative features.
- **Separation of Concerns**: Keep responsibilities clearly separated.
- **Single Responsibility Principle**: Each function, class, or module should do one thing well.

Additional guidance:
- Prefer small, composable helper functions.
- Avoid nested functions.
- Keep side effects localized.
- Keep I/O at the edges of the system.

---

## File Organization

- Each significant public class should live in its own file.
- File naming:
  - `ClassName` → `class_name.py`
- Small helper classes or custom exceptions may live alongside the primary class when cohesion improves.
- Import statements must appear at the top of the file.
- Library code should be import-safe (no side effects on import).

---

## Entry Points and Scripts

- Executable scripts must define a `main()` function.
- Use the standard execution guard:
  - `if __name__ == "__main__": raise SystemExit(main())`
- `main()` should return an integer exit code.
- CLI argument parsing must use `argparse`.

---

## Object-Oriented Design

- Prefer **composition over inheritance**.
- Use inheritance only when it models a true “is-a” relationship.
- When an interface is required:
  - Use `typing.Protocol` for structural typing
  - Use `abc.ABC` for nominal typing
- Choose the simplest construct that expresses the intent.

---

## String Processing

- Prefer simple string methods:
  - `.split()`, `.startswith()`, `.strip()`
- Avoid regular expressions unless they materially improve clarity.
- When regex is used:
  - Add a short comment explaining the pattern.

---

## Development Process Expectations

- Clarify uncertainties before writing code.
- Confirm:
  - Inputs and outputs
  - Error handling behavior
  - Performance expectations (if relevant)
  - File and module boundaries
- When multiple solutions are possible, prefer the simplest viable option.

---

## Work Summaries

When summarizing work (e.g., in PRs or reports), include:

- What was changed and why
- Key assumptions
- Known limitations
- Recommended file reading order, using a **foundation-first, complexity-last** approach
