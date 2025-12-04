# AdoPrManager

A Model Context Protocol (MCP) server for managing Azure DevOps Pull Requests.

## Features

- **Manage PRs**: Create, list, get details, and update Pull Requests.
- **Collaborate**: Add and view comments on PR threads.
- **Inspect**: View file changes and diffs.

## Quick Start

### Prerequisites

- Python 3.10+
- Azure DevOps Personal Access Token (PAT) with **Code (Read & Write)** and **Pull Request Threads (Read & Write)** scopes.

### Installation

Install via `pip` or `uv`:

```bash
pip install ado-pr-manager
# or
uv pip install ado-pr-manager
```

### Configuration

Set the following environment variables:

| Variable | Description | Required |
|----------|-------------|----------|
| `AZDO_ORG_URL` | Organization URL (e.g., `https://dev.azure.com/myorg`) | Yes |
| `AZDO_PAT` | Personal Access Token | Yes |
| `AZDO_REPO_ID` | Default Repository ID or Name (alias: `AZDO_REPO`) | Optional |
| `AZDO_PROJECT` | Default Project Name | Optional |
| `AZDO_DEFAULT_BRANCH` | Default target branch (default: `main`) | Optional |

### Usage with Claude Desktop

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "ado-pr-manager": {
      "command": "python3",
      "args": ["-m", "ado_pr_manager.server"],
      "env": {
        "AZDO_ORG_URL": "https://dev.azure.com/myorg",
        "AZDO_PAT": "your-token",
        "AZDO_REPO_ID": "your-repo"
      }
    }
  }
}
```

## Development

1.  **Clone & Install**:
    ```bash
    git clone https://github.com/om-surushe/ado-pr-manager.git
    cd ado-pr-manager
    python3 -m venv .venv
    source .venv/bin/activate
    pip install -e .[dev]
    ```

2.  **Test**:
    ```bash
    pytest
    ```
