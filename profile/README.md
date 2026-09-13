
**A Flutter ecosystem an AI coding agent can operate:** a utility-first styling framework, an app framework, a CLI, an end-to-end driver and a runtime inspector.

An agent writing Flutter code cannot see the app it just built. It guesses at the widget tree, never taps a button, and never reads the exception it caused. Artisan, Dusk and Telescope each ship a stdio MCP server, so the agent works from the running app instead of from a guess.

## Wind

Tailwind CSS for Flutter. Write `className` strings, get optimised widget trees.

```dart
// Flutter native
Container(
  padding: EdgeInsets.all(24),
  margin: EdgeInsets.symmetric(horizontal: 16),
  decoration: BoxDecoration(
    color: Colors.white,
    borderRadius: BorderRadius.circular(12),
    boxShadow: [BoxShadow(color: Colors.black.withOpacity(0.1), blurRadius: 10, offset: Offset(0, 4))],
  ),
  child: Text('Hello', style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold)),
)

// Wind
WDiv(
  className: 'p-6 mx-4 bg-white dark:bg-gray-800 rounded-xl shadow-lg',
  child: WText('Hello', className: 'text-xl font-bold'),
)
```

```bash
flutter pub add fluttersdk_wind
```

The Flutter team looked at the same problem. In the [Decorators experiment](https://github.com/flutter/flutter/issues/161345) they wrote that "the source code can be a bit verbose due to heavy nesting", ran 3 rounds of user studies with 8 participants, and closed it with "we've decided not to move forward with the decorators experiment". Their experiment chained modifiers onto a widget. Wind takes the other route: utility strings parsed into a widget tree, so the styling stays declarative and the tree stays flat.

[![pub downloads](https://img.shields.io/pub/dm/fluttersdk_wind?label=downloads&color=2ea44f)](https://pub.dev/packages/fluttersdk_wind)
[![pub points](https://img.shields.io/pub/points/fluttersdk_wind?label=pub%20points)](https://pub.dev/packages/fluttersdk_wind/score)
[![pub version](https://img.shields.io/pub/v/fluttersdk_wind?label=version)](https://pub.dev/packages/fluttersdk_wind)

W-prefix widgets, a parser per utility family, a themeable token set, dark mode, responsive prefixes and the `WindRecipe` variant primitives. [Documentation](https://fluttersdk.com/wind)

## The rest of the ecosystem

| Package | What it is | Downloads | Quality |
| --- | --- | --- | --- |
| [**Artisan**](https://github.com/fluttersdk/artisan) | Composable Dart CLI framework and stdio MCP server. Scaffolding, code generation, transactional plugin installs, hot reload and a REPL in one binary. | [![pub downloads](https://img.shields.io/pub/dm/fluttersdk_artisan?label=&color=2ea44f)](https://pub.dev/packages/fluttersdk_artisan) | [![pub points](https://img.shields.io/pub/points/fluttersdk_artisan?label=)](https://pub.dev/packages/fluttersdk_artisan/score) |
| [**Dusk**](https://github.com/fluttersdk/dusk) | End-to-end driver. Taps, snaps and screenshots a live app over VM Service, the way Playwright drives a browser. | [![pub downloads](https://img.shields.io/pub/dm/fluttersdk_dusk?label=&color=2ea44f)](https://pub.dev/packages/fluttersdk_dusk) | [![pub points](https://img.shields.io/pub/points/fluttersdk_dusk?label=)](https://pub.dev/packages/fluttersdk_dusk/score) |
| [**Telescope**](https://github.com/fluttersdk/telescope) | Passive runtime inspector. Captures HTTP, logs, exceptions and DB queries and surfaces them to the CLI and the agent. Debug-only, zero release overhead. | [![pub downloads](https://img.shields.io/pub/dm/fluttersdk_telescope?label=&color=2ea44f)](https://pub.dev/packages/fluttersdk_telescope) | [![pub points](https://img.shields.io/pub/points/fluttersdk_telescope?label=)](https://pub.dev/packages/fluttersdk_telescope/score) |
| [**Magic**](https://github.com/fluttersdk/magic) | The Laravel experience for Flutter. Facades, Eloquent ORM, service providers, IoC container. Alpha. | [![pub downloads](https://img.shields.io/pub/dm/magic?label=&color=2ea44f)](https://pub.dev/packages/magic) | [![pub version](https://img.shields.io/pub/v/magic?label=)](https://pub.dev/packages/magic) |

Wind's CI runs OpenSSF Scorecard and [`zizmor`](https://github.com/zizmorcore/zizmor), so the supply chain of a package you depend on is inspectable.

## Magic plugins

[Starter kit](https://github.com/fluttersdk/magic_starter) · [Notifications](https://github.com/fluttersdk/magic_notifications) · [Social auth](https://github.com/fluttersdk/magic_social_auth) · [Deep links](https://github.com/fluttersdk/magic_deeplink) · [Payments](https://github.com/fluttersdk/magic_payments) · [DevTools](https://github.com/fluttersdk/magic_devtools)

## Teach your agent

[**fluttersdk/ai**](https://github.com/fluttersdk/ai) is the shared store for the ecosystem's skills, rules and MCP wiring. One command in Claude Code:

```
/plugin marketplace add fluttersdk/ai
/plugin install fluttersdk@fluttersdk-marketplace
```

Or `npx skills add fluttersdk/ai --skill wind-ui`, which reaches Cursor, OpenCode, Copilot, Codex, Cline and 40+ other agents.

That gets you two things. The **skill** teaches the `className` grammar and the framework conventions, loaded into context before the first line is written. The **docs MCP server** at `mcp.fluttersdk.com` answers `search-docs` across all five packages over streamable HTTP, public and with no auth, so an agent can look up what it does not already hold.

A flat markdown inventory also sits at [`/wind/llms.txt`](https://fluttersdk.com/wind/llms.txt) and the same path under `/magic`, `/dusk`, `/telescope` and `/artisan`, if you would rather point your agent at a URL than install anything.

[How it fits together](https://fluttersdk.com/wind/ai)

## The platform

[**fluttersdk.com**](https://fluttersdk.com) is a cloud IDE with live preview, AI generation and deployment, pre-configured with Magic and Wind. Currently in closed beta.

---

Maintained by [Anılcan Çakır](https://github.com/anilcancakir). Documentation at [fluttersdk.com](https://fluttersdk.com), issues on the individual repositories.
