> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Connect Razorpay MCP Server to Cursor

> Connect the Razorpay MCP Server to Cursor through the mcp-remote bridge by editing the mcp.json configuration file.

Available in
🇮🇳 India

Cursor connects to the Razorpay Remote MCP Server through the `mcp-remote` bridge. You can add it from Cursor Settings, or by editing the MCP configuration file directly.

> [!NOTE]
>
> **Handy Tips**
>
> Cursor requires Node.js and `npm` for the `mcp-remote` bridge. Refer to the [Remote MCP Server setup](https://razorpay.com/docs/mcp-server/remote.md#step-1-install-node-js) to install Node.js and generate your Base64-encoded merchant token.

## Cursor Configuration

1. Open **Cursor** and navigate to **Settings** → **Cursor Settings**.
2. Go to **MCP Tools** and click **Add Custom MCP**. This opens your `mcp.json` file.
3. Paste the following configuration and save the file:

```json Cursor Configuration theme={null}
{
  "mcpServers": {
    "rzp-mcp-server": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.razorpay.com/mcp",
        "--header",
        "Authorization:${AUTH_HEADER}"
      ],
      "env": {
        "AUTH_HEADER": "Basic <Base64(key:secret)>"
      }
    }
  }
}
```

4. Replace `<Base64(key:secret)>` with your Base64-encoded token.
5. Cursor starts the server and lists the available Razorpay tools, which confirms a successful connection.

> [!NOTE]
>
> **Handy Tips**
>
> The `.cursor/mcp.json` file in a repository root applies to that project only, while `~/.cursor/mcp.json` applies globally. If both files define the server, the project configuration takes precedence.

## Video Walkthrough

Watch this video to see how to set up the Razorpay MCP Server in the Cursor agent.

[Set up Razorpay MCP Server in Cursor Agent](https://www.youtube.com/embed/vpm94BATvUc)

Watch this video to see how to configure the Razorpay MCP Server in the Cursor CLI.

[Configure Razorpay MCP Server in Cursor CLI](https://www.youtube.com/embed/priYWCinKpI)

> [!NOTE]
>
> **Need Help?**
>
> If you need any assistance with the integration, reach out to us at [agentic-payments@razorpay.com](mailto:agentic-payments@razorpay.com).
