# helmguild-plugins-public

The **public, community-licensed** marketplace of plugins for [helmguild](https://www.helmguild.com) mentors. Sibling repo to the private/commercial [`helmguild-plugins`](https://github.com/helmut-hoffer-von-ankershoffen/helmguild-plugins) marketplace.

Same shape — [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) catalogue + per-plugin `plugins/<name>/` folders following the [Claude Code plugin](https://code.claude.com/docs/en/plugins) and [AgentSkills](https://agentskills.io) conventions. The only differences are:

| Aspect           | `helmguild-plugins` (private)                                | `helmguild-plugins-public` (this repo)        |
| ---------------- | ------------------------------------------------------------ | ---------------------------------------------- |
| Visibility       | Private GitHub repo                                          | Public GitHub repo                             |
| Plugin license   | `LicenseRef-helmguild-mentoring-1.0` (proprietary)           | `CC-BY-4.0` / `MIT` (or other OSI-approved)    |
| `commercial`     | `true` on `marketplace.json` + every `plugin.json`           | `false` on `marketplace.json` + every plugin   |
| Distribution     | AMMP `GetPluginArchive` only                                 | `claude plugin marketplace add` + zip download |
| Active plugins   | All of Pepe's playbooks                                      | (empty — accepting contributions)              |

## Distribution

```sh
# Add this marketplace to Claude Code, then install any plugin from it.
claude plugin marketplace add helmut-hoffer-von-ankershoffen/helmguild-plugins-public
claude plugin install <plugin>@helmguild-plugins-public
```

Because this marketplace is public, the standard Claude-Code marketplace flow works directly — no Bearer token, no AMMP brokerage required.

## Contributing a community plugin

1. Open an issue describing what playbook your plugin would capture and why it's a fit for helmguild's mentor lineage.
2. After the issue is acked, fork + open a PR with:
   - `plugins/<plugin-name>/.claude-plugin/plugin.json` (sets `"commercial": false` and an OSI-approved `license`)
   - `plugins/<plugin-name>/skills/<id>/SKILL.md` (per AgentSkills format)
   - `plugins/<plugin-name>/LICENSE.md`, `README.md`
   - Bundled scripts under `scripts/` / `mcp-server/` must come with tests in `tests/` (same policy as the private marketplace).
3. The validator + test job runs on the PR. Once green, the marketplace entry in `.claude-plugin/marketplace.json` is added in the same PR.

## See also

- [Private/commercial sibling marketplace `helmguild-plugins`](https://github.com/helmut-hoffer-von-ankershoffen/helmguild-plugins) — Pepe Arturo's playbooks, distributed only inside active mentor/mentee engagements via AMMP `GetPluginArchive`.
- [AMMP — Agentic Mentor-Mentee Protocol](https://www.helmguild.com/rfc/ammp/) — the IETF Internet-Draft both marketplaces' plugins reference via their `.mcp.json`.
- [ammp-mcp](https://github.com/helmut-hoffer-von-ankershoffen/ammp-mcp) — the reference AMMP server implementation.
- [agentskills.io](https://agentskills.io) — the open SKILL format every plugin in both marketplaces conforms to.
- [Claude Code plugins](https://code.claude.com/docs/en/plugins) + [marketplaces](https://code.claude.com/docs/en/plugin-marketplaces) — the runtime plugin convention.
