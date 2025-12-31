---
description: Run linting and fix code quality issues
model: claude-sonnet-4-5
---

Run linting and fix code quality issues in the codebase.

## Target

$ARGUMENTS

## Lint Strategy

### 1. **Run Linting Commands**

**Python**
```bash
# Ruff (fast, recommended)
ruff check . --fix
ruff format .

# Or traditional tools
flake8 .
black .
isort .
mypy .
```

**JavaScript/TypeScript**
```bash
npm run lint
npx eslint . --fix
npx prettier --write .
npx tsc --noEmit
```

**Go**
```bash
go fmt ./...
go vet ./...
golangci-lint run --fix
staticcheck ./...
```

**Rust**
```bash
cargo fmt
cargo clippy --fix
cargo check
```

**Flutter/Dart**
```bash
dart fix --apply
dart format .
flutter analyze
```

**Kotlin**
```bash
ktlint --format
detekt
```

### 2. **Common Issues by Language**

**Python**
- Missing type hints
- Unused imports
- Line too long (>88 chars)
- Missing docstrings
- Incorrect indentation

**TypeScript/JavaScript**
- Missing type annotations
- `any` types used
- Unused variables
- Missing return types
- Console.log statements

**Go**
- Unused variables/imports
- Missing error handling
- Shadowed variables
- Ineffective assignments
- Missing comments on exports

**Rust**
- Unused variables/imports
- Unnecessary clones
- Missing documentation
- Clippy warnings
- Unused Results

**Dart/Flutter**
- Unused imports
- Missing const constructors
- Avoid print() in production
- Prefer final for unchanging values

### 3. **Auto-Fix What You Can**

**Safe Auto-Fixes**
- Import ordering/removal
- Formatting (indentation, spacing)
- Simple type annotations
- Trailing whitespace
- Line endings

**Manual Fixes Needed**
- Complex type annotations
- Logic errors
- Missing error handling
- Security issues

### 4. **Lint Configuration Examples**

**Python (pyproject.toml)**
```toml
[tool.ruff]
line-length = 88
select = ["E", "F", "W", "I", "UP", "B"]

[tool.mypy]
strict = true
```

**TypeScript (.eslintrc.json)**
```json
{
  "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended"],
  "rules": {
    "@typescript-eslint/no-explicit-any": "error",
    "@typescript-eslint/no-unused-vars": "error"
  }
}
```

**Go (.golangci.yml)**
```yaml
linters:
  enable:
    - gofmt
    - govet
    - errcheck
    - staticcheck
```

**Rust (clippy.toml)**
```toml
cognitive-complexity-threshold = 25
```

### 5. **Priority Fixes**

**High Priority** (fix immediately)
- Type errors blocking build
- Security vulnerabilities
- Runtime errors
- Broken functionality

**Medium Priority** (fix before commit)
- Missing type annotations
- Unused variables
- Code style violations
- TODO comments

**Low Priority** (fix when convenient)
- Formatting inconsistencies
- Comment improvements
- Minor refactoring opportunities

### 6. **Pre-Commit Hooks** (Recommended)

**Python (pre-commit-config.yaml)**
```yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    hooks:
      - id: ruff
      - id: ruff-format
```

**JavaScript (Husky + lint-staged)**
```json
{
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": ["eslint --fix", "prettier --write"]
  }
}
```

**Go**
```bash
# In .git/hooks/pre-commit
go fmt ./...
go vet ./...
```

## What to Generate

1. **Lint Report** - All issues found
2. **Auto-Fix Results** - What was automatically fixed
3. **Manual Fix Suggestions** - Issues requiring manual intervention
4. **Priority List** - Ordered by severity
5. **Configuration Recommendations** - Improve lint setup

Focus on fixes that improve code quality and prevent bugs. Run linting before every commit.
