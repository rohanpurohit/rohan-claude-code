---
description: Refactor and clean up code following best practices
model: claude-sonnet-4-5
---

Clean up and refactor the following code to improve readability, maintainability, and follow best practices.

## Code to Clean

$ARGUMENTS

## Cleanup Checklist

### 1. **Code Smells to Fix**

**Naming**
-  Descriptive variable/function names
-  Consistent naming conventions
-  Avoid abbreviations unless obvious
-  Boolean names start with is/has/can

**Functions**
-  Single responsibility per function
-  Keep functions small (<50 lines)
-  Reduce parameters (max 3-4)
-  Extract complex logic
-  Avoid side effects where possible

**DRY (Don't Repeat Yourself)**
-  Extract repeated code to utilities
-  Create reusable components/modules
-  Use generics for type reuse
-  Centralize constants/configuration

**Complexity**
-  Reduce nested if statements
-  Replace complex conditions with functions
-  Use early returns
-  Simplify boolean logic

### 2. **Modern Patterns by Language**

**Python**
```python
# Use dataclasses
from dataclasses import dataclass

@dataclass
class User:
    name: str
    email: str

# Use type hints
def process(data: list[dict]) -> list[str]:
    return [item["name"] for item in data]

# Use context managers
async with aiohttp.ClientSession() as session:
    async with session.get(url) as response:
        return await response.json()
```

**TypeScript/JavaScript**
```typescript
// Use optional chaining
const value = obj?.prop?.nested

// Use nullish coalescing
const result = value ?? defaultValue

// Use destructuring
const { name, email } = user

// Use proper types
interface Props {
  user: User
  onUpdate: (user: User) => void
}
```

**Go**
```go
// Use named returns for clarity
func divide(a, b int) (result int, err error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

// Use defer for cleanup
func processFile(path string) error {
    f, err := os.Open(path)
    if err != nil {
        return err
    }
    defer f.Close()
    // process file
}
```

**Rust**
```rust
// Use Result and Option properly
fn process(input: &str) -> Result<Output, Error> {
    let parsed = input.parse()?;
    Ok(transform(parsed))
}

// Use iterators
let result: Vec<_> = items
    .iter()
    .filter(|x| x.active)
    .map(|x| x.value)
    .collect();
```

**Dart/Flutter**
```dart
// Use const constructors
const MyWidget({super.key});

// Use null safety
final String? name = user?.name;
final displayName = name ?? 'Unknown';

// Use cascade notation
final user = User()
  ..name = 'John'
  ..email = 'john@example.com';
```

### 3. **Refactoring Techniques**

**Extract Function**
```python
# Before
def process():
    # 50 lines of code
    pass

# After
def validate(data): ...
def transform(data): ...
def save(data): ...

def process():
    validate(data)
    result = transform(data)
    save(result)
```

**Replace Conditional with Polymorphism**
```python
# Before
if type == 'A':
    return process_a()
elif type == 'B':
    return process_b()

# After
processors = {
    'A': process_a,
    'B': process_b
}
return processors[type]()
```

**Introduce Parameter Object**
```python
# Before
def create(name, email, age, address): ...

# After
@dataclass
class UserData:
    name: str
    email: str
    age: int
    address: str

def create(user_data: UserData): ...
```

### 4. **Common Cleanup Tasks**

**Remove Dead Code**
- Unused imports
- Unreachable code
- Commented out code
- Unused variables

**Improve Error Handling**
```python
# Before
try:
    do_something()
except Exception as e:
    print(e)

# After
try:
    do_something()
except ValidationError as e:
    logger.warning(f"Validation failed: {e}")
    raise HTTPException(status_code=400, detail=str(e))
except DatabaseError as e:
    logger.error(f"Database error: {e}")
    raise
```

**Consistent Formatting**
- Proper indentation
- Consistent quotes
- Line length limits
- Organized imports

**Better Comments**
- Remove obvious comments
- Add why, not what
- Document complex logic
- Update outdated comments

### 5. **Language-Specific Best Practices**

**Python**
- Use pathlib instead of os.path
- Use f-strings for formatting
- Use enumerate() instead of range(len())
- Use comprehensions appropriately

**Go**
- Handle all errors
- Use short variable declarations
- Group related declarations
- Use table-driven tests

**Rust**
- Use ? for error propagation
- Prefer &str over String when borrowing
- Use clippy suggestions
- Document public APIs

**Flutter**
- Extract widgets for reusability
- Use BuildContext correctly
- Dispose controllers properly
- Use const where possible

## Output Format

1. **Issues Found** - List of code smells and problems
2. **Cleaned Code** - Refactored version
3. **Explanations** - What changed and why
4. **Before/After Comparison** - Side-by-side if helpful
5. **Further Improvements** - Optional enhancements

Focus on practical improvements that make code more maintainable without over-engineering. Balance clean code with pragmatism.
