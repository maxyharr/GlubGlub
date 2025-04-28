# GlubGlub

A repository demonstrating GitHub MCP server configuration in VS Code.

## Creating GitHub Repositories via GitHub MCP Server in VS Code

This repository demonstrates how to create and manage GitHub repositories using the Model Context Protocol (MCP) server configured within Visual Studio Code.

### What is MCP?

Model Context Protocol (MCP) is a standardized communication protocol that allows large language models (LLMs) to interact with external services and tools. In the context of VS Code, it enables GitHub Copilot and other AI tools to perform actions on your behalf, such as creating repositories.

### Setting Up GitHub MCP Server in VS Code

There are two main approaches to configuring GitHub MCP server in VS Code:

#### Option 1: Using Docker (Recommended)

1. **Install the GitHub extension for VS Code**
   - Open VS Code
   - Go to the Extensions view (Ctrl+Shift+X or Cmd+Shift+X on Mac)
   - Search for "GitHub"
   - Install the official GitHub extension

2. **Sign in to GitHub in VS Code**
   - Open the Command Palette (Ctrl+Shift+P or Cmd+Shift+P on Mac)
   - Type "GitHub: Sign In" and select it
   - Follow the authentication flow to connect your GitHub account

3. **Configure Docker-based MCP Integration**
   - Ensure Docker is installed on your system
   - Generate a GitHub Personal Access Token with necessary permissions
   - In settings.json, add or modify:
   ```json
   "mcp": {
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "your_personal_access_token"
         }
       }
     }
   }
   ```

#### Option 2: Using Copilot Advanced Settings

1. **Install GitHub Copilot**
   - Open VS Code
   - Go to the Extensions view
   - Search for "GitHub Copilot"
   - Install and configure GitHub Copilot

2. **Enable MCP Support**
   - In settings.json, add or modify:
   ```json
   "github.copilot.advanced": {
     "enableMCPSupport": true
   }
   ```

### Creating a New Repository using MCP

With the MCP server correctly configured, you can use natural language to ask GitHub Copilot to create repositories:

1. Open the GitHub Copilot chat panel in VS Code
2. Type a command like "Create a new GitHub repository named MyProject"
3. Copilot will use MCP to interface with GitHub's API and create the repository
4. You can specify additional details like description, visibility, and whether to initialize with README

### Benefits of Using MCP for GitHub Operations

- **Streamlined Workflow**: Create repositories without leaving your development environment
- **Natural Language Interface**: No need to remember specific commands or navigate GitHub web UI
- **Integration with Other Tools**: MCP can be extended to perform other GitHub operations like creating issues, PRs, etc.

### Example Commands

- "Create a new private GitHub repo named secret-project with a Python .gitignore"
- "Create a public JavaScript repository with README and MIT license"
- "Fork repository xyz/awesome-project to my account"

### How This Repository Was Created

This very repository (`GlubGlub`) was created using GitHub Copilot with MCP configured in VS Code on April 28, 2025.

## Getting Started

To clone and work with this repository:

```bash
git clone https://github.com/maxyharr/GlubGlub.git
cd GlubGlub
```

## Learn More

- [GitHub MCP Documentation](https://docs.github.com/en/mcp)
- [VS Code GitHub Integration](https://code.visualstudio.com/docs/editor/github)
- [Model Context Protocol Specification](https://github.com/microsoft/model-context-protocol)