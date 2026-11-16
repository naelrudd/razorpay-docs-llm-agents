> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Connect Razorpay MCP Server to Gemini CLI

> Connect the Razorpay MCP Server to Gemini CLI by adding the server to the mcpServers block in settings.json using HTTP transport.

Available in
🇮🇳 India

Gemini CLI discovers MCP servers from the `mcpServers` block in its `settings.json` file. Add the Razorpay Remote MCP Server using HTTP transport.

## Gemini CLI Configuration

1. Open your Gemini CLI settings file. Use `~/.gemini/settings.json` for global configuration, or `.gemini/settings.json` within a project.
2. Add the following Razorpay server entry and save the file:

```json Gemini CLI Configuration theme={null}
{
  "mcpServers": {
    "razorpay": {
      "httpUrl": "https://mcp.razorpay.com/mcp",
      "headers": {
        "Authorization": "Basic <your-base64-encoded-key-secret>"
      }
    }
  }
}
```

3. Replace `<your-base64-encoded-key-secret>` with your Base64 token. You can also reference an environment variable, such as `$RAZORPAY_TOKEN`, as Gemini CLI expands variables in the configuration. Refer to the [Remote MCP Server setup](https://razorpay.com/docs/mcp-server/remote.md#step-3-authenticate-razorpay-account) to generate the token.
4. Restart Gemini CLI and run `/mcp` to check the server status. If required, run `/mcp reload` to fetch the tools again.

> [!NOTE]
>
> **Need Help?**
>
> If you need any assistance with the integration, reach out to us at [agentic-payments@razorpay.com](mailto:agentic-payments@razorpay.com).
