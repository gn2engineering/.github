# Python Style Guide

## Language & Version
- Always target Python 3.12 when writing Python code.
- Do not use deprecated APIs.

## Type Hinting
- All methods and functions must be type-hinted (parameters and return types).
- Prefer built-in generic types where possible (e.g., list[str], dict[str, int], tuple[int, int]).
- Use the typing module when necessary for advanced types that do not have built-in equivalents (e.g., Callable, Protocol, TypeVar, Literal).

## Documentation
- At the top of each generated Python file, include a 2–4 sentence introductory comment describing:
  - What the file contains,
  - What it is responsible for,
  - Any important constraints or assumptions.
- Every class, method, and function must contain a Python docstring in Google format.
- When generating any type of documentation in Markdown format, never include emojis or emoticons.

## Code Architecture Principles
- Adhere to KISS (Keep It Simple, Stupid): prefer the simplest solution that correctly solves the problem.
- Adhere to DRY (Don't Repeat Yourself): factor out repeated logic into reusable functions or methods.
- Adhere to YAGNI (You Ain't Gonna Need It): do not add functionality beyond what is explicitly required.
- Adhere to Separation of Concerns (SoC).
- Adhere to the Single Responsibility Principle (SRP).
- Prefer clarity over cleverness.
- Prefer small, focused, modular helper functions.
- Keep I/O at the edges: isolate filesystem, network, UI, and CLI interactions from core logic where practical.
- Avoid nested functions.

## File Organization
- As a general rule, each significant public class should be in its own file.
- Small, tightly-coupled helper classes or custom exceptions may be included in the same file as the primary class that uses them if doing so improves readability and cohesion.
- File naming: ClassName should be in class_name.py (snake_case filename).
- Separate the main() function and its helper functions into their own file where practical.
- The main file should import any classes and modules that are needed.
- Always place import statements at the top of the file.

## Entry Points and Executable Scripts
- Executable Python modules must define a main() entry point.
- Use the standard execution guard:
  - if __name__ == "__main__": raise SystemExit(main())
- Prefer returning an int exit code from main().

## Comments
- Comments should be used sparingly.
- Beyond the required 2–4 sentence file header comment, add comments only when the "why" is non-obvious (e.g., tricky edge cases, non-trivial regex patterns, domain constraints).
- Prefer expressive naming and clear structure over explanatory comments.

## String Processing
- Prefer simple string methods such as .split(), .startswith(), and .strip() for simple manipulations.
- Avoid regular expressions for tasks that can be handled clearly by simple string methods.
- Use the re module for complex pattern matching only when necessary.
- When using regex, include a short comment explaining the pattern to ensure maintainability.

## Object-Oriented Design
- Prefer composition over inheritance as a general design principle.
- When a formal interface is required:
  - Use typing.Protocol for structural typing (duck typing), or
  - Use abc.ABC for nominal typing.
- Choose the simplest and most appropriate tool for the task.

## Command Line Interface
- When creating CLI Python programs, use the argparse module.

## Development Process / Clarification Rules
- IMPORTANT: Ask questions about anything uncertain or needing clarification before writing code.
- Clarify requirements upfront, including:
  - expected inputs/outputs,
  - error handling needs,
  - performance constraints (if relevant),
  - architectural decisions (module boundaries, public APIs, file layout).
- If multiple implementations are possible, present the simplest viable option first and explain key trade-offs briefly.

## Work Summary Expectations
- When summarizing completed work, include:
  - a brief description of what changed and why,
  - any assumptions made,
  - recommended file reading/study order using a "foundation-first, complexity-last" approach.
