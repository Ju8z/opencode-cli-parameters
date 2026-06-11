# OpenCode CLI Configuration Parameters (opencode.json)

OpenCode is an advanced, open-source AI coding agent designed to operate autonomously within your terminal. It assists developers by analyzing codebases, executing terminal commands, managing files, and interfacing directly with Language Server Protocols (LSPs) to automate complex engineering tasks.

The opencode.json file serves as the primary configuration engine for the OpenCode CLI. It allows developers to completely customize the agent's behavior—from defining custom LLM providers, model limits, and token budgets, to establishing granular file-system permissions, setting up Model Context Protocol (MCP) integrations, and crafting bespoke subagent personas.

Note: The configuration parameters detailed in this document are applicable to OpenCode release v1.17.3 : https://github.com/anomalyco/opencode/releases/tag/v1.17.3

| Parameter (JSON Path) | Type | Description / Usage |
| :--- | :--- | :--- |
| `shell` | `string` | Default shell to use for terminal and bash tool |
| `logLevel` | `enum` | Log level Options: "DEBUG", "INFO", "WARN", "ERROR". |
| `server` | `object` | Server configuration for opencode serve and web commands |
| `server.port` | `integer` | Port to listen on |
| `server.hostname` | `string` | Hostname to listen on |
| `server.mdns` | `boolean` | Enable mDNS service discovery |
| `server.mdnsDomain` | `string` | Custom domain name for mDNS service (default: opencode.local) |
| `server.cors` | `array<string>` | Additional domains to allow for CORS |
| `server.cors[i]` | `string` |  |
| `command` | `object` | Command configuration, see https://opencode.ai/docs/commands |
| `command.<dynamic_key>.template` | `string` |  |
| `command.<dynamic_key>.description` | `string` |  |
| `command.<dynamic_key>.agent` | `string` |  |
| `command.<dynamic_key>.model` | `string` | Model identifier (external schema reference). |
| `command.<dynamic_key>.variant` | `string` |  |
| `command.<dynamic_key>.subtask` | `boolean` |  |
| `skills` | `object` | Additional skill folder paths |
| `skills.paths` | `array<string>` | Additional paths to skill folders |
| `skills.paths[i]` | `string` |  |
| `skills.urls` | `array<string>` | URLs to fetch skills from (e.g., https://example.com/.well-known/skills/) |
| `skills.urls[i]` | `string` |  |
| `references` | `object` | Named git or local directory references |
| `references.<dynamic_key>` | `string | object |
| `references.<dynamic_key>.repository` | `string` |  |
| `references.<dynamic_key>.branch` | `string` |  |
| `references.<dynamic_key>.description` | `string` |  |
| `references.<dynamic_key>.hidden` | `boolean` |  |
| `references.<dynamic_key>.path` | `string` |  |
| `reference` | `object` | @deprecated Use 'references' field instead. Named git or local directory references |
| `reference.<dynamic_key>` | `string | object |
| `reference.<dynamic_key>.repository` | `string` |  |
| `reference.<dynamic_key>.branch` | `string` |  |
| `reference.<dynamic_key>.description` | `string` |  |
| `reference.<dynamic_key>.hidden` | `boolean` |  |
| `reference.<dynamic_key>.path` | `string` |  |
| `watcher.ignore` | `array<string>` |  |
| `watcher.ignore[i]` | `string` |  |
| `snapshot` | `boolean` | Enable or disable snapshot tracking. When false, filesystem snapshots are not recorded and undoing or reverting will not undo/redo file changes. Defaults to true. |
| `plugin` | `array<any>` |  |
| `plugin[i]` | `string | array` |
| `share` | `enum` | Control sharing behavior:'manual' allows manual sharing via commands, 'auto' enables automatic sharing, 'disabled' disables all sharing Options: "manual", "auto", "disabled". |
| `autoshare` | `boolean` | @deprecated Use 'share' field instead. Share newly created sessions automatically |
| `autoupdate` | `boolean | string` |
| `disabled_providers` | `array<string>` | Disable providers that are loaded automatically |
| `disabled_providers[i]` | `string` |  |
| `enabled_providers` | `array<string>` | When set, ONLY these providers will be enabled. All other providers will be ignored |
| `enabled_providers[i]` | `string` |  |
| `model` | `string` | Model identifier (external schema reference). |
| `small_model` | `string` | Model identifier (external schema reference). |
| `default_agent` | `string` | Default agent to use when none is specified. Must be a primary agent. Falls back to 'build' if not set or if the specified agent is invalid. |
| `username` | `string` | Custom username to display in conversations instead of system username |
| `mode` | `object` | @deprecated Use `agent` field instead. |
| `mode.build.model` | `string` | Model identifier (external schema reference). |
| `mode.build.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `mode.build.temperature` | `number` |  |
| `mode.build.top_p` | `number` |  |
| `mode.build.prompt` | `string` |  |
| `mode.build.tools` | `object` | @deprecated Use 'permission' field instead |
| `mode.build.tools.<dynamic_key>` | `boolean` |  |
| `mode.build.disable` | `boolean` |  |
| `mode.build.description` | `string` | Description of when to use the agent |
| `mode.build.mode` | `enum` | Options: "subagent", "primary", "all". |
| `mode.build.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `mode.build.color` | `string | string` |
| `mode.build.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `mode.build.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `mode.build.permission` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.read` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.list` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.task` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.build.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `mode.build.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.model` | `string` | Model identifier (external schema reference). |
| `mode.plan.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `mode.plan.temperature` | `number` |  |
| `mode.plan.top_p` | `number` |  |
| `mode.plan.prompt` | `string` |  |
| `mode.plan.tools` | `object` | @deprecated Use 'permission' field instead |
| `mode.plan.tools.<dynamic_key>` | `boolean` |  |
| `mode.plan.disable` | `boolean` |  |
| `mode.plan.description` | `string` | Description of when to use the agent |
| `mode.plan.mode` | `enum` | Options: "subagent", "primary", "all". |
| `mode.plan.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `mode.plan.color` | `string | string` |
| `mode.plan.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `mode.plan.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `mode.plan.permission` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.read` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.list` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.task` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.plan.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `mode.plan.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.model` | `string` | Model identifier (external schema reference). |
| `mode.<dynamic_key>.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `mode.<dynamic_key>.temperature` | `number` |  |
| `mode.<dynamic_key>.top_p` | `number` |  |
| `mode.<dynamic_key>.prompt` | `string` |  |
| `mode.<dynamic_key>.tools` | `object` | @deprecated Use 'permission' field instead |
| `mode.<dynamic_key>.tools.<dynamic_key>` | `boolean` |  |
| `mode.<dynamic_key>.disable` | `boolean` |  |
| `mode.<dynamic_key>.description` | `string` | Description of when to use the agent |
| `mode.<dynamic_key>.mode` | `enum` | Options: "subagent", "primary", "all". |
| `mode.<dynamic_key>.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `mode.<dynamic_key>.color` | `string | string` |
| `mode.<dynamic_key>.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `mode.<dynamic_key>.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `mode.<dynamic_key>.permission` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.read` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.list` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.task` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `mode.<dynamic_key>.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent` | `object` | Agent configuration, see https://opencode.ai/docs/agents |
| `agent.plan.model` | `string` | Model identifier (external schema reference). |
| `agent.plan.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.plan.temperature` | `number` |  |
| `agent.plan.top_p` | `number` |  |
| `agent.plan.prompt` | `string` |  |
| `agent.plan.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.plan.tools.<dynamic_key>` | `boolean` |  |
| `agent.plan.disable` | `boolean` |  |
| `agent.plan.description` | `string` | Description of when to use the agent |
| `agent.plan.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.plan.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.plan.color` | `string | string` |
| `agent.plan.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.plan.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.plan.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.plan.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.plan.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.model` | `string` | Model identifier (external schema reference). |
| `agent.build.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.build.temperature` | `number` |  |
| `agent.build.top_p` | `number` |  |
| `agent.build.prompt` | `string` |  |
| `agent.build.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.build.tools.<dynamic_key>` | `boolean` |  |
| `agent.build.disable` | `boolean` |  |
| `agent.build.description` | `string` | Description of when to use the agent |
| `agent.build.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.build.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.build.color` | `string | string` |
| `agent.build.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.build.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.build.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.build.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.build.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.model` | `string` | Model identifier (external schema reference). |
| `agent.general.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.general.temperature` | `number` |  |
| `agent.general.top_p` | `number` |  |
| `agent.general.prompt` | `string` |  |
| `agent.general.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.general.tools.<dynamic_key>` | `boolean` |  |
| `agent.general.disable` | `boolean` |  |
| `agent.general.description` | `string` | Description of when to use the agent |
| `agent.general.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.general.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.general.color` | `string | string` |
| `agent.general.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.general.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.general.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.general.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.general.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.model` | `string` | Model identifier (external schema reference). |
| `agent.explore.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.explore.temperature` | `number` |  |
| `agent.explore.top_p` | `number` |  |
| `agent.explore.prompt` | `string` |  |
| `agent.explore.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.explore.tools.<dynamic_key>` | `boolean` |  |
| `agent.explore.disable` | `boolean` |  |
| `agent.explore.description` | `string` | Description of when to use the agent |
| `agent.explore.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.explore.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.explore.color` | `string | string` |
| `agent.explore.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.explore.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.explore.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.explore.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.explore.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.model` | `string` | Model identifier (external schema reference). |
| `agent.title.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.title.temperature` | `number` |  |
| `agent.title.top_p` | `number` |  |
| `agent.title.prompt` | `string` |  |
| `agent.title.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.title.tools.<dynamic_key>` | `boolean` |  |
| `agent.title.disable` | `boolean` |  |
| `agent.title.description` | `string` | Description of when to use the agent |
| `agent.title.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.title.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.title.color` | `string | string` |
| `agent.title.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.title.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.title.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.title.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.title.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.model` | `string` | Model identifier (external schema reference). |
| `agent.summary.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.summary.temperature` | `number` |  |
| `agent.summary.top_p` | `number` |  |
| `agent.summary.prompt` | `string` |  |
| `agent.summary.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.summary.tools.<dynamic_key>` | `boolean` |  |
| `agent.summary.disable` | `boolean` |  |
| `agent.summary.description` | `string` | Description of when to use the agent |
| `agent.summary.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.summary.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.summary.color` | `string | string` |
| `agent.summary.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.summary.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.summary.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.summary.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.summary.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.model` | `string` | Model identifier (external schema reference). |
| `agent.compaction.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.compaction.temperature` | `number` |  |
| `agent.compaction.top_p` | `number` |  |
| `agent.compaction.prompt` | `string` |  |
| `agent.compaction.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.compaction.tools.<dynamic_key>` | `boolean` |  |
| `agent.compaction.disable` | `boolean` |  |
| `agent.compaction.description` | `string` | Description of when to use the agent |
| `agent.compaction.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.compaction.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.compaction.color` | `string | string` |
| `agent.compaction.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.compaction.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.compaction.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.compaction.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.model` | `string` | Model identifier (external schema reference). |
| `agent.<dynamic_key>.variant` | `string` | Default model variant for this agent (applies only when using the agent's configured model). |
| `agent.<dynamic_key>.temperature` | `number` |  |
| `agent.<dynamic_key>.top_p` | `number` |  |
| `agent.<dynamic_key>.prompt` | `string` |  |
| `agent.<dynamic_key>.tools` | `object` | @deprecated Use 'permission' field instead |
| `agent.<dynamic_key>.tools.<dynamic_key>` | `boolean` |  |
| `agent.<dynamic_key>.disable` | `boolean` |  |
| `agent.<dynamic_key>.description` | `string` | Description of when to use the agent |
| `agent.<dynamic_key>.mode` | `enum` | Options: "subagent", "primary", "all". |
| `agent.<dynamic_key>.hidden` | `boolean` | Hide this subagent from the @ autocomplete menu (default: false, only applies to mode: subagent) |
| `agent.<dynamic_key>.color` | `string | string` |
| `agent.<dynamic_key>.steps` | `integer` | Maximum number of agentic iterations before forcing text-only response |
| `agent.<dynamic_key>.maxSteps` | `integer` | @deprecated Use 'steps' field instead. |
| `agent.<dynamic_key>.permission` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.read` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.edit` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.glob` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.grep` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.list` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.bash` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.task` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.skill` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `agent.<dynamic_key>.permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `provider` | `object` | Custom provider configurations and model overrides |
| `provider.<dynamic_key>.api` | `string` |  |
| `provider.<dynamic_key>.name` | `string` |  |
| `provider.<dynamic_key>.env` | `array<string>` |  |
| `provider.<dynamic_key>.env[i]` | `string` |  |
| `provider.<dynamic_key>.id` | `string` |  |
| `provider.<dynamic_key>.npm` | `string` |  |
| `provider.<dynamic_key>.whitelist` | `array<string>` |  |
| `provider.<dynamic_key>.whitelist[i]` | `string` |  |
| `provider.<dynamic_key>.blacklist` | `array<string>` |  |
| `provider.<dynamic_key>.blacklist[i]` | `string` |  |
| `provider.<dynamic_key>.options.apiKey` | `string` |  |
| `provider.<dynamic_key>.options.baseURL` | `string` |  |
| `provider.<dynamic_key>.options.enterpriseUrl` | `string` | GitHub Enterprise URL for copilot authentication |
| `provider.<dynamic_key>.options.setCacheKey` | `boolean` | Enable promptCacheKey for this provider (default false) |
| `provider.<dynamic_key>.options.timeout` | `integer | boolean` |
| `provider.<dynamic_key>.options.headerTimeout` | `integer | boolean` |
| `provider.<dynamic_key>.options.chunkTimeout` | `integer` | Timeout in milliseconds between streamed SSE chunks for this provider. If no chunk arrives within this window, the request is aborted. |
| `provider.<dynamic_key>.models.<dynamic_key>.id` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.name` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.family` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.release_date` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.attachment` | `boolean` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.reasoning` | `boolean` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.temperature` | `boolean` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.tool_call` | `boolean` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.interleaved` | `boolean | object` |
| `provider.<dynamic_key>.models.<dynamic_key>.interleaved.field` | `enum` | Options: "reasoning", "reasoning_content", "reasoning_details". |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.input` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.output` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.cache_read` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.cache_write` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.context_over_200k.input` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.context_over_200k.output` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.context_over_200k.cache_read` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.cost.context_over_200k.cache_write` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.limit.context` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.limit.input` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.limit.output` | `number` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.modalities.input` | `array<string>` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.modalities.input[i]` | `enum` | Options: "text", "audio", "image", "video", "pdf". |
| `provider.<dynamic_key>.models.<dynamic_key>.modalities.output` | `array<string>` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.modalities.output[i]` | `enum` | Options: "text", "audio", "image", "video", "pdf". |
| `provider.<dynamic_key>.models.<dynamic_key>.experimental` | `boolean` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.status` | `enum` | Options: "alpha", "beta", "deprecated", "active". |
| `provider.<dynamic_key>.models.<dynamic_key>.provider.npm` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.provider.api` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.headers.<dynamic_key>` | `string` |  |
| `provider.<dynamic_key>.models.<dynamic_key>.variants` | `object` | Variant-specific configuration |
| `provider.<dynamic_key>.models.<dynamic_key>.variants.<dynamic_key>.disabled` | `boolean` | Disable this variant for the model |
| `mcp` | `object` | MCP (Model Context Protocol) server configurations |
| `mcp.<dynamic_key>` | `object` |  |
| `mcp.<dynamic_key>.enabled` | `boolean` |  |
| `formatter` | `boolean | object` |
| `formatter.<dynamic_key>.disabled` | `boolean` |  |
| `formatter.<dynamic_key>.command` | `array<string>` |  |
| `formatter.<dynamic_key>.command[i]` | `string` |  |
| `formatter.<dynamic_key>.environment.<dynamic_key>` | `string` |  |
| `formatter.<dynamic_key>.extensions` | `array<string>` |  |
| `formatter.<dynamic_key>.extensions[i]` | `string` |  |
| `lsp` | `boolean | object` |
| `lsp.<dynamic_key>` | `object | object` |
| `lsp.<dynamic_key>.disabled` | `enum` | Options: true. |
| `lsp.<dynamic_key>.command` | `array<string>` |  |
| `lsp.<dynamic_key>.command[i]` | `string` |  |
| `lsp.<dynamic_key>.extensions` | `array<string>` |  |
| `lsp.<dynamic_key>.extensions[i]` | `string` |  |
| `lsp.<dynamic_key>.env.<dynamic_key>` | `string` |  |
| `instructions` | `array<string>` | Additional instruction files or patterns to include |
| `instructions[i]` | `string` |  |
| `layout` | `enum` | @deprecated Always uses stretch layout. Options: "auto", "stretch". |
| `permission` | `object | Options: "ask", "allow", "deny". |
| `permission.read` | `object | Options: "ask", "allow", "deny". |
| `permission.read.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.edit` | `object | Options: "ask", "allow", "deny". |
| `permission.edit.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.glob` | `object | Options: "ask", "allow", "deny". |
| `permission.glob.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.grep` | `object | Options: "ask", "allow", "deny". |
| `permission.grep.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.list` | `object | Options: "ask", "allow", "deny". |
| `permission.list.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.bash` | `object | Options: "ask", "allow", "deny". |
| `permission.bash.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.task` | `object | Options: "ask", "allow", "deny". |
| `permission.task.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.external_directory` | `object | Options: "ask", "allow", "deny". |
| `permission.external_directory.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.todowrite` | `enum` | Options: "ask", "allow", "deny". |
| `permission.question` | `enum` | Options: "ask", "allow", "deny". |
| `permission.webfetch` | `enum` | Options: "ask", "allow", "deny". |
| `permission.websearch` | `enum` | Options: "ask", "allow", "deny". |
| `permission.lsp` | `object | Options: "ask", "allow", "deny". |
| `permission.lsp.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.doom_loop` | `enum` | Options: "ask", "allow", "deny". |
| `permission.skill` | `object | Options: "ask", "allow", "deny". |
| `permission.skill.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `permission.<dynamic_key>` | `object | Options: "ask", "allow", "deny". |
| `permission.<dynamic_key>.<dynamic_key>` | `enum` | Options: "ask", "allow", "deny". |
| `tools.<dynamic_key>` | `boolean` |  |
| `attachment` | `object` | Attachment processing configuration, including image size limits and resizing behavior |
| `attachment.image` | `object` | Image attachment configuration |
| `attachment.image.auto_resize` | `boolean` | Resize images before sending them to the model when they exceed configured limits (default: true) |
| `attachment.image.max_width` | `integer` | Maximum image width before resizing or rejecting the attachment (default: 2000) |
| `attachment.image.max_height` | `integer` | Maximum image height before resizing or rejecting the attachment (default: 2000) |
| `attachment.image.max_base64_bytes` | `integer` | Maximum base64 payload bytes for an image attachment (default: 5242880) |
| `enterprise.url` | `string` | Enterprise URL |
| `tool_output` | `object` | Thresholds for truncating tool output. When output exceeds either limit, the full text is written to the truncation directory and a preview is returned. |
| `tool_output.max_lines` | `integer` | Maximum lines of tool output before it is truncated and saved to disk (default: 2000) |
| `tool_output.max_bytes` | `integer` | Maximum bytes of tool output before it is truncated and saved to disk (default: 51200) |
| `compaction.auto` | `boolean` | Enable automatic compaction when context is full (default: true) |
| `compaction.prune` | `boolean` | Enable pruning of old tool outputs (default: false) |
| `compaction.tail_turns` | `integer` | Number of recent user turns, including their following assistant/tool responses, to keep verbatim during compaction (default: 2) |
| `compaction.preserve_recent_tokens` | `integer` | Maximum number of tokens from recent turns to preserve verbatim after compaction |
| `compaction.reserved` | `integer` | Token buffer for compaction. Leaves enough window to avoid overflow during compaction. |
| `experimental.disable_paste_summary` | `boolean` |  |
| `experimental.batch_tool` | `boolean` | Enable the batch tool |
| `experimental.openTelemetry` | `boolean` | Enable OpenTelemetry spans for AI SDK calls (using the 'experimental_telemetry' flag) |
| `experimental.primary_tools` | `array<string>` | Tools that should only be available to primary agents. |
| `experimental.primary_tools[i]` | `string` |  |
| `experimental.continue_loop_on_deny` | `boolean` | Continue the agent loop when a tool call is denied |
| `experimental.mcp_timeout` | `integer` | Timeout in milliseconds for model context protocol (MCP) requests |
| `experimental.policies` | `array<object>` | Policy statements applied to supported resources, such as provider access |
| `experimental.policies[i].action` | `` |  |
| `experimental.policies[i].effect` | `enum` | Options: "allow", "deny". |
| `experimental.policies[i].resource` | `string` |  |

