# Contributing to Persian Tools

Thank you for your interest in contributing to Persian Tools! We welcome contributions from the community and are grateful for your support.

## Code of Conduct

This project adheres to the [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [ali_4286@live.com](mailto:ali_4286@live.com).

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the [issue tracker](https://github.com/persian-tools/persian-tools/issues) as you might find that the issue has already been reported.

When creating a bug report, include as many details as possible:

- **Use a clear and descriptive title**
- **Describe the exact steps to reproduce the problem**
- **Provide specific examples** (code snippets, test cases)
- **Describe the behavior you observed** and what you expected
- **Include system information** (OS, Node.js version, Persian Tools version)
- **Add screenshots or error messages** if applicable

Use the [bug report template](.github/ISSUE_TEMPLATE/bug_report.md) when creating issues.

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear and descriptive title**
- **Provide a detailed description** of the proposed feature
- **Explain why this enhancement would be useful** to most users
- **List some examples** of how it would be used
- **Include code examples** if applicable

Use the [feature request template](.github/ISSUE_TEMPLATE/feature_request.md).

### Your First Code Contribution

Unsure where to begin? Look for issues labeled:

- `good first issue` - Simple issues perfect for newcomers
- `help wanted` - Issues where we need community help
- `documentation` - Improvements to documentation

### Pull Requests

Follow these steps to submit a pull request:

1. **Fork the repository** and create your branch from `master`
2. **Install dependencies**: `npm install` or `bun install`
3. **Make your changes** following our coding standards
4. **Add tests** for any new functionality
5. **Run the test suite**: `npm test`
6. **Run the linter**: `npm run lint`
7. **Ensure the build passes**: `npm run build`
8. **Update documentation** if needed
9. **Commit your changes** using conventional commits
10. **Push to your fork** and submit a pull request

## Development Setup

### Prerequisites

- **Node.js** >= 14.x (or Bun >= 1.0.0)
- **npm** >= 7.0.0 (or equivalent package manager)
- **Git** for version control

### Setup Instructions

```bash
# Clone your fork
git clone https://github.com/YOUR-USERNAME/persian-tools.git
cd persian-tools

# Install dependencies
npm install
# or with Bun
bun install

# Run tests
npm test

# Run tests in watch mode
npm run test:watch

# Build the project
npm run build

# Run linter
npm run lint

# Fix linting issues automatically
npm run lint:fix
```

## Coding Standards

### TypeScript Guidelines

- **Use TypeScript**: All code must be written in TypeScript
- **Strict mode**: We use strict TypeScript settings
- **Type everything**: Avoid `any` type; use `unknown` when necessary
- **Export types**: Export types for public APIs
- **Document functions**: Use JSDoc comments for public functions

Example:

```typescript
/**
 * Converts Persian digits to English digits
 * @param input - Text containing Persian digits
 * @returns Text with English digits
 * @throws {TypeError} When input is not a string
 * 
 * @example
 * ```typescript
 * persianToEnglishDigits('۱۲۳'); // '123'
 * ```
 */
export function persianToEnglishDigits(input: string): string {
  if (typeof input !== 'string') {
    throw new TypeError('Input must be a string');
  }
  // Implementation...
}
```

### Code Style

We use ESLint and Prettier to maintain consistent code style:

- **Indentation**: Tabs (configured in .editorconfig)
- **Quotes**: Single quotes for strings
- **Semicolons**: Required
- **Line length**: Maximum 120 characters
- **Naming conventions**:
  - `camelCase` for functions and variables
  - `PascalCase` for types and interfaces
  - `UPPER_CASE` for constants

Run `npm run format` to auto-format your code.

### Testing

- **Write tests** for all new features and bug fixes
- **Use descriptive test names** that explain what is being tested
- **Test edge cases**: empty strings, null, undefined, special characters
- **Aim for high coverage**: We target >90% code coverage
- **Use Vitest**: Our test framework of choice

Test structure example:

```typescript
describe('functionName', () => {
  describe('valid inputs', () => {
    it('should handle basic case', () => {
      expect(functionName('input')).toBe('expected');
    });
  });

  describe('invalid inputs', () => {
    it('should throw error for invalid input', () => {
      expect(() => functionName('')).toThrow('Invalid input');
    });
  });

  describe('edge cases', () => {
    it('should handle empty string', () => {
      expect(functionName('')).toBe('');
    });
  });
});
```

### Persian Language Considerations

When working with Persian text:

- Understand **Persian vs Arabic** character differences
- Handle **RTL (right-to-left)** text properly
- Use **ZWNJ (zero-width non-joiner)** correctly for half-spaces
- Support both **Persian and Arabic-Indic** digit systems
- Test with **real Persian text** and edge cases

See [Persian Language Guide](.github/instructions/persian-language.instructions.md) for details.

## Commit Message Guidelines

We follow [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, semicolons, etc.)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `ci`: CI/CD changes
- `build`: Build system changes

### Examples

```
feat(digits): add support for Arabic-Indic digits

Add conversion functions for Arabic-Indic digits to Persian and English.

Closes #123
```

```
fix(national-id): correct validation for edge cases

Fix validation logic to properly handle national IDs starting with zero.

Fixes #456
```

### Breaking Changes

Breaking changes should be indicated with `BREAKING CHANGE:` in the footer:

```
feat(api)!: change function signature

BREAKING CHANGE: The function now requires an options object as second parameter
```

## Pull Request Process

1. **Update documentation**: Update README.md if you add/change features
2. **Add tests**: All tests must pass (`npm test`)
3. **Follow coding standards**: Lint must pass (`npm run lint`)
4. **Build successfully**: Build must complete (`npm run build`)
5. **Update CHANGELOG**: Add entry for significant changes
6. **Describe your changes**: Use the pull request template
7. **Link related issues**: Reference any related issues
8. **Request review**: At least one maintainer must approve
9. **Resolve conflicts**: Keep your branch up to date with master
10. **Be patient**: We'll review as soon as possible!

### PR Checklist

Before submitting, verify:

- [ ] All tests pass (`npm test`)
- [ ] Linter passes (`npm run lint`)
- [ ] Build succeeds (`npm run build`)
- [ ] Type checking passes (`npm run test:types`)
- [ ] Documentation is updated
- [ ] Tests are added for new features
- [ ] Commit messages follow conventions
- [ ] No breaking changes (or clearly documented)
- [ ] Code follows project style guide

## Project Structure

```
persian-tools/
├── src/               # Source code
│   ├── modules/      # Feature modules
│   └── index.ts      # Main entry point
├── test/             # Test files
├── .github/          # GitHub configuration
│   ├── workflows/    # CI/CD workflows
│   └── ISSUE_TEMPLATE/ # Issue templates
├── docs/             # Documentation
└── website/          # Website source
```

## Release Process

Releases are managed by project maintainers:

1. Version bump using `npm run release`
2. Update CHANGELOG.md
3. Create GitHub release
4. Publish to npm

## Getting Help

- **Documentation**: Read the [README](README.md) and [API docs](https://persian-tools.usestrict.dev)
- **Issues**: Search [existing issues](https://github.com/persian-tools/persian-tools/issues)
- **Discussions**: Ask questions in [GitHub Discussions](https://github.com/persian-tools/persian-tools/discussions)
- **Email**: Contact maintainers at [ali_4286@live.com](mailto:ali_4286@live.com)

## Recognition

Contributors are automatically added to:

- [CONTRIBUTORS.md](CONTRIBUTORS.md)
- README.md contributors section (via all-contributors bot)

Thank you for contributing to Persian Tools! 🙏
