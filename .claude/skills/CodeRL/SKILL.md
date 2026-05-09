```markdown
# CodeRL Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill introduces the core development patterns and workflows used in the CodeRL repository, a TypeScript codebase focused on reinforcement learning and research project management. You'll learn about the project's coding conventions, how to maintain dependencies across multiple research projects, and the typical structure for tests and code organization.

## Coding Conventions

- **Language:** TypeScript
- **Framework:** None detected

### File Naming
- Use **camelCase** for file names.
  - Example: `myModule.ts`, `dataLoader.test.ts`

### Import Style
- Use **relative imports** for internal modules.
  - Example:
    ```typescript
    import { myFunction } from './utils';
    ```

### Export Style
- Use **named exports**.
  - Example:
    ```typescript
    export function myFunction() { /* ... */ }
    ```

### Commit Patterns
- Commit messages are freeform, with no strict prefix requirements.
- Average commit message length: ~56 characters.

## Workflows

### Update Python Dependencies Across Multiple Projects
**Trigger:** When someone wants to keep dependencies up to date across all research project examples.  
**Command:** `/update-dependencies`

1. Identify outdated dependencies in each project's `requirements.txt` file located at `transformers/examples/research_projects/*/requirements.txt`.
2. Update the version numbers for relevant packages (such as `transformers`, `torch`, `pytorch-lightning`, etc.) in each `requirements.txt`.
3. Commit all changed `requirements.txt` files together with a summary of updated packages.

**Example Workflow:**
```bash
# 1. Check for outdated dependencies
cd transformers/examples/research_projects/projectA
pip list --outdated

# 2. Edit requirements.txt to bump versions
nano requirements.txt

# 3. Repeat for each project, then commit changes
git add transformers/examples/research_projects/*/requirements.txt
git commit -m "Update dependencies: transformers, torch, etc."
```

## Testing Patterns

- **Framework:** Unknown (not detected)
- **Test File Pattern:** Files are named with `.test.` in the filename.
  - Example: `dataLoader.test.ts`
- Tests are likely colocated with source files or in parallel directory structures.

**Example Test File:**
```typescript
// dataLoader.test.ts
import { loadData } from './dataLoader';

test('loadData returns expected data', () => {
  const data = loadData();
  expect(data).toBeDefined();
});
```

## Commands

| Command               | Purpose                                                      |
|-----------------------|--------------------------------------------------------------|
| /update-dependencies  | Update Python package dependencies across all research projects |

```