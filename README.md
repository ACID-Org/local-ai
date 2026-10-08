# 🐦‍🔥 ACID AI 🐦‍🔥 

> **Cybersecurity Intelligence & Automation**

A local AI platform for cybersecurity analysis, decision-making,
and controlled security automation.

---

## About

ACID AI is an open-source cybersecurity AI project developed by ACID.

The project aims to build a local AI system capable of analyzing security
problems, reasoning about possible actions, using security tools, and
interpreting their results.

Unlike a traditional chatbot, ACID AI is designed around an agent
architecture that can make decisions and interact with security tools
through controlled interfaces.

---

## What We Are Building

- Cybersecurity-focused AI
- Security analysis and reconnaissance
- Agent-based decision making
- Controlled security tool execution
- Cybersecurity knowledge and RAG
- Context and persistent memory
- Isolated security laboratories
- Security-first tool permissions

---

## Architecture

```
                              ACID AI
                                 │
                 ┌───────────────┴───────────────┐
                 │                               │
                 ▼                               ▼
              Questions                       Security
                 │                               │
                 ▼                               ▼
            AI / LLM Core                     Agent
                                                 │
                                      ┌──────────┴──────────┐
                                      │                     │
                                      ▼                     ▼
                                   Decision               Tools
                                                            │
                                  ┌─────────────────────────┼─────────┐
                                  │                         │         │
                                  ▼                         ▼         ▼
                                Nmap                      HTTP       ffuf
```
---

## Security Model

Security is a core part of ACID AI.

The AI model should never receive unrestricted access to the host system.
Instead, the application will act as a security layer between the model
and external tools.

```
User
 │
 ▼
ACID AI
 │
 ▼
Agent
 │
 ▼
Permission Layer
 │
 ▼
Tool Manager
 │
 ▼
Security Tool
 │
 ▼
Authorized Target
```

Planned security controls include:

- Tool permissions
- Target allowlists
- Command validation
- Sandboxed execution
- Audit logging
- Isolated security labs

ACID AI is intended for authorized security testing, research, education,
and controlled laboratory environments.

---

## AI Core

The initial model selected for ACID AI is:

**Dolphin3-Cyber 8B**

The model will be evaluated based on:

- Cybersecurity knowledge
- Reasoning quality
- Tool-use capabilities
- Response quality
- Local inference performance
- GPU utilization

The model layer will remain replaceable, allowing different models to be
tested without redesigning the rest of the platform.

---

## Security Tools

ACID AI will eventually interact with security tools through controlled
interfaces.

Initial tools:

- Nmap
- HTTP analysis
- ffuf
- Python

Tool execution will be mediated by the application and restricted to
authorized targets and controlled environments.

---

## Security Labs

The first planned security laboratory is:

**OWASP Juice Shop**

The lab will provide an intentionally vulnerable and isolated environment
for testing ACID AI.

Planned experiments include:

- Reconnaissance
- Vulnerability analysis
- Security tool usage
- Agent decision-making
- Automated security testing

The laboratory environment is intended to ensure that offensive security
capabilities can be developed and tested safely.

---

## Knowledge

ACID AI will eventually use **Retrieval-Augmented Generation (RAG)** to
provide additional cybersecurity knowledge to the model.

Potential knowledge sources include:

- OWASP
- MITRE ATT&CK
- Security research
- Project documentation
- Laboratory documentation

The knowledge layer will allow the agent to retrieve relevant information
when analyzing security problems.

---

## Memory

ACID AI will maintain different types of context and memory.

Planned capabilities include:

- Conversation history
- Session context
- Security findings
- Long-term memory

Memory will be managed by the application rather than being treated as
permanent model memory.

---

## Roadmap

### Infrastructure

- [x] Git
- [x] GitHub SSH
- [x] Docker
- [x] NVIDIA Container Toolkit
- [x] NVIDIA GPU inside Docker

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

### Knowledge & Memory

- [ ] Implement RAG
- [ ] Add OWASP knowledge
- [ ] Add MITRE ATT&CK knowledge
- [ ] Conversation history
- [ ] Session context
- [ ] Security findings
- [ ] Long-term memory

### Security & Testing

- [ ] Target allowlist
- [ ] Command validation
- [ ] Sandbox execution
- [ ] Audit logging
- [ ] Unit tests
- [ ] Agent behavior tests
- [ ] Tool integration tests
- [ ] Security tests
- [ ] Model evaluation

### Security Lab

- [ ] Deploy OWASP Juice Shop
- [ ] Create isolated lab environment
- [ ] Create automated security tests
- [ ] Test reconnaissance
- [ ] Test vulnerability analysis
- [ ] Test agent decision-making

---

## 💻 Tech Stack

| Component | Technology |
|---|---|
| Operating System | Fedora Linux |
| AI Runtime | Ollama |
| Containers | Docker |
| Language | Python |
| GPU | NVIDIA RTX 4050 |
| Initial Model | Dolphin3-Cyber 8B |
| Security Lab | OWASP Juice Shop |

---

## Project Structure

```
local-ai/
├── app/              # Application layer
├── agent/            # Agent and decision-making logic
├── tools/            # Security tool integrations
├── knowledge/        # RAG and cybersecurity knowledge
├── memory/           # Persistent context and findings
├── tests/            # Unit and security tests
├── labs/             # Isolated security laboratories
├── data/             # Local application data
├── models/           # Local models
├── compose.yml       # Container orchestration
├── README.md
└── .gitignore
```

This structure represents the planned architecture. Components will be
introduced incrementally as the project evolves.

---

## Privacy

ACID AI follows a **local-first architecture**.

Models, conversations, memory, databases, and other local data are intended
to remain on the user's machine and are not committed to the repository.

External services are not required for the core AI infrastructure.

---

## Status

 **Work in progress**

ACID AI is an experimental open-source project focused on the intersection
of:

**Cybersecurity × Artificial Intelligence × Automation**

Built as part of the **ACID** cybersecurity initiative.

---

### ACID

*Aprendemos juntos. Construímos juntos. Hackeamos juntos.*
