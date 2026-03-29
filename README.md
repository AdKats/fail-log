# FailLog

A Procon v2 plugin that logs game server crashes, layer disconnects, and Blaze dumps for Battlefield servers.

## Features

- **Server crash detection** -- detects game server restarts via uptime regression
- **Procon reconnect detection** -- logs when the Procon layer reconnects to the game server
- **Blaze disconnect detection** -- uses configurable player-count heuristics to identify EA/Blaze backend failures
- **Network congestion detection** -- flags excessive gaps between listPlayers responses
- **Optional file logging** -- writes failure events to a local log file
- **Optional web reporting** -- sends Blaze reports to a remote endpoint
- **Optional email alerts** -- sends SMTP email notifications on Blaze disconnects
- **Optional server restart** -- can issue `admin.shutDown` after a Blaze disconnect when no players remain

## Installation

Download the latest release from the [Releases](../../releases) page and place `FailLog.cs` in your Procon plugins directory.

## Configuration

All settings are configured through the Procon plugin interface:

| Section | Settings |
|---------|----------|
| **1 - Settings** | Debug level, file/web logging toggles, Blaze detection thresholds, restart and email toggles |
| **2 - Server Description** | Game type, provider, owner, region, Battlelog link (used in reports) |
| **3 - Email Settings** | SMTP configuration and email template (shown when email alerts are enabled) |

## Authors

- PapaCharlie9
- MorpheusX(AUT)

## License

This project is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details.

## Legacy Version

The original Procon v1 version is preserved on the `legacy` branch.
