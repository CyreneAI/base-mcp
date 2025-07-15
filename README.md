## 📦 Base MCP (Multi-Channel Platform Server)

This repository provides the Base MCP (Multi-Channel Platform) server image and common configurations for other specialized MCP services within the Multi-Agent Bot system. It serves as a foundational Docker image (`Dockerfile.base`) that other MCPs can build upon, ensuring consistent dependencies and basic setup. While it doesn't expose any tools itself, it's crucial for streamlining the development and deployment of other MCPs.

## ✨ Features

- **Standardized Base Image**: Provides a consistent Python environment and common dependencies (like FastAPI, FastMCP, uvicorn, httpx, python-dotenv) for all specialized MCPs.
- **Reduced Image Size**: By building on a common base, individual MCP Docker images can be smaller and build faster.
- **Simplified Dependency Management**: Common dependencies are managed in one place.
- **Modular Foundation**: A clear separation of concerns, where the base provides the runtime environment and specialized MCPs add their unique tools.

## 🏛️ Architecture Context

The base-mcp repository primarily defines a `Dockerfile.base` that other MCPs (web-mcp, finance-mcp, rag-mcp, telegram-mcp, discord-mcp) use as their starting point (`FROM multi-agent-bot/base-mcp:latest`). This ensures that all MCPs share a consistent and optimized environment.


## 🚀 Getting Started

### Prerequisites

* Docker Desktop

### Building the Base Image

This repository's primary output is a Docker image that other MCPs will use. You'll typically build this image as part of your main orchestrator's build process.

Clone this repository:

```bash
git clone https://github.com/CyreneAI/base-mcp.git
cd base-mcp
```

Build the Docker image:

```bash
docker build -t multi-agent-bot/base-mcp:latest -f Dockerfile.base .
```

This command builds the base image and tags it as `multi-agent-bot/base-mcp:latest`. Other MCPs can then use this tag in their `FROM` instructions.

### Usage

This base-mcp itself is not run as a separate service. Its purpose is to provide a common foundation for other MCPs. You will see lines like:

```dockerfile
FROM multi-agent-bot/base-mcp:latest
```

in the Dockerfile of other MCP repositories.

## 📁 Project Structure

```
base-mcp/
├── .gitignore
├── README.md            # <- This file
├── Dockerfile.base      # The Dockerfile for building the base MCP image
└── requirements.txt     # Python dependencies for the base MCP environment
```
