# Contributing to ACID-AI

## Purpose

ACID-AI is a personal learning and portfolio project focused on local AI, Python, Linux, and cybersecurity.

Development should prioritize understandable code, incremental progress, and security from the beginning.

## Development Principles

* Implement one small feature at a time.
* Prefer simple solutions over unnecessary complexity.
* Keep functions and modules focused on clear responsibilities.
* Explain important design decisions in the documentation.
* Verify that each feature works before moving to the next one.
* Update the documentation when the project's behavior or architecture changes.

## Current Development Priorities

The initial priority is to build a minimal Python terminal client that communicates with the local Ollama API.

The first implementation should:

* Accept a message from the user.
* Send the message to Ollama.
* Display the model's response.
* Handle basic connection and API errors.

Advanced capabilities such as tool execution, persistent memory, and RAG should be introduced only after the initial application works reliably.

## Code Quality

* Use clear and descriptive names.
* Follow standard Python conventions, including PEP 8 where practical.
* Avoid unnecessary dependencies.
* Handle expected errors explicitly.
* Keep configuration separate from application logic.
* Never commit secrets, credentials, or private data.

## Testing

New features should be tested before being considered complete.

Testing should begin with simple manual checks and expand to automated tests as the application grows.

Security-sensitive functionality requires additional testing, including invalid inputs, rejected actions, unexpected model output, and permission boundaries.

## Security Rules

* Never execute a model-generated command without application-level validation and explicit user approval.
* Request fresh approval for every new tool execution.
* Restrict operations to authorized targets and environments.
* Do not provide the model with unrestricted shell access.
* Do not treat user approval as a substitute for validating permissions.
* Use isolated lab environments for cybersecurity testing whenever possible.
* Keep credentials and other sensitive information out of Git.

## Git Workflow

* Make small, focused commits.
* Use commit messages that describe the change.
* Review changes before committing.
* Keep generated files, local model data, secrets, and temporary files out of version control.
* Update related documentation when necessary.

## Documentation

The main project documents are:

* `README.md` — project overview and current status.
* `ROADMAP.md` — development phases and milestones.
* `ARCHITECTURE.md` — planned components and their interactions.
* `CONTRIBUTING.md` — development and security guidelines.

Documentation must distinguish implemented features from planned features.

## Learning Approach

ACID-AI is also a learning project. Implementations should remain understandable to a developer learning Python, even when more advanced solutions are possible.

When introducing a new concept or dependency, prefer a short explanation and a small working example.

## Scope

These guidelines may evolve as the project grows. Simplicity, controlled execution, and verifiable behavior remain the main priorities.
