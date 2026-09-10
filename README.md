<p align="center"><img src="assets/roost.png" width="112" alt="Roost bird logo"></p>

# Roost for Claude

Bring your connected coursework into Claude. Find assignments, understand their requirements, compare a draft with saved instructions, and practice from your course notes.

This plugin connects to [Roost](https://roostai.app) through its hosted, read-only MCP service. It includes a study skill and three guided commands. You need a Roost account with saved coursework or notes; school materials use the connections you set up in Roost.

## Install in Claude Code

Add the Roost marketplace and install the plugin:

```text
/plugin marketplace add chadwickboseman1675-stack/roost-claude-plugin
/plugin install roost@roost-plugins
```

Restart Claude Code to load the plugin. Run `/mcp`, select the Roost server, and complete the browser sign-in and consent flow. The plugin server may appear as `plugin:roost:roost`. Sign in to your own Roost account and review the access shown before approving it. No API key, client secret, or school password belongs in the plugin configuration or chat. Claude handles OAuth discovery and registration.

If you have not connected a school platform yet, open [Roost Courses](https://roostai.app/app/#/courses). Use [Connect AI](https://roostai.app/app/#/connect-ai) to manage Roost authorizations.

These instructions install from Roost's own repository marketplace. They do not indicate approval or inclusion in Anthropic's official plugin directory. Plugin and connector availability may be restricted by your Claude workspace administrator.

## Try it

Ask naturally or use one of the commands:

| Command | What it does |
| --- | --- |
| `/roost:upcoming` | Lists upcoming saved work and proposes a study plan in the conversation. |
| `/roost:assignment` | Reads a selected assignment and explains requirements or reviews an available draft. |
| `/roost:quiz` | Runs a practice session from retrieved coursework and saved notes. |

Three example prompts:

1. “Use Roost to find my unfinished assignments for the next seven days and help me plan what to study first.”
2. “Use Roost to read Homework 2 for my economics class. Explain what each question asks, and cite the instructions.”
3. “Quiz me on the notes saved for my biology class, one question at a time. Explain anything I miss.”

## What Roost can read

The connector exposes five tools: `list_courses`, `search`, `fetch`, `get_course_notes`, and `connection_status`. It retrieves coursework and notes from the Roost account you authorize.

The course roster comes from Course Site. Assignments saved from other platforms remain searchable, including work that is not under a current Course Site class. Supported Course Site documents can be read on demand using the school session already saved in Roost. Other platforms currently provide saved imported instructions and notes; this plugin does not read their live questions or attachments. Previously uploaded text is available when saved in Roost course notes.

Roost returns source links, read failures, and freshness or partial-excerpt labels so Claude can distinguish school documents from student notes. Saved assignment lists are an index, not a guarantee that every current school item is present. A proposed plan or quiz stays in the conversation: these tools cannot save plans, edit coursework, submit assignments, start assessment attempts, or change grades.

## Connection and data access

The hosted service is configured in `.mcp.json`:

```text
https://roost-connectors.chadwickboseman1675.workers.dev/mcp
```

Roost uses OAuth with dynamic client registration and the `coursework:read` scope. Retrieved coursework and notes become part of the Claude conversation in which you request them. You can revoke Roost authorization on [Connect AI](https://roostai.app/app/#/connect-ai). Revoking access does not remove material already included in a conversation.

The repository contains plugin instructions, a remote connection definition, and logo assets. It contains no Roost application source, bundled school sessions, account mapping, or credentials. The plugin does not install a local server or define executable hooks.

## Troubleshooting

| Symptom | Next step |
| --- | --- |
| Commands or tools are missing | Confirm Roost is installed and enabled in `/plugin`, then restart Claude Code. Check whether your workspace permits the plugin and remote server. |
| Roost needs authentication | Open `/mcp`, select Roost, and finish the sign-in and consent flow. |
| A school login has expired | Follow the Roost link returned by the tool, renew that connection in Roost Courses, and retry the assignment. |
| A document is unreadable, partial, or unsupported | Read the returned reason. Check the source and connection in Roost. Saved notes may still be usable, but they do not establish the unread document's requirements. |
| An assignment is missing | Check the class and search wording, search without the class filter if needed, and refresh coursework in Roost. Imported results can be incomplete. |
| A request is rate limited or temporarily unavailable | Wait before retrying and follow the returned recovery guidance; repeated immediate attempts will not repair a login or unreadable file. |

The assistant's browser does not share the saved school session in Roost. Opening a second school login is not the normal recovery path. Do not paste passwords, cookies, access tokens, or private coursework into a public issue.

## Support

Report plugin installation problems or suggestions in [GitHub Issues](https://github.com/chadwickboseman1675-stack/roost-claude-plugin/issues). Describe the step that failed and the error message with personal information removed. These issues are public: do not include student data, assignment contents, passwords, tokens, cookies, or other secrets. Manage account authorization and school connections inside Roost.

## Test a local copy

From a checkout of this repository:

```sh
claude plugin validate .claude-plugin/plugin.json
claude plugin validate .claude-plugin/marketplace.json
claude --plugin-dir .
```

The last command starts a Claude Code session with this local plugin; use `/mcp` to connect your own Roost account. Manifest validation checks packaging, not a completed account connection or the correctness of an answer. The plugin follows Claude's documented [plugin layout](https://code.claude.com/docs/en/plugins-reference), [marketplace format](https://code.claude.com/docs/en/plugin-marketplaces), and [remote MCP authorization](https://code.claude.com/docs/en/mcp#authenticate-with-remote-mcp-servers).
