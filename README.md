# cc-mcp-admin

Claude Code MCP Server Manager - A CLI tool to manage MCP servers across your projects.

## Features

- List all MCP servers across all projects with status indicators
- Show detailed configuration for specific servers with diff highlighting
- Add servers from other projects to current project
- Remove servers from current project
- Detect and highlight configuration differences

## Installation

```bash
cargo install --path .
```

Or build manually:

```bash
cargo build --release
cp .target/release/cc-mcp-admin ~/.local/bin/
```

## Usage

### List all MCP servers

```bash
cc-mcp-admin
# or
cc-mcp-admin list
```

Output shows:
- `●` (green) - enabled in current project
- `○` - not enabled in current project
- `(multiple configs)` - different configurations exist across projects

### Show server details

```bash
cc-mcp-admin serena
# or
cc-mcp-admin show serena
```

Displays all configurations with differences highlighted in yellow.

### Add a server to current project

```bash
cc-mcp-admin add serena
```

If multiple configurations exist, use `--from` to specify which one:

```bash
cc-mcp-admin add serena --from slint
cc-mcp-admin add psd2x --from navi
```

The `--from` option supports partial path matching.

### Remove a server from current project

```bash
cc-mcp-admin remove serena
```

## Configuration Sources

The tool reads MCP configurations from:

1. `~/.claude.json` - Global Claude Code settings (per-project `mcpServers`)
2. `.mcp.json` - Project-local MCP configuration files

## License

MIT
