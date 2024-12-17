---
title: "Contributing to the Project"
nav_order: 8
parent: "Smart Control Project Documentation"
---

# Contributing to the Project

## Coding Standards

- **Style Guide**: Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) for Python code.
- **Type Annotations**: Use type hints throughout the code for better readability and tooling support.
- **Docstrings**: Include docstrings for all modules, classes, and functions using the Google Python Style Guide.
- **Naming Conventions**:
  - Use descriptive names for variables, functions, and classes.
  - Class names should follow `CamelCase`.
  - Function and variable names should be in `snake_case`.

## Development Workflow

1. **Branching**:

   - Create a new branch for each feature or bug fix.
   - Branch names should be descriptive, e.g., `feature/add-new-reward-function`.

2. **Writing Tests**:

   - Write unit tests for new features and bug fixes.
   - Use `unittest` or `pytest` frameworks.
   - Place tests in the `tests` directory, mirroring the module structure.

3. **Commits**:

   - Make small, atomic commits with clear commit messages.
   - Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification if possible.

4. **Pull Requests**:

   - Submit pull requests to the `main` branch when ready.
   - Include a detailed description of changes and any related issues.

5. **Code Review**:

   - Participate in code reviews for peers.
   - Be constructive and focus on improving code quality.

## Testing

- **Unit Tests**:

  - Ensure high test coverage across modules.
  - Tests should be independent and repeatable.

- **Integration Tests**:

  - Test interactions between modules, especially environment and reward functions.

- **Continuous Integration**:

  - Use CI tools like GitHub Actions or Jenkins to automate testing on each commit or pull request.

---

[Back to Home](../index.md)
