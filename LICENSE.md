# Licensing — helmguild-plugins-public

This marketplace is the **public, community-licensed** sibling of the [private/commercial `helmguild-plugins`](https://github.com/helmut-hoffer-von-ankershoffen/helmguild-plugins) marketplace.

## Marketplace tooling

The tooling at the repo root — the validator, CI workflows, README, AGENTS.md, and `.claude-plugin/marketplace.json` itself — is **MIT-licensed**:

```
MIT License

Copyright © 2026 Helmut Hoffer von Ankershoffen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Plugin content

Every plugin under `plugins/` carries its **own** license file (`plugins/<plugin>/LICENSE.md`). The marketplace policy is:

- The plugin's `plugin.json` MUST declare `"commercial": false`.
- The plugin's `plugin.json` `license` field MUST be a recognised open license — typically `CC-BY-4.0` for skill bodies + `MIT` for bundled code. Other OSI-approved licenses are accepted with a rationale in the plugin's `README.md`.
- Plugins from the private/commercial `helmguild-plugins` marketplace MUST NOT be mirrored here, nor adapted into a derivative work for republishing here.

The validator enforces all three.
