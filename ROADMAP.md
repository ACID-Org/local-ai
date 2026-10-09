# ACID-AI — Roadmap

This roadmap describes the planned development of ACID-AI. Tasks are marked as completed only when the corresponding work has been verified.

## Phase 1 — Local Infrastructure

* [x] Configure Git and GitHub SSH authentication
* [x] Configure Docker and Docker Compose
* [x] Configure NVIDIA GPU support for Docker
* [x] Run Ollama in a Docker container
* [x] Download the initial Qwen 3.5 4B model
* [ ] Verify model responses through the local Ollama API

## Phase 2 — Initial Python Application

* [ ] Create the Python project structure
* [ ] Set up a Python virtual environment
* [ ] Implement a basic terminal interface
* [ ] Send messages to the local Ollama API
* [ ] Display model responses in the terminal
* [ ] Handle basic connection and API errors

**Milestone:** Interact with the local model through a Python terminal application.

## Phase 3 — Agent Identity and Context

* [ ] Define ACID-AI's identity and system instructions
* [ ] Establish a consistent response style
* [ ] Maintain conversation context during a session
* [ ] Separate model communication from application logic

## Phase 4 — Task Planning and Human Approval

* [ ] Interpret user requests as tasks
* [ ] Generate clear, step-by-step plans
* [ ] Explain the purpose of each proposed action
* [ ] Allow the user to approve, edit, or reject actions
* [ ] Require fresh approval before each tool execution
* [ ] Validate actions and permissions in application code

## Phase 5 — Controlled Tool Integration

* [ ] Design a restricted tool interface
* [ ] Define allowed operations and target boundaries
* [ ] Implement execution and error handling
* [ ] Return actual tool output to the agent
* [ ] Test tools in an authorized lab environment
* [ ] Prevent unrestricted shell execution by the model

## Phase 6 — Memory and Knowledge

* [ ] Add session history
* [ ] Evaluate persistent conversation storage
* [ ] Implement long-term memory when needed
* [ ] Evaluate retrieval-augmented generation (RAG)
* [ ] Support retrieval from selected local documents

## Phase 7 — Security and Quality

* [ ] Add automated tests
* [ ] Validate user input and tool parameters
* [ ] Protect credentials and sensitive information
* [ ] Review permissions and execution boundaries
* [ ] Document setup, usage, and limitations
* [ ] Test failure cases and unexpected model output

## Development Principles

* Build one small feature at a time.
* Prefer simple, understandable implementations.
* Verify each milestone before marking it complete.
* Keep private data, credentials, and local model files out of Git.
* Never rely on the language model alone to enforce security.
* Require explicit authorization for cybersecurity operations.
* Use only systems and environments the user is authorized to test.

## Current Focus

The immediate priority is Phase 2: building a minimal Python terminal client that communicates with Ollama running locally.

Advanced features will be considered after this initial milestone works reliably.
