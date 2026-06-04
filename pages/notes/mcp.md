# VSCODE 配置 mcp

1. 配置文件系统 
``` bash
// 安装 @modelcontextprotocol/server-filesystem
npm install -g @modelcontextprotocol/server-filesystem
```

配置完后需要重新启动 vscode

2. 配置 mcp.json

``` JSON
{
    "mcpServers": {
        "Framelink Figma MCP": {
            "command": "cmd",
            "args": [
                "/c",
                "npx",
                "-y",
                "figma-developer-mcp",
                "--stdio"
            ],
            "env": {
                "FIGMA_API_KEY": "figd_<YOUR_API_KEY>"
            },
            "disabled": false
        },
        "filesystem": {
            "command": "cmd",
            "args": [
                "/c",
                "npx",
                "-y",
                "@modelcontextprotocol/server-filesystem",
                "D:\\sn_work_files\\Documents",
                "D:\\workspace\\wms_289_pda"
            ],
            "disabled": false
        }
    }
}
```