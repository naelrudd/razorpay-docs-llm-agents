> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Connect Razorpay MCP Server to VS Code

> Connect the Razorpay MCP Server to Visual Studio Code in agent mode using user settings that prompt securely for your merchant token.

Available in
🇮🇳 India

Visual Studio Code supports MCP servers in agent mode through user settings. The following configuration prompts you securely for your merchant token instead of storing it in plain text.

> [!NOTE]
>
> **Handy Tips**
>
> Visual Studio Code requires Node.js and `npm` for the `mcp-remote` bridge. Refer to the [Remote MCP Server setup](https://razorpay.com/docs/mcp-server/remote.md#step-1-install-node-js) to install Node.js and generate your Base64-encoded merchant token.

## Visual Studio Code Configuration

1. Open **Visual Studio Code**.
2. Open the Command Palette and select **Preferences: Open User Settings (JSON)**.
3. Paste the following configuration into the settings file and save it:

```json Visual Studio Code Configuration theme={null}
{
  "mcp": {
    "inputs": [
      {
        "type": "promptString",
        "id": "merchant_token",
        "description": "Razorpay Merchant Token",
        "password": true
      }
    ],
    "servers": {
      "razorpay-remote": {
        "command": "npx",
        "args": [
          "mcp-remote",
          "https://mcp.razorpay.com/mcp",
          "--header",
          "Authorization: Basic ${input:merchant_token}"
        ]
      }
    }
  }
}
```

4. When you start the server, Visual Studio Code prompts you to enter your Base64-encoded merchant token. Paste the token to complete the connection.

> [!NOTE]
>
> **Handy Tips**
>
> To learn more about running MCP servers in Visual Studio Code, refer to the [agent mode documentation](https://code.visualstudio.com/docs/copilot/chat/mcp-servers).

## Video Walkthrough

Watch this video to see how to connect the Razorpay MCP Server to Visual Studio Code.

[Connect Razorpay MCP Server to Visual Studio Code](https://www.youtube.com/embed/rVJvaLu_1UA)

> [!NOTE]
>
> **Need Help?**
>
> If you need any assistance with the integration, reach out to us at [agentic-payments@razorpay.com](mailto:agentic-payments@razorpay.com).
