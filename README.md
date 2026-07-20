# Notifications

Multi-project notification service for desktop apps.

Each project in this repo has its own directory with a `notifications.json` file.
Clients fetch the JSON from GitHub raw URLs and render notifications based on
version matching and display rules.

## Quick Start

1. Add a directory for your project: `mkdir <project-name>`
2. Create `notifications.json` inside it (see [schema.json](schema.json))
3. Commit and push

Client apps configure the URL:
```
https://raw.githubusercontent.com/iFishin/notifications/main/<project>/notifications.json
```

## Projects

| Project | Description | URL |
|---|---|---|
| [scom-t](./scom-t/notifications.json) | SCOM-T Serial Command Tool | [raw](https://raw.githubusercontent.com/iFishin/notifications/main/scom-t/notifications.json) |

## Notification Format

```json
[
  {
    "id": "v0.3-upgrade",
    "title": "v0.3.0 Released",
    "body": "Please upgrade to the latest version.",
    "severity": "important",
    "date": "2026-07-20",
    "link": "https://github.com/iFishin/SCOM-T/releases",
    "minVersion": "0.1.0.0",
    "maxVersion": "0.2.9.9999",
    "display": "once"
  }
]
```

See [schema.json](schema.json) for the full field reference.

## Tips

- **Branch for environments**: `main` = production, use other branches for testing
- **Archive old notifications**: move to `<project>/archive/` to keep the main file clean
- **Multi-language**: create `<project>/notifications.zh.json` per locale