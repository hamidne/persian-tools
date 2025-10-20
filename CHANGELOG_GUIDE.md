# Changelog Guidelines

This guide helps contributors and maintainers keep the CHANGELOG.md file organized and useful.

## Format

We follow [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) format with [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Structure

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- New features

### Changed
- Changes in existing functionality

### Deprecated
- Soon-to-be removed features

### Removed
- Removed features

### Fixed
- Bug fixes

### Security
- Security fixes

## [1.0.0] - 2024-01-01

### Added
- Initial release
```

## Categories

### Added
For new features or functionality.

```markdown
### Added
- New `slugify` function for URL-safe Persian text conversion (#123)
- Support for Arabic-Indic digits in `digitsToFa` function (#124)
```

### Changed
For changes in existing functionality.

```markdown
### Changed
- Improved performance of `verifyCardNumber` by 30% (#125)
- Updated `numberToWords` to handle larger numbers up to trillion (#126)
```

### Deprecated
For soon-to-be removed features.

```markdown
### Deprecated
- `oldFunctionName` is deprecated, use `newFunctionName` instead (#127)
  - Will be removed in version 5.0.0
```

### Removed
For removed features.

```markdown
### Removed
- Removed deprecated `oldFunction` (deprecated in v3.0.0) (#128)
- Dropped support for Node.js 12 (#129)
```

### Fixed
For bug fixes.

```markdown
### Fixed
- Fixed `verifyIranianNationalId` validation for IDs starting with zero (#130)
- Corrected `timeAgo` calculation for edge cases (#131)
```

### Security
For security fixes (in case of vulnerabilities).

```markdown
### Security
- Fixed ReDoS vulnerability in phone number validation regex (#132)
```

## Entry Format

Each entry should:

1. **Be concise but descriptive**
   - ✅ Good: "Add support for Persian ordinal numbers in `numberToWords`"
   - ❌ Bad: "Update function"

2. **Reference the PR or issue**
   - Format: `(#123)` where 123 is the PR/issue number
   - Example: "Fix validation bug in national ID checker (#456)"

3. **Use imperative mood** (like git commits)
   - ✅ Good: "Add", "Fix", "Update", "Remove"
   - ❌ Bad: "Added", "Fixed", "Updating"

4. **Include breaking changes prominently**
   ```markdown
   ### Changed
   - **BREAKING**: `functionName` now requires options object as second parameter (#789)
     - Migration guide: See UPGRADING.md
   ```

## Unreleased Section

Keep an `[Unreleased]` section at the top for ongoing development:

```markdown
## [Unreleased]

### Added
- Feature X (#123)

### Fixed
- Bug Y (#124)
```

When releasing:
1. Change `[Unreleased]` to the version number with date
2. Add links at the bottom
3. Create a new `[Unreleased]` section

## Version Number Guidelines

Follow [Semantic Versioning](https://semver.org/):

- **Major (X.0.0)**: Breaking changes
- **Minor (0.X.0)**: New features, backward compatible
- **Patch (0.0.X)**: Bug fixes, backward compatible

Examples:
- `4.0.0` → `4.1.0`: Added new function
- `4.1.0` → `4.1.1`: Fixed a bug
- `4.1.1` → `5.0.0`: Breaking API change

## Examples

### Good Changelog Entry

```markdown
## [4.1.0] - 2024-03-15

### Added
- New `analyzeText` function for comprehensive Persian text analysis (#234)
  - Provides statistics, language detection, and readability metrics
  - See documentation for full API details
- Support for Jalali calendar in `timeAgo` function (#235)

### Changed
- Improved `extractCardNumber` performance for large texts by 50% (#236)
- Updated `isPersian` to better handle mixed Persian-English content (#237)

### Fixed
- Fixed `verifyCardNumber` false positives for specific bank codes (#238)
- Corrected `wordsToNumber` handling of negative numbers (#239)

### Security
- Updated dependencies to address CVE-2024-XXXXX (#240)
```

### Bad Changelog Entry

```markdown
## [4.1.0]

- Added stuff
- Fixed things
- Updated code
```

## Before Release Checklist

- [ ] Move all `[Unreleased]` entries to new version section
- [ ] Add release date in YYYY-MM-DD format
- [ ] Verify all entries have PR/issue references
- [ ] Check that breaking changes are marked with **BREAKING**
- [ ] Ensure version follows semantic versioning
- [ ] Add comparison links at the bottom
- [ ] Create new empty `[Unreleased]` section

## Comparison Links

At the bottom of CHANGELOG.md:

```markdown
[Unreleased]: https://github.com/persian-tools/persian-tools/compare/v4.1.0...HEAD
[4.1.0]: https://github.com/persian-tools/persian-tools/compare/v4.0.0...v4.1.0
[4.0.0]: https://github.com/persian-tools/persian-tools/compare/v3.9.0...v4.0.0
```

## Automated Tools

We use `standard-version` for changelog automation:

```bash
# Automatically bump version and update CHANGELOG
npm run release

# For beta releases
npm run release:beta
```

This will:
- Analyze conventional commits
- Bump version appropriately
- Update CHANGELOG.md
- Create a git tag

## Tips

1. **Update CHANGELOG in your PR**: Add your changes to `[Unreleased]` section
2. **One entry per PR**: If fixing multiple things, list them separately
3. **User perspective**: Write for users, not developers
4. **Link to docs**: Reference documentation for complex features
5. **Credit contributors**: Mention contributors when appropriate

## Questions?

See [Keep a Changelog FAQ](https://keepachangelog.com/en/1.0.0/#frequently-asked-questions) or ask in [GitHub Discussions](https://github.com/persian-tools/persian-tools/discussions).
