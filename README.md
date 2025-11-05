# .github

This is a special `.github` repository for the `danielsan` GitHub account. It provides shared resources that can be used across all repositories under `github.com/danielsan`.

## Repository Structure

```
.github/
├── workflows/          # Shared reusable workflows
│   ├── reusable-test.yml
│   ├── reusable-lint.yml
│   └── reusable-build.yml
└── agents/            # Reusable custom agents
    ├── CodeReviewer.agent.md
    ├── DocumentationWriter.agent.md
    └── TestEngineer.agent.md
```

## Shared Workflows

### Using Reusable Workflows

To use a shared workflow from another repository under `danielsan`, reference it in your workflow file:

```yaml
name: CI

on: [push, pull_request]

jobs:
  lint:
    uses: danielsan/.github/workflows/reusable-lint.yml@main
    with:
      node-version: '20'

  test:
    uses: danielsan/.github/workflows/reusable-test.yml@main
    with:
      node-version: '20'

  build:
    uses: danielsan/.github/workflows/reusable-build.yml@main
    with:
      node-version: '20'
      build-command: 'npm run build'
```

### Available Workflows

#### reusable-test.yml
Runs tests for Node.js projects.

**Inputs:**
- `node-version` (optional): Node.js version to use (default: '18')
- `working-directory` (optional): Working directory (default: '.')

**Secrets:**
- `token` (optional): GitHub token for authentication

#### reusable-lint.yml
Runs linting for Node.js projects.

**Inputs:**
- `node-version` (optional): Node.js version to use (default: '18')
- `working-directory` (optional): Working directory (default: '.')
- `lint-command` (optional): Lint command to run (default: 'npm run lint')

#### reusable-build.yml
Builds Node.js projects and uploads artifacts.

**Inputs:**
- `node-version` (optional): Node.js version to use (default: '18')
- `working-directory` (optional): Working directory (default: '.')
- `build-command` (optional): Build command to run (default: 'npm run build')
- `artifact-path` (optional): Path to the build output directory (default: 'dist')

## Custom Agents

Custom agents are AI-powered assistants with specialized knowledge for specific tasks. They are defined in `.agent.md` files under `.github/agents/`.

### Available Agents

#### CodeReviewer.agent.md
Expert code reviewer focused on:
- Code quality and maintainability
- Best practices and design patterns
- Performance and security
- Test coverage and documentation

#### DocumentationWriter.agent.md
Technical documentation specialist for:
- README files and API documentation
- User guides and tutorials
- Code comments and architecture decisions
- Contributing guidelines

#### TestEngineer.agent.md
Test engineering expert for:
- Unit, integration, and e2e tests
- Test strategy and design
- Test automation best practices
- Coverage and quality

### Using Custom Agents

Custom agents can be invoked by GitHub Copilot or other tools that support custom agent definitions. The agents provide specialized guidance and can perform tasks within their domain of expertise.

## Contributing

To add new shared workflows or custom agents:

1. **Workflows**: Add `.yml` files to `.github/workflows/`
2. **Agents**: Add `.agent.md` files to `.github/agents/`
3. Follow the naming convention: `AgentName.agent.md` for agents
4. Update this README to document new additions

## Resources

- [GitHub Reusable Workflows Documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Community Health Files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)