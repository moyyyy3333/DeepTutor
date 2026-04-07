```markdown
# DeepTutor Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns and conventions used in the DeepTutor Python codebase. You'll learn about file and code organization, import/export styles, commit message habits, and how to write and run tests. This guide is designed to help contributors quickly adapt to the project's established practices.

## Coding Conventions

### File Naming
- Use **snake_case** for all file names.
  - Example: `deep_tutor_engine.py`, `user_session_manager.py`

### Import Style
- Use **relative imports** within the package.
  - Example:
    ```python
    from .utils import load_data
    from .models import TutorModel
    ```

### Export Style
- Use **named exports** (explicitly list what is exported).
  - Example:
    ```python
    __all__ = ['TutorModel', 'load_data']
    ```

### Commit Messages
- Freeform style, no enforced prefixes.
- Average message length: ~79 characters.
- Example:
  ```
  Add support for multi-step reasoning in the tutor engine
  ```

## Workflows

### Adding a New Module
**Trigger:** When you need to add a new feature or component.
**Command:** `/add-module`

1. Create a new Python file using snake_case (e.g., `new_feature.py`).
2. Implement your module, using relative imports for dependencies.
3. Add named exports via `__all__` if needed.
4. Write corresponding tests in a file named `new_feature.test.py`.
5. Commit your changes with a clear, descriptive message.

### Writing and Running Tests
**Trigger:** When you add or modify code.
**Command:** `/run-tests`

1. Create or update test files using the pattern: `*.test.py`.
2. Write test functions for your new or changed code.
3. Use the project's preferred (unknown) test framework to run tests.
   - If unsure, try running: `python -m unittest discover` or similar.
4. Ensure all tests pass before committing.

### Refactoring or Updating Imports
**Trigger:** When reorganizing code or resolving import issues.
**Command:** `/update-imports`

1. Use relative imports for all intra-package dependencies.
2. Update any absolute imports to relative where appropriate.
3. Test the module to ensure imports resolve correctly.

## Testing Patterns

- Test files follow the pattern: `*.test.py`
  - Example: `session_manager.test.py`
- Each test file should focus on one module or component.
- The testing framework is not explicitly specified; likely uses standard Python testing tools.
- Example test structure:
  ```python
  import unittest
  from .session_manager import SessionManager

  class TestSessionManager(unittest.TestCase):
      def test_create_session(self):
          sm = SessionManager()
          self.assertIsNotNone(sm.create_session('user1'))
  ```

## Commands
| Command         | Purpose                                      |
|-----------------|----------------------------------------------|
| /add-module     | Scaffold and add a new module or feature     |
| /run-tests      | Run all tests in the codebase                |
| /update-imports | Refactor imports to match project conventions|
```
