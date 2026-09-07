# Changelog

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.0.0] - 2026-08-21

### Added

- Added datasource to retrieve and select from Exchange accepted domains
- Room mailboxes now support explicit alias specification during creation
- Implemented three separate validation datasources for enhanced uniqueness checking:
  - Display Name uniqueness validation
  - Alias uniqueness validation
  - Email address uniqueness validation
- Added line-level error reporting with script line numbers for improved troubleshooting
- Added explicit command list (`New-Mailbox`, `Set-Mailbox`) for session import to optimize resource usage

### Changed

- Renamed all connector files to include standardized prefix `exchange-on-premises-roommailbox-create` for better organization
- Email addresses are now constructed from user-entered prefix and selected domain instead of full address input
- Enhanced form structure to separate email prefix and domain selection
- Increased generated password length from 10 to 22 characters for improved security
- Restructured error handling with comprehensive try-catch-finally blocks and detailed audit logging
- Improved Exchange session creation and cleanup with explicit command imports and proper disconnection in all scenarios
- Replaced single combined validation datasource with three specialized validation datasources for better user feedback

### Removed

- Removed old `CheckMailboxName` and `EmailAddress` datasources (replaced with granular validation datasources)
- Removed single-datasource validation approach in favor of separate, purpose-specific validations

### Fixed

- Ensured Exchange sessions are properly disconnected even when errors occur, preventing resource leaks
- Standardized variable naming conventions across all scripts for consistency
- Corrected audit log message formatting for consistent tracking across all operations

## [1.0.2] - 2022-08-22

### Added

- Added version number and updated code for SA-agent and auditlogging

## [1.0.1] - 2021-11-16

### Added

- Added version number and updated all-in-one script

## [1.0.0] - 2021-04-29

Initial release of HelloID-Conn-SA-Full-Exchange-On-Premises-Roommailbox-Create.

### Added

- Initial release for creating Exchange On-Premises Room Mailboxes
- Basic room mailbox creation functionality
- Display name and email address validation
- Integration with HelloID Service Automation
