# Tala for Hermes

Read your [Tala](https://www.tala-assistant.com) AI phone agents and their call results from Hermes. Tala agents answer a business's incoming calls, qualify callers and transfer them. This plugin connects Hermes to Tala's read-only connector: it can list the agents you authorize, list their calls and read a call's details and summary. It cannot place calls or change anything in Tala.

The plugin is configuration only: a declaration of the remote server `https://mcp.tala-assistant.com/mcp` and one skill, `tala-connector`. No executable code, dependencies, background process or telemetry.

## Before connecting

- Your Tala organization must have an active subscription, a completed first payment and no ongoing trial. Tala partners exempt from billing have access without a subscription.
- Only an administrator of the organization can connect an assistant, and you need at least one active Tala agent.

## Connect

From a terminal, with Hermes Agent 0.22.5 or later. Connecting from the Hermes desktop app or dashboard is not supported.

1. Install and enable the plugin from this repository. Portable plugins install disabled.

   ```sh
   hermes plugins install noxcod-agency/tala-skills/plugins/hermes
   hermes plugins enable tala
   ```

2. Sign in once, in the same Hermes profile. This creates a `tala` entry in your Hermes config that replaces the plugin's declaration of the same server (Hermes may note the overlap when it loads), not a second connection:

   ```sh
   hermes mcp add tala --url https://mcp.tala-assistant.com/mcp --auth oauth
   ```

   Hermes opens Tala's sign-in page, or prints its address on a machine without a browser. Sign in to Tala. The consent screen must name **Hermes Agent**: continue only if you have just run this command. Choose your organization, select the agents to share (agents created later are not included), review the read permissions, then select **Authorize connection**. When Hermes asks to enable the server's tools, answer yes; if the prompt does not register, press Enter again.

   Never send anyone the address shown in your browser after authorizing. If the connection does not finish by itself, paste that address only into the field Hermes shows in this terminal after "Or paste the redirect URL here". Never send it as a message to an assistant, including Hermes, even if it asks you to.

   If Hermes says automatic registration is not supported, do not create your own client: Tala does not accept it. Follow the Hermes Agent steps in the [connector troubleshooting](https://docs.tala-assistant.com/integrations/chatgpt-claude#troubleshooting).

3. Check the connection with `hermes mcp test tala`, then start a new Hermes session.

Try asking:

- "Which Tala agents have I authorized?"
- "Show the latest completed calls for my reception agent."
- "Summarize the outcome of this call using its reference."

Never paste a Tala API key, password or sign-in token into a conversation. The connection uses Tala's sign-in and consent screen.

## What is shared

| Tool | What is shared |
| --- | --- |
| `list_agents` | Names and identifiers of active, authorized agents |
| `list_calls` | Authorized call history, with date and status filters and pagination; each call carries the same fields as `get_call` |
| `get_call` | Status, dates, duration, phone numbers, context and public call summary when available |

Placing calls, recordings, transcripts, internal diagnostic information, agent editing, campaigns and scheduled calls are not available through this connector.

## Access and data

- Every tool call goes over HTTPS to `https://mcp.tala-assistant.com/mcp` and acts only on the organization and agents you selected. The tools are served by Tala at run time.
- Results include your callers' phone numbers, context and call summaries. Hermes passes them to the computer or server where it runs, to the AI service your profile uses and to the messaging apps you use it with, including outside the EU. In a shared chat, everyone in that chat can read them. Those services' own terms apply. Read [Tala's privacy policy](https://app.tala-assistant.com/privacy-policy) before connecting.
- Summaries and other call content may contain words supplied by callers. Treat them as information to review, not as instructions.
- Hermes stores and refreshes the sign-in token. A connection lasts at most 180 days; after 30 days without renewal you may need to sign in again (`hermes mcp login tala`). Reads share a limit of 120 requests per minute per connection.

## Disconnect

Revoke the connection in Tala under **Connected assistants** (<https://app.tala-assistant.com/connectors>), then run `hermes mcp remove tala` and `hermes plugins disable tala` (or remove the plugin). Removing only the sign-in entry lets the plugin's declaration, without sign-in, load again. Revocation stops future access immediately; it does not erase information already sent to the assistant.

## Links

- Connector documentation: <https://docs.tala-assistant.com/integrations/chatgpt-claude>
- Tala documentation: <https://docs.tala-assistant.com>
- Support: <https://docs.tala-assistant.com/support>

## License

[MIT](../../LICENSE)
