# openclaw-schema

Community-maintained **JSON Schema** for [`openclaw.json`](https://docs.openclaw.ai/cli/config) — the configuration file for [OpenClaw](https://openclaw.ai).

## What this gives you

- ✅ **Red squiggles** on invalid keys in VS Code (zero setup if using SchemaStore)
- ✅ **Auto-complete** for channel names, log levels, enum values
- ✅ **Inline docs** on hover for every configuration key
- ✅ **CI validation** before gateway restarts

## Auto-detection (VS Code + SchemaStore)

Once this schema is merged into [SchemaStore](https://github.com/SchemaStore/schemastore), VS Code will automatically detect and validate any file named `openclaw.json`. No configuration needed.

## Manual setup (VS Code)

Add to `.vscode/settings.json` or your global VS Code settings:

```json
{
  "json.schemas": [
    {
      "fileMatch": ["**/openclaw.json", "~/.openclaw/openclaw.json"],
      "url": "https://raw.githubusercontent.com/aronchick/openclaw-schema/main/openclaw.schema.json"
    }
  ]
}
```

Or add `$schema` to your `openclaw.json` (note: verify your OpenClaw version accepts `$schema` at the root):

```json
{
  "$schema": "https://raw.githubusercontent.com/aronchick/openclaw-schema/main/openclaw.schema.json",
  "model": "anthropic/claude-sonnet-4-6"
}
```

## Schema URL

```
https://raw.githubusercontent.com/aronchick/openclaw-schema/main/openclaw.schema.json
```

## Status

This schema is **community-maintained** and inferred from real OpenClaw configs. It covers the primary configuration surface but may not include all valid keys — `additionalProperties: true` is used where the official schema is not fully known.

The upstream feature request to expose an official schema is tracked at:
👉 [openclaw/openclaw#22278](https://github.com/openclaw/openclaw/issues/22278)

## Contributing

If you find a key that's missing, wrong, or has an incorrect enum — please open a PR. The more real configs we can reference, the more accurate this gets.

Tested against OpenClaw `2026.2.19-2`.
