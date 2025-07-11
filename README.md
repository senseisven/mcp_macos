# MCP Remote macOS Control Server + AI Chat Web App

**The first open-source MCP server that enables AI to fully control remote macOS systems, now with a web-based chat interface.**

This project provides both:
1. **MCP Server** - Python-based server for remote macOS control via VNC
2. **AI Chat Web App** - Modern web interface for chatting with AI to control your Mac

## 🚀 Quick Start for Web App

### Prerequisites
- Docker Desktop installed
- Node.js 18+ installed
- A Mac with Screen Sharing enabled (can be the same machine)

### 1. Clone and Setup
```bash
git clone <repository-url>
cd mcp_macos

# Install root dependencies
npm install

# Install frontend and backend dependencies
npm run install:all
```

### 2. Configure Environment
```bash
# Copy example environment file
cp backend/.env.example backend/.env

# Edit backend/.env with your settings:
# - MACOS_HOST=localhost (for local control)
# - MACOS_PASSWORD=your_vnc_password
# - OPENAI_API_KEY=your_openai_api_key
```

### 3. Enable Screen Sharing (macOS)
1. Open System Preferences > Sharing
2. Enable "Screen Sharing"
3. Set a VNC password when prompted

### 4. Run the Application
```bash
# Start both frontend and backend
npm run dev

# Or start individually:
npm run dev:frontend  # Frontend on http://localhost:3000
npm run dev:backend   # Backend on http://localhost:3001
```

### 5. Open and Chat!
1. Open http://localhost:3000 in your browser
2. Wait for connection to establish
3. Try commands like:
   - "Take a screenshot"
   - "Open Safari"
   - "Click on the Dock"
   - "Type hello world"

## 📁 Project Structure

```
mcp_macos/
├── frontend/           # Next.js React frontend
│   ├── src/
│   │   ├── components/ # Chat interface components
│   │   ├── hooks/      # Socket.IO and state management
│   │   ├── stores/     # Zustand state stores
│   │   └── types/      # TypeScript definitions
├── backend/            # Node.js Express backend
│   ├── src/
│   │   ├── services/   # MCP client, LLM service, chat service
│   │   ├── config/     # Environment configuration
│   │   └── utils/      # Logging and utilities
└── src/               # Original Python MCP server
    ├── mcp_remote_macos_use/
    ├── action_handlers.py
    └── vnc_client.py
```

## 🔧 Development Commands

```bash
# Development
npm run dev              # Start both frontend and backend
npm run dev:frontend     # Start only frontend
npm run dev:backend      # Start only backend

# Building
npm run build            # Build both
npm run build:frontend   # Build frontend only
npm run build:backend    # Build backend only

# Testing
npm run test             # Run all tests
```

## 🎯 Architecture

```
Browser ←→ Frontend (Next.js) ←→ Backend (Node.js) ←→ MCP Server (Python) ←→ macOS
         WebSocket/HTTP        Socket.IO/REST      Docker/stdio         VNC
```

## 🛠️ How It Works

1. **Frontend**: Modern React app with real-time chat interface
2. **Backend**: Express.js server with Socket.IO for real-time communication
3. **LLM Integration**: OpenAI GPT-4 for natural language understanding
4. **MCP Client**: Communicates with Python MCP server via Docker
5. **macOS Control**: VNC-based control of local or remote Macs

## 🎮 Example Interactions

```
You: "Take a screenshot"
AI: "Here's a screenshot of your Mac desktop:" [shows image]

You: "Click on Safari in the dock"
AI: "I'll click on Safari in the dock for you" [clicks Safari]

You: "Open a new tab and go to apple.com"
AI: "Opening a new tab and navigating to apple.com" [executes commands]
```

## 🔒 Security Notes

- Only use with Macs you own or have explicit permission to control
- VNC passwords are transmitted securely
- LLM API keys are stored server-side only
- All actions are logged for debugging

## 📚 Original MCP Server Documentation

The original Python MCP server functionality remains fully intact. See below for the original documentation about using it directly with Claude Desktop.

---

# Original MCP Server Documentation

**The first open-source MCP server that enables AI to fully control remote macOS systems.**

**A direct alternative to OpenAI Operator, optimized specifically for autonomous AI agents with complete desktop capabilities, requiring no additional software installation.**

