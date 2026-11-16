> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Razorpay MCP Server Integrations

> Connect the Razorpay MCP Server to AI platforms such as Claude, ChatGPT, Cursor, VS Code, Windsurf, Replit, and Gemini CLI.

Available in
🇮🇳 India

The Razorpay MCP Server connects to a wide range of AI platforms, letting your AI tool create and track payments, Payment Links, orders, refunds, settlements, payouts, and QR codes using natural language commands.

Each platform has its own configuration method, so follow the guide that matches the tool you use. Where Razorpay is already available as a built-in connector or app, no manual configuration is required. All guides use the recommended [Remote MCP Server](https://razorpay.com/docs/mcp-server/remote.md) endpoint `https://mcp.razorpay.com/mcp`.

> [!NOTE]
>
> **Handy Tips**
>
> Before you begin, generate your [Razorpay API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md#generate-api-keys) and, for platforms that connect through the `mcp-remote` bridge (Cursor, Visual Studio Code, and Windsurf), install Node.js. Refer to the [Remote MCP Server setup](https://razorpay.com/docs/mcp-server/remote.md) for prerequisites and to encode your merchant token.

## Choose Your Platform

> [card] [Claude](https://razorpay.com/docs/mcp-server/integrations/claude.md)
>
> Connect using the official Razorpay connector or Claude Code (CLI).

> [card] [ChatGPT](https://razorpay.com/docs/mcp-server/integrations/chatgpt.md)
>
> Install the official Razorpay app and authorise it using OAuth.

> [card] [Cursor](https://razorpay.com/docs/mcp-server/integrations/cursor.md)
>
> Add the server through the mcp-remote bridge in mcp.json.

> [card] [Visual Studio Code](https://razorpay.com/docs/mcp-server/integrations/vs-code.md)
>
> Configure agent mode with a secure merchant token prompt.

> [card] [Windsurf](https://razorpay.com/docs/mcp-server/integrations/windsurf.md)
>
> Add the server to the Cascade agent via mcp\_config.json.

> [card] [Replit](https://razorpay.com/docs/mcp-server/integrations/replit.md)
>
> Add the server from Integrations settings and authorise via OAuth.

> [card] [Gemini CLI](https://razorpay.com/docs/mcp-server/integrations/gemini-cli.md)
>
> Add the server to the mcpServers block in settings.json.
