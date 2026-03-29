# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Changed
- Moved source to `src/` directory
- Converted code style to System types (`String`, `Int32`, `Boolean`, etc.)
- Added `.editorconfig` and `FailLog.csproj` for CI format checks
- Added CI and release GitHub Actions workflows
- Added `CLAUDE.md`, `README.md`, `CHANGELOG.md`, `LICENSE`, `.gitignore`
- Stripped BOM, converted to UTF-8 with LF line endings

## [1.1.0.0] - Legacy

- Last release for Procon v1 (see `legacy` branch)
- Blaze disconnect detection with configurable heuristics
- File logging, web reporting, and email notifications
- Server restart on Blaze disconnect
- Plugin update checker
