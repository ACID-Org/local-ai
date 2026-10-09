# ACID-AI

ACID-AI is a local-first AI agent project focused on cybersecurity, developed gradually around a locally hosted language model.

The project is also a personal learning journey focused on Python, Linux, AI infrastructure, software development, and cybersecurity.

## Vision

The goal is to develop an assistant that can understand cybersecurity tasks, prepare plans, explain proposed actions, request human approval, use authorized security tools, and analyze the results.

ACID-AI will use an existing language model rather than training a model from scratch. The application surrounding the model will provide its identity, instructions, workflow, tool integrations, and safety controls.

## Technologies

* Fedora Linux with GNOME
* Docker and Docker Compose
* Ollama for local model inference
* Qwen 3.5 4B as the initial model
* NVIDIA GPU acceleration
* Python
* Git and GitHub

## Current Status

The local infrastructure has been prepared:

* [x] Configure Git and GitHub SSH authentication
* [x] Configure Docker and Docker Compose
* [x] Configure NVIDIA GPU support for Docker
* [x] Run Ollama in a container
* [x] Download the Qwen 3.5 4B model
* [ ] Build the initial Python terminal client
* [ ] Define ACID-AI's identity and system instructions
* [ ] Implement conversation context
* [ ] Add task planning
* [ ] Implement human approval for proposed actions
* [ ] Integrate controlled cybersecurity tools
* [ ] Test in an authorized lab environment
* [ ] Add persistent memory and knowledge retrieval
* [ ] Expand automated tests and security controls

See [ROADMAP.md](ROADMAP.md) for the development plan.

## Planned Workflow

1. The user describes a task.
2. ACID-AI interprets the request and proposes a plan.
3. The application presents the next proposed action and explains its purpose.
4. The user approves, edits, or rejects the action.
5. If approved, the application validates permissions and executes the authorized operation.
6. The model analyzes the actual result.
7. ACID-AI explains the result and proposes the next step.

The application must enforce permissions and execution restrictions itself. Safety must not depend only on instructions given to the language model.

## Architecture

The initial application will be a small Python terminal program that communicates with the local Ollama API.

The planned architecture will evolve gradually:

* **Interface:** receives user input and displays responses.
* **Agent logic:** manages instructions, context, and task planning.
* **Model provider:** communicates with Ollama.
* **Approval layer:** asks the user before executing proposed actions.
* **Tool manager:** validates and dispatches permitted operations.
* **Results and history:** returns tool output to the agent and maintains relevant session context.

These components describe the intended design. Most application components have not been implemented yet.

See [ARCHITECTURE.md](ARCHITECTURE.md) for more details.

## Security Principles

* Require explicit human approval before each tool execution.
* Restrict operations to authorized targets and environments.
* Do not give the language model unrestricted shell access.
* Validate proposed actions in application code.
* Prefer isolated, controlled lab environments for testing.
* Keep secrets, credentials, model data, and private logs out of Git.
* Test behavior before expanding the agent's capabilities.

## Development Approach

The developer has programming experience with C and is learning Python. Development will proceed in small, understandable steps.

The first milestone is deliberately limited: send a message to the local Qwen model through Ollama and display the response in the terminal.

Tool execution, persistent memory, retrieval-augmented generation (RAG), and other advanced capabilities will be introduced only when needed.

See [CONTRIBUTING.md](CONTRIBUTING.md) for development guidelines.

## Privacy

ACID-AI follows a local-first approach. Model inference is intended to run on the user's own machine through Ollama.

Conversation history, local databases, model data, credentials, and other private information should not be committed to the Git repository.

Local execution does not automatically guarantee complete privacy or security: network access, logs, dependencies, and tool permissions must also be considered.

## Project Status

Work in progress. This repository is an evolving personal learning and portfolio project.