[![Docker Pulls](https://img.shields.io/docker/pulls/buryhuang/mcp-remote-macos-use)](https://hub.docker.com/r/buryhuang/mcp-remote-macos-use)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Showcases**
- Research Twitter and Post Twitter(https://www.youtube.com/watch?v=--QHz2jcvcs)
<img width="400" alt="image" src="https://github.com/user-attachments/assets/bfe6e354-3d59-4d08-855b-2eecdaaeb46f" />

- Use CapCut to create short highlight video(https://www.youtube.com/watch?v=RKAqiNoU8ec)
<img width="400" alt="image" src="https://github.com/user-attachments/assets/3b4d07c5-cd25-4dae-b9a1-a373bf7492aa" />

- AI Recruiter: Automated candidate information collection, qualifying applications and sending screening sessions using Mail App
- AI Marketing Intern: LinkedIn engagement - automated following, liking, and commenting with relevant users
- AI Marketing Intern: Twitter engagement - automated following, liking, and commenting with relevant users

## To-Do List (Prioritized)

1. **Performance Optimization** - Match speed of Ubuntu desktop alternatives
2. **Apple Scripts Generation** - Reduce execution time while maintaining flexibility
3. **VNC Cursor Visibility** - Improve debugging and demo experience

*We welcome contributions!*

## Features

* **No Extra API Costs**: Free screen processing with your existing Claude Pro plan
* **Minimal Setup**: Just enable Screen Sharing on the target Mac – no additional software needed
* **Universal Compatibility**: Works with all macOS versions, current and future
  
## Why We Built This

### Native macOS Experience Without Compromise
The macOS native ecosystem remains unmatched in user experience today and will continue to be the gold standard for years to come. This is where human capabilities truly thrive, and now your AI can operate in this environment with the same fluency.

### Open Architecture By Design
* **Universal LLM Compatibility**: Work with any MCP Client of your choice
* **Model Flexibility**: Seamlessly integrate with OpenAI, Anthropic, or any other LLM provider
* **Future-Proof Integration**: Designed to evolve with the MCP ecosystem

### Effortless Deployment
* **Zero Setup on Target Machines**: No background applications or agents needed on macOS
* **Screen Sharing is All You Need**: Control any Mac with Screen Sharing enabled
* **Eliminate Backend Complexity**: Unlike other solutions that require running Python applications or background services

### Streamlined Bootstrap Process
* **Leverage Claude Desktop's Polished UI**: No need for developer-style Python interfaces
* **Intuitive User Experience**: Interact with your AI-controlled Mac through a familiar, user-friendly interface
* **Instant Productivity**: Start working immediately without configuration hassles

## Architecture
<img width="912" alt="remote_macos_use_system_architecture" src="https://github.com/user-attachments/assets/75ece060-90e2-4ad3-bb52-2c69427001dd" />


## Installation
- [Enable Screen Sharing on MacOs](https://support.apple.com/guide/remote-desktop/set-up-a-computer-running-vnc-software-apdbed09830/mac) **If you rent a mac from macstadium.com, you can skip this step**
- [Connect to your remote MacOs](https://support.apple.com/guide/mac-help/share-the-screen-of-another-mac-mh14066/mac)
- [Install Docker Desktop for local Mac](https://docs.docker.com/desktop/setup/install/mac-install/)
- [Add this MCP server to Claude Desktop](https://modelcontextprotocol.io/quickstart/user)
You can configure Claude Desktop to use the Docker image by adding the following to your Claude configuration:
```json
{
  "mcpServers": {
    "remote-macos-use": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "-e",
        "MACOS_USERNAME=your_macos_username",
        "-e",
        "MACOS_PASSWORD=your_macos_password",
        "-e",
        "MACOS_HOST=your_macos_hostname_or_ip",
        "--rm",
        "buryhuang/mcp-remote-macos-use:latest"
      ]
    }
  }
}
```

### WebRTC Support via LiveKit

This server now includes WebRTC support through LiveKit integration, enabling:
- Low-latency real-time screen sharing
- Improved performance and responsiveness
- Better network efficiency compared to traditional VNC
- Automatic quality adaptation based on network conditions

To use WebRTC features, you'll need to:
1. Set up a LiveKit server or use LiveKit Cloud
2. Configure the LiveKit environment variables as shown in the configuration example above

## Developer Instruction
### Clone the repo
```bash
# Clone the repository
git clone https://github.com/yourusername/mcp-remote-macos-use.git
cd mcp-remote-macos-use
```

### Building the Docker Image

```bash
# Build the Docker image
docker build -t mcp-remote-macos-use .
```

## Cross-Platform Publishing

To publish the Docker image for multiple platforms, you can use the `docker buildx` command. Follow these steps:

1. **Create a new builder instance** (if you haven't already):
   ```bash
   docker buildx create --use
   ```

2. **Build and push the image for multiple platforms**:
   ```bash
   docker buildx build --platform linux/amd64,linux/arm64 -t buryhuang/mcp-remote-macos-use:latest --push .
   ```

3. **Verify the image is available for the specified platforms**:
   ```bash
   docker buildx imagetools inspect buryhuang/mcp-remote-macos-use:latest
   ```

## Usage

The server provides Remote MacOs functionality through MCP tools.

### Tools Specifications

The server provides the following tools for remote macOS control:

#### remote_macos_get_screen
Connect to a remote macOS machine and get a screenshot of the remote desktop. Uses environment variables for connection details.

#### remote_macos_send_keys
Send keyboard input to a remote macOS machine. Uses environment variables for connection details.

#### remote_macos_mouse_move
Move the mouse cursor to specified coordinates on a remote macOS machine, with automatic coordinate scaling. Uses environment variables for connection details.

#### remote_macos_mouse_click
Perform a mouse click at specified coordinates on a remote macOS machine, with automatic coordinate scaling. Uses environment variables for connection details.

#### remote_macos_mouse_double_click
Perform a mouse double-click at specified coordinates on a remote macOS machine, with automatic coordinate scaling. Uses environment variables for connection details.

#### remote_macos_mouse_scroll
Perform a mouse scroll at specified coordinates on a remote macOS machine, with automatic coordinate scaling. Uses environment variables for connection details.

#### remote_macos_open_application
Opens/activates an application and returns its PID for further interactions.

#### remote_macos_mouse_drag_n_drop
Perform a mouse drag operation from start point and drop to end point on a remote macOS machine, with automatic coordinate scaling.

All tools use the environment variables configured during setup instead of requiring connection parameters.

## Limitations

- **Authentication Support**: 
  - Only Apple Authentication (protocol 30) is supported

## Security Note

https://support.apple.com/guide/remote-desktop/encrypt-network-data-apdfe8e386b/mac
https://cafbit.com/post/apple_remote_desktop_quirks/

We only support protocol 30, which uses the Diffie-Hellman key agreement protocol with a 512-bit prime. This protocol is used by macOS 11 to macOS 12 when communicating with OS X 10.11 or earlier clients.

Here's the information converted to a markdown table:

| macOS version running Remote Desktop | macOS client version | Authentication | Control and Observe | Copy items or install package | All other tasks | Protocol Version |
|--------------------------------------|----------------------|----------------|---------------------|-------------------------------|----------------|----------------|
| macOS 13 | macOS 13 | 2048-bit RSA host keys | 2048-bit RSA host keys | 2048-bit RSA host keys to authenticate, then 128-bit AES | 2048-bit RSA host keys | 36 |
| macOS 13 | macOS 10.12 | Secure Remote Password (SRP) protocol for local only. Diffie-Hellman (DH) if bound to LDAP or macOS server is version 10.11 or earlier | SRP or DH,128-bit AES | SRP or DH to authenticate, then 128-bit AES | 2048-bit RSA host keys | 35 |
| macOS 11 to macOS 12 | macOS 10.12 to macOS 13 | Secure Remote Password (SRP) protocol for local only, Diffie-Hellman if bound to LDAP | SRP or DH 1024-bit, 128-bit AES | 2048-bit RSA host keys macOS 13 to macOS 10.13 | 2048-bit RSA host keys macOS 10.13 or later |  33 |
| macOS 11 to macOS 12 | OS X 10.11 or earlier | DH 1024-bit | DH 1024-bit, 128-bit AES | Diffie-Hellman Key agreement protocol with a 512-bit prime | Diffie-Hellman Key agreement protocol with a 512-bit prime |  30 |


Always use secure, authenticated connections when accessing remote remote MacOs machines. This tool should only be used with servers you trust and have permission to access.

## License

See the LICENSE file for details. 
