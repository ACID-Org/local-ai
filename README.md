# Local AI

A local AI assistant designed to run entirely on a personal machine using
Ollama, Docker, and NVIDIA GPU acceleration.

## Goal

The goal of this project is to build a private and customizable AI assistant
for everyday use, while keeping data and processing under the user's control.

The project will start as a terminal-based assistant and gradually gain
persistent memory, document retrieval, and controlled access to local tools.

## Technologies

- Fedora Linux
- Docker
- Docker Compose
- Ollama
- NVIDIA GPU
- Python

## Features

Planned features include:

- Terminal-based AI interaction
- Local model execution
- Persistent conversation history
- Long-term memory
- Retrieval-Augmented Generation (RAG)
- Local document processing
- Controlled access to system tools
- Privacy-focused architecture

## Roadmap

- [x] Configure Git
- [x] Configure SSH authentication with GitHub
- [x] Configure Docker
- [x] Configure NVIDIA GPU support for Docker
- [ ] Run Ollama in a container
- [ ] Run a local AI model
- [ ] Build the terminal interface
- [ ] Add conversation history
- [ ] Implement persistent memory
- [ ] Add RAG
- [ ] Add local tools
- [ ] Improve security and isolation
- [ ] Add automated tests
- [ ] Improve documentation

## Architecture

```
                  ┌──────────────┐
                  │   Terminal   │
                  └──────┬───────┘
                         │
                         ▼
                  ┌──────────────┐
                  │  AI Client   │
                  └──────┬───────┘
                         │
                         ▼
                  ┌──────────────┐
                  │    Ollama    │
                  └──────┬───────┘
                         │
                         ▼
                  ┌──────────────┐
                  │  AI Model    │
                  └──────┬───────┘
                         │
                         ▼
                  ┌──────────────┐
                  │ NVIDIA RTX   │
                  │     4050     │
                  └──────────────┘
```
## Project Structure

```
local-ai/
├── app/          # Application source code
├── data/         # Local data and persistent memory
├── compose.yml   # Docker Compose configuration
├── README.md
└── .gitignore
```

## Privacy

This project is designed with a local-first approach.

Conversation history, persistent memory, databases, models, and other local
data are intended to remain on the user's machine and are not committed to
the Git repository.

## Status

Work in progress.

This project is being developed as a personal learning and portfolio project,
with a focus on Linux, Docker, AI infrastructure, Python, and cybersecurity.
