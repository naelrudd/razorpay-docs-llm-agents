> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Connect Razorpay MCP Server to Windsurf

> Connect the Razorpay MCP Server to the Windsurf Cascade agent by adding the server entry to the raw mcp_config.json file.

Available in
🇮🇳 India

The Windsurf Cascade agent reads MCP servers from a single configuration file. Add the Razorpay Remote MCP Server using the raw configuration editor.

> [!NOTE]
>
> **Handy Tips**
>
> Windsurf requires Node.js and `npm` for the `mcp-remote` bridge. Refer to the [Remote MCP Server setup](https://razorpay.com/docs/mcp-server/remote.md#step-1-install-node-js) to install Node.js and generate your Base64-encoded merchant token.

## Windsurf Configuration

1. Open **Windsurf** and navigate to **Windsurf Settings** → **Cascade** → **MCP Servers**. You can also click the MCP icon at the top-right of the Cascade panel.
2. Click **Manage MCPs**, then click **View raw config** to open the `mcp_config.json` file.
3. Add the following Razorpay server entry to the file and save it:

```json Windsurf Configuration theme={null}
{
  "mcpServers": {
    "rzp-mcp-server": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.razorpay.com/mcp",
        "--header",
        "Authorization: Basic <your-base64-encoded-key-secret>"
      ]
    }
  }
}
```

4. Return to the **Manage MCPs** page and click **Refresh** to connect to the server and fetch the Razorpay tools.

> [!NOTE]
>
> **Handy Tips**
>
> The configuration file is located at `~/.codeium/windsurf/mcp_config.json` on macOS and `%USERPROFILE%\.codeium\windsurf\mcp_config.json` on Windows. Windsurf supports global configuration only and does not interpolate environment variables, so enter the token value directly.

> [!NOTE]
>
> **Need Help?**
>
> If you need any assistance with the integration, reach out to us at [agentic-payments@razorpay.com](mailto:agentic-payments@razorpay.com).
