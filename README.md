# ACID AI

ACID AI is a local AI platform focused on cybersecurity analysis,
decision-making, and controlled security automation.

The project is designed to run locally, using open-source AI models,
Docker, and NVIDIA GPU acceleration.

The goal is not to build only a conversational chatbot, but an AI system
capable of analyzing security problems, reasoning about possible actions,
using security tools, and interpreting their results.

## Goal

The goal of ACID AI is to build a local cybersecurity-focused AI platform
capable of:

- Answering cybersecurity questions
- Analyzing security problems
- Making decisions based on available information
- Using security tools in a controlled environment
- Interpreting tool results
- Maintaining context and security findings
- Retrieving information from cybersecurity knowledge bases
- Operating inside isolated security labs

The project is designed with a local-first approach, keeping models,
processing, conversations, and project data under the user's control.

## Technologies

- Fedora Linux
- Docker
- Docker Compose
- Ollama
- NVIDIA GPU
- Python
- Git / GitHub

## Core Components

### AI Core

The AI core is responsible for running the language model locally.

Initial model:

- Dolphin3-Cyber 8B

The model will be evaluated based on:

- Cybersecurity knowledge
- Reasoning quality
- Tool-use capabilities
- Response quality
- Local inference performance
- GPU utilization

The model layer will remain replaceable so different models can be
tested without redesigning the entire system.

### Agent

The agent layer is responsible for turning the language model into a
decision-making system.

Instead of simply generating a response, the agent should be able to:

1. Understand the user's request
2. Analyze the available context
3. Decide whether a tool is necessary
4. Select an appropriate tool
5. Execute the tool through a controlled interface
6. Analyze the result
7. Decide whether additional actions are necessary
8. Produce a final response

Conceptually:

```
User
 │
 ▼
Agent
 │
 ▼
Decision
 │
 ▼
Tool Manager
 │
 ▼
Tool
 │
 ▼
Result
 │
 └──────────────► Agent
```

## Security Tools

The agent will eventually be able to interact with security tools through
controlled interfaces.

Initial tools:

- Nmap
- HTTP analysis
- ffuf
- Python

Tools will not receive unrestricted access to the host system.

The application will control which tools can be executed, which targets
can be accessed, and which operations are permitted.

## Knowledge

ACID AI will eventually use Retrieval-Augmented Generation (RAG) to
provide additional cybersecurity knowledge to the model.

Potential knowledge sources include:

- OWASP
- MITRE ATT&CK
- Project documentation
- Security research
- Lab documentation

## Memory

The system will maintain different types of information separately.

Planned memory components:

- Conversation history
- Session context
- Security findings
- Long-term memory

Context provided to the model will be controlled by the application rather
than being treated as permanent model memory.

## Security Architecture

Security is a core part of the project.

The model should never receive unrestricted access to the host operating
system.

The application will provide a security layer between the AI model and
external tools.

Planned controls include:

- Tool permissions
- Target allowlists
- Command validation
- Sandboxed execution
- Audit logging
- Isolated security labs

The initial security testing environment will use intentionally vulnerable
applications such as OWASP Juice Shop.

The project is intended for authorized security testing, research,
education, and controlled laboratory environments.

## Architecture

The initial architecture is:

``` 
                         ACID AI
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
           Questions                  Security
              │                           │
              ▼                           ▼
        AI / LLM Core                  Agent
                                          │
                                  ┌───────┴───────┐
                                  │               │
                                  ▼               ▼
                               Tools          Analysis
                                  │
                    ┌─────────────┼─────────────┐
                    │             │             │
                    ▼             ▼             ▼
                   Nmap         HTTP          ffuf
``` 

The infrastructure layer currently consists of:

``` 
                    ┌──────────────┐
                    │   Terminal   │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │ AI Client    │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Ollama    │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │ AI Model     │
                    │ Dolphin3     │
                    │ Cyber 8B     │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │ NVIDIA RTX   │
                    │     4050     │
                    └──────────────┘
``` 

## Project Structure

The following structure represents the planned architecture:

``` 
local-ai/
├── app/
│   ├── main.py
│   ├── client.py
│   └── config.py
│
├── agent/
│   ├── agent.py
│   ├── planner.py
│   └── decision.py
│
├── tools/
│   ├── nmap.py
│   ├── http.py
│   ├── ffuf.py
│   └── python.py
│
├── knowledge/
│   └── README.md
│
├── memory/
│   └── README.md
│
├── tests/
│   ├── unit/
│   └── security/
│
├── labs/
│   └── juice-shop/
│
├── data/
├── models/
├── compose.yml
├── README.md
└── .gitignore
``` 

This structure is a target architecture. Components will be added
incrementally as the project evolves.

## Roadmap

### Infrastructure

- [x] Configure Git
- [x] Configure GitHub SSH
- [x] Configure Docker
- [x] Configure NVIDIA Container Toolkit
- [x] Verify NVIDIA GPU inside Docker

### AI Core

- [ ] Deploy Ollama
- [ ] Deploy Dolphin3-Cyber 8B
- [ ] Verify GPU inference
- [ ] Create terminal interface
- [ ] Evaluate model
- [ ] Compare alternative models

### Agent

- [ ] Define agent architecture
- [ ] Implement decision loop
- [ ] Implement tool interface
- [ ] Implement permission layer
- [ ] Implement tool execution
- [ ] Implement result analysis

### Security Tools

- [ ] Nmap integration
- [ ] HTTP analysis
- [ ] ffuf integration
- [ ] Python execution sandbox

### Security Lab

- [ ] Deploy OWASP Juice Shop
- [ ] Create isolated lab environment
- [ ] Create automated security tests
- [ ] Test reconnaissance
- [ ] Test vulnerability analysis
- [ ] Test agent decision-making

### Knowledge

- [ ] Implement RAG
- [ ] Add OWASP knowledge
- [ ] Add MITRE ATT&CK knowledge
- [ ] Add project documentation

### Memory

- [ ] Conversation history
- [ ] Session context
- [ ] Security findings
- [ ] Long-term memory

### Security

- [ ] Tool permissions
- [ ] Target allowlist
- [ ] Command validation
- [ ] Sandbox execution
- [ ] Audit logging

### Testing

- [ ] Unit tests
- [ ] Agent behavior tests
- [ ] Tool integration tests
- [ ] Security tests
- [ ] Model evaluation

## Privacy

ACID AI follows a local-first architecture.

Conversation history, memory, databases, models, and other local data are
intended to remain on the user's machine and are not committed to the
Git repository.

External services are not required for the core AI infrastructure.

## Status

**Work in progress**

ACID AI is being developed as a cybersecurity, AI, Linux, and software
engineering learning project.

The project also serves as a practical portfolio project focused on
local AI infrastructure, cybersecurity automation, agent architecture,
and secure tool execution.
