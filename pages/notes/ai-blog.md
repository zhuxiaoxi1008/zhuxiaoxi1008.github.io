### ai 笔记
https://www.freedidi.com/21795.html

vscode MCP 插件
---
``` PYTHON
pip install fastmcp-file-server

{
  "mcpServers": {
    "filesystem": {
      "command": "fastmcp-file-server",
      "env": {
        "MCP_ALLOWED_PATH": "${workspaceFolder}"
      },
      "cwd": "${workspaceFolder}"
    }
  }
}
```