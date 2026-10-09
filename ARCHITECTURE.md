# ACID-AI — Architecture

## Overview

ACID-AI is a local-first AI agent focused on cybersecurity. It uses an existing language model served locally by Ollama and adds application logic for task planning, human approval, and controlled tool execution.

The project will be developed incrementally. The architecture described here is the intended design, not a claim that all components already exist.

## High-Level Architecture

```
User
 |
 v
Terminal Interface
 |
 v
Agent Logic
 |-- System Instructions
 |-- Conversation Context
 |-- Task Planning
 |
 v
Local Model Provider
 |
 v
Ollama API
 |
 v
Qwen 3.5 4B


Planned Tool Execution:

Agent Logic
 |
 v
Proposed Action
 |
 v
Human Approval
 |
 v
Application Security Checks
 |
 v
Restricted Tool Manager
 |
 v
Authorized Target or Lab
 |
 v
Tool Result
 |
 v
Agent Logic
```

## Main Components

### 1. Terminal Interface

The initial interface will run in the terminal.

Responsibilities:

* Receive user messages.
* Display model responses.
* Present proposed actions and their purposes.
* Ask the user to approve, edit, or reject proposed actions.
* Display execution results and errors.

### 2. Agent Logic

The agent logic coordinates the application workflow.

Responsibilities:

* Apply ACID-AI's system instructions.
* Manage conversation context.
* Interpret user requests.
* Prepare task plans.
* Propose actions when tools are available.
* Analyze model responses and actual tool results.

The agent logic must not be treated as a security boundary by itself.

### 3. Local Model Provider

The model provider handles communication between the Python application and Ollama.

Responsibilities:

* Send prompts and conversation messages to the local API.
* Receive model responses.
* Handle connection failures and API errors.
* Keep model-specific communication separate from the rest of the application.

The initial model is Qwen 3.5 4B.

### 4. Human Approval

Before an action is executed, the application must present it to the user.

The user can approve, edit, or reject the proposed action. Each new tool execution requires a fresh approval.

Approval does not replace security validation. The application must also verify that the action and its target are permitted.

### 5. Security Checks

Security checks are enforced by application code rather than relying only on the model's instructions.

Planned checks include:

* Validate tool parameters.
* Restrict operations to explicitly permitted capabilities.
* Enforce target and environment boundaries.
* Reject unsupported or unauthorized actions.
* Handle errors without bypassing restrictions.

The model will not receive unrestricted shell access.

### 6. Tool Manager

The tool manager will provide a controlled interface to approved cybersecurity tools.

Responsibilities:

* Expose only explicitly registered tools.
* Validate proposed tool inputs.
* Execute permitted operations.
* Capture actual output and errors.
* Return results to the agent for analysis.

Initial testing will use an authorized, controlled lab environment.

### 7. Conversation History and Memory

Conversation context will initially be maintained within a session.

Persistent history, long-term memory, and retrieval-augmented generation (RAG) may be added later if they provide clear benefits.

Sensitive data must be handled carefully and excluded from version control.

## Execution Workflow

1. The user submits a request.
2. The agent interprets the request and prepares a response or plan.
3. If an operation is needed, the agent proposes one action.
4. The interface explains the action and requests approval.
5. The application validates the approved action and its permissions.
6. The tool manager executes the permitted operation.
7. The application returns the actual result to the agent.
8. The agent explains the result and proposes the next step, if necessary.

Every new operation must pass through the approval and validation process again.

## Technology Stack

* **Operating system:** Fedora Linux
* **Containerization:** Docker and Docker Compose
* **Model runtime:** Ollama
* **Initial model:** Qwen 3.5 4B
* **Application language:** Python
* **Version control:** Git and GitHub
* **Hardware acceleration:** NVIDIA GPU

## Development Strategy

The first implementation will be intentionally small: a Python terminal client that sends a message to Ollama and displays the response.

Task planning, tool execution, approval controls, memory, and document retrieval will be added in later stages.

The architecture may evolve as the project is implemented and tested.

## Security Considerations

Local model execution does not automatically guarantee security or privacy.

The project must consider tool permissions, input validation, network exposure, dependency risks, logging, and the protection of credentials and other sensitive information.

Security controls must be enforced by the application and the environment in which tools run.
