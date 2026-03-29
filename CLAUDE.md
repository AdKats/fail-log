# FailLog — Procon v2 Plugin

## Project Overview

FailLog is a C# plugin for Procon v2 (Battlefield game server administration) that logs game server crashes, layer disconnects, and Blaze dumps. The legacy Procon v1 version lives on the `legacy` branch.

- **Language:** C#
- **License:** GPLv3
- **Authors:** PapaCharlie9, MorpheusX(AUT)
- **Supported games:** BF3, BF4 (any Frostbite game supported by Procon)
- **Dependencies:** None (only Procon v2 runtime)

## Architecture

Single-file plugin: `src/FailLog.cs` contains the main `FailLog` class (extends `PRoConPluginAPI`, implements `IPRoConPluginInterface`) and a static utility class `FailLogUtils`.

### Key functionality
- Detects game server restarts via uptime regression in `OnServerInfo`
- Detects Procon reconnects via `OnLogin` events
- Detects Blaze disconnects via player count heuristics in `OnListPlayers`
- Detects network congestion via listPlayers timing gaps
- Optionally logs to file, web endpoint, and email on Blaze events
- Optionally restarts game server via `admin.shutDown` after Blaze disconnect
- Tracks server configuration changes for inclusion in Blaze reports

## Code Style

Style is enforced by `.editorconfig` and checked via `dotnet format` in CI.

**Critical conventions:**
- **Use `String`, `Int32`, `Boolean`, `Double`** — NOT `string`, `int`, `bool`, `double`. The codebase uses explicit System type names everywhere.
- **Allman brace style** — opening brace on its own line
- **4 spaces** for indentation, LF line endings
- **Block-scoped namespaces** (not file-scoped)
- **`using` directives outside namespace**, System usings first

## Build & CI

- `FailLog.csproj` at root is a **CI-only artifact** for `dotnet format`. It is NOT a real build file — Procon v2 assemblies are unavailable for compilation.
- **CI workflow** (`.github/workflows/ci.yml`): runs on push to `master` and PRs. Checks `dotnet format whitespace` and `dotnet format style --exclude-diagnostics IDE1007`.
- **Release workflow** (`.github/workflows/release.yml`): triggered by `v*` tags. Packages `.cs` files from `src/` into a zip and creates a GitHub Release.

### Running style checks locally

```bash
dotnet restore
dotnet format whitespace --verify-no-changes
dotnet format style --verify-no-changes --severity warn --exclude-diagnostics IDE1007
```

## Branch Structure

- `master` — current development, Procon v2 only
- `legacy` — archived Procon v1 version, no longer maintained
