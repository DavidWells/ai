---
description: Enforce shorthand truthiness/falsiness checking and boolean naming conventions for cleaner, more readable code
globs: "**/*.{js,ts,jsx,tsx}"
alwaysApply: false
---

# Enforce Shorthand Truthiness

**Your task: Review JavaScript/TypeScript code and identify places where explicit comparisons are used, then suggest shorthand truthiness/falsiness patterns for cleaner, more idiomatic code.**

Follow this process:

1. **Identify Explicit Comparison Patterns:**
   - Look for `if` statements with explicit boolean checks: `if (variable === true)`, `if (variable !== false)`
   - Find comparisons to undefined/null: `if (variable !== undefined)`, `if (variable !== null)`
   - Detect empty string checks: `if (variable !== '')`, `if (variable.length > 0)`
   - Spot zero comparisons: `if (variable !== 0)`, `if (variable > 0)`
   - Find verbose logical operations: `variable === true && action()`
   - Locate explicit ternary comparisons: `variable === true ? true : false`

2. **Analyze Appropriateness:**
   - Ensure the variable is intended for truthiness checking
   - Verify that shorthand won't introduce bugs (e.g., `0` vs `false` distinction)
   - Consider if the explicit comparison serves a specific purpose

3. **Suggest Shorthand Patterns:**
   - Replace `if (variable === true)` with `if (variable)`
   - Replace `if (variable !== false)` with `if (variable)`
   - Replace `if (variable !== undefined)` with `if (variable)`
   - Replace `if (variable !== null)` with `if (variable)`
   - Replace `if (variable !== '')` with `if (variable)`
   - If array, Replace `if (variable.length > 0)` with `if (variable.length)`
   - Replace `if (variable !== 0)` with `if (variable)` (when appropriate)

**Guidelines:**
- Prefer shorthand truthiness for cleaner, more idiomatic JavaScript
- Use `if (variable)` instead of `if (variable === true)`
- Use `if (!variable)` instead of `if (variable === false)`
- Use `variable && action()` instead of `variable === true && action()`
- Use `variable || fallback` instead of `variable !== undefined ? variable : fallback`
- Only suggest shorthand when it doesn't change the logical behavior

**Target Patterns (What We Want):**

```javascript
// Boolean variables in if statements
if (isEnabled) {
  doSomething()
}

// String variables (truthy check)
if (userName) {
  greetUser()
}

// Number variables (truthy check)
if (count) {
  processItems()
}

// While loops
while (isRunning) {
  process()
}

// Do-while loops
do {
  work()
} while (hasMore)

// Logical operations
isReady && execute()
hasPermission || showError()

// Ternary operators
const result = isSuccess ? "OK" : "Error"

// Negation
if (!isDisabled) {
  run()
}
```

**Replace These Verbose Patterns:**

```javascript
// Replace explicit boolean checks:
if (isEnabled === true) { ... }
if (isEnabled !== false) { ... }

// Replace undefined/null checks:
if (userName !== undefined) { ... }
if (userName !== null) { ... }

// Replace empty string checks:
if (userName !== '') { ... }
if (userName.length > 0) { ... }

// Replace zero checks (when appropriate):
if (count !== 0) { ... }
if (count > 0) { ... }

// Replace verbose logical operations:
isEnabled === true && execute()
hasPermission !== false || showError()

// Replace explicit ternary comparisons:
const result = isSuccess === true ? "OK" : "Error"
const result = isSuccess !== false ? "OK" : "Error"
```

**Notes:**
- **This is primarily about variable naming**: Well-named boolean variables like `isEnabled`, `hasPermission`, `isReady` naturally read better with shorthand truthiness
- Shorthand truthiness is more idiomatic in JavaScript when variables are properly named
- Variables with boolean-like names (`is*`, `has*`, `can*`, `should*`) are perfect candidates for shorthand
- Be cautious with numbers where `0` might be a valid value
- Consider if the explicit comparison was intentional for edge cases
- Falsy values: `false`, `0`, `""`, `null`, `undefined`, `NaN`
- Truthy values: everything else, including `"0"`, `"false"`, `[]`, `{}`
- **Good variable naming makes shorthand truthiness self-documenting**: `if (userIsLoggedIn)` reads like English
