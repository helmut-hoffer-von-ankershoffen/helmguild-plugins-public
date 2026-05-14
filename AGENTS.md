# AGENTS.md — `helmguild-plugins-public`

Operator guide for the **public, community-licensed** sibling of `helmguild-plugins`. Same shape; different distribution + license posture.

## What this is

The **open** marketplace of plugins for helmguild mentors. Anyone can `claude plugin marketplace add helmut-hoffer-von-ankershoffen/helmguild-plugins-public` and install from here. The plugins published here are licensed under standard open licenses (`CC-BY-4.0` for skill bodies, `MIT` for bundled code is the canonical pair) and carry `"commercial": false` on `marketplace.json` + every `plugin.json`.

The **private** sibling marketplace lives at <https://github.com/helmut-hoffer-von-ankershoffen/helmguild-plugins>. Plugins there carry the proprietary Helmguild Mentoring License and are distributed exclusively through AMMP `GetPluginArchive` inside an active mentor/mentee engagement.

## Invariants the validator enforces

`.github/scripts/validate.py` runs on every push / PR and exits non-zero on any of:

1. `.claude-plugin/marketplace.json` is missing, doesn't parse, or references a plugin folder that doesn't exist.
2. **`metadata.commercial: false`** and **`metadata.distribution: "public"`** on the marketplace.
3. Each plugin entry on the marketplace must carry `"commercial": false`.
4. Each `plugins/<name>/.claude-plugin/plugin.json` must:
   - declare an OSI-approved `license` (one of `CC-BY-4.0`, `CC-BY-SA-4.0`, `MIT`, `Apache-2.0`, `BSD-2-Clause`, `BSD-3-Clause`, `ISC`);
   - declare `"commercial": false`.
5. Each plugin folder must ship a `LICENSE.md`.
6. Each `SKILL.md` must have valid AgentSkills frontmatter.
7. Each plugin's `.mcp.json`, if present, must parse.
8. Any bundled script under `scripts/` or `mcp-server/` must have a matching test under `tests/test-<dir>-<stem>.{sh,mjs}`, and the test must be executable. (Same policy as the private sibling.)

The `test-bundled-scripts` CI job walks every plugin's `tests/`, runs `.mjs` via `node --test` and `.sh` via `bash`, and fails on any non-zero exit.

## Adding a plugin

Open an issue first describing the playbook intent + why it fits helmguild's mentor lineage. After ack, open a PR that drops:

```
plugins/<plugin>/
├── .claude-plugin/plugin.json    # commercial=false, OSI license, version
├── .mcp.json                      # optional — wire to AMMP if mentor-backed
├── skills/<id>/SKILL.md           # AgentSkills frontmatter + body
├── scripts/                       # optional — each script needs a test
├── mcp-server/                    # optional — each .mjs needs a test
├── tests/                         # required iff scripts/ or mcp-server/ exists
├── LICENSE.md
└── README.md
```

…and adds the matching entry to `.claude-plugin/marketplace.json`. Validator + test job must be green before merge.

## See also

- [Private sibling: `helmguild-plugins`](https://github.com/helmut-hoffer-von-ankershoffen/helmguild-plugins) — commercial plugins, AMMP-distribution.
- [Private sibling's AGENTS.md](https://github.com/helmut-hoffer-von-ankershoffen/helmguild-plugins/blob/main/AGENTS.md) — full plugin authoring patterns (most of which apply identically here).
- [AMMP draft](https://www.helmguild.com/rfc/ammp/), [agentskills.io](https://agentskills.io), [Claude Code plugins](https://code.claude.com/docs/en/plugins).
