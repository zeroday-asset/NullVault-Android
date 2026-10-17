# NullVault Android

A fork of Bitwarden Android. Upstream history, license, and attribution are retained.

## Foundation

- Initial upstream commit: 1470154cf3d3d0511cdbe5bfc6493971b6478edf.
- Preserve upstream password-manager functionality and self-hosted server configuration.
- Use the F-Droid variant as the development baseline.
- Baseline validation: :app:testFdroidDebugUnitTest and :app:assembleFdroidDebug.
- The baseline still uses upstream branding and application identity. It is not a NullVault release.

## Product direction

Encrypted vaults are available on-device while offline. Optional synchronization uses a privately operated, compatible server. Standalone account-free vault creation is an additional development goal; it does not exist in the baseline.

Retain existing autofill, inline suggestions, credential-provider integration, folders, search, generators, import/export, and vault settings. Features that require a server or platform support retain those requirements.

NullVault-specific additions:

- Launch an installed app from its androidapp:// URI; offer a store fallback only when missing.
- Copy a password and switch to its associated app or website.
- A repository URL field on entries.
- Import the existing NullVault preview format without losing folders, URL lists, or OTP data.

## Migration

The existing zeroday-asset/NullVault repository and Preview3 app remain available during development. Do not replace their encrypted storage with the upstream format in place. Establish a tested export/import path before migrating real vaults.

Assign this fork its own application ID and persistent signing key before producing a NullVault-branded APK. Do not use the upstream checked-in debug key for a release containing real user vaults.

## Stages

1. Verify the unchanged upstream baseline in this fork.
2. Set NullVault identity and establish repeatable signing.
3. Validate self-hosted sync and offline unlock across devices with synthetic credentials.
4. Add and test the preview migration and custom launch behavior.
5. Add standalone local vault creation while preserving the server-backed path.

No private server is deployed by this repository bootstrap. End-to-end sync and device autofill require separate runtime validation.
