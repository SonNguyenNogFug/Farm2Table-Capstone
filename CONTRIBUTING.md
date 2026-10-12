# Contributing to Farm2Table

This document explains how team members contribute to the Farm2Table Capstone project.

The project is currently in the planning and setup phase. Development tools and technical requirements will be updated as the team makes decisions.

## Issues & Planning

- Use GitHub Issues to track tasks, bugs, and feature requests.
- Each issue should have a description, an assigned member, and a target completion date.
- The Project Manager is responsible for keeping the task board updated and tracking sprint progress.
- Team members should communicate blockers through Discord.

## Commit Messages

- Write short, descriptive commit messages that explain the changes.
- Suggested format: `type: description`.

Examples:
- `feat: add sensor station markers`
- `fix: correct map display`
- `docs: update README`
- `test: add API tests`

- Reference related GitHub Issues when applicable.

## Code Style, Linting & Formatting

- Use clear and descriptive names for variables, functions, and files.
- Keep code readable and consistent with existing conventions.
- Avoid unnecessary complexity and unrelated changes.
- The team has not finalized the technology stack, formatter, or linter.
- Once selected, the Quality Owner will document the configuration files and local linting commands here.

## Testing

- Test changes before submitting a pull request.
- Add or update tests for new features and bug fixes when the testing framework is available.
- Until automated tests are configured, describe manual testing steps in the pull request.
- The Quality Owner will coordinate the testing setup.
- Testing commands and coverage requirements will be documented once the team selects the framework.

## Definition of Done

A contribution is considered complete when:

- The work meets its assigned requirements and acceptance criteria.
- The changes have been reviewed by another team member.
- Relevant testing has been completed and documented.
- Related documentation has been updated when necessary.
- No secrets or sensitive information are exposed.
- Required automated checks pass once CI is configured.

### Planned Quality Checks

The following checks are not yet implemented:

| Check | Planned Enforcement | Owner | Target Sprint |
|---|---|---|---|
| Code review | GitHub PR approval | Quality Owner | TBD |
| Documentation | PR review checklist | Documentation Owner | TBD |
| Linting | CI lint job | Quality Owner | TBD |
| Automated tests | CI test job | Quality Owner | TBD |
| Security checks | Secret/dependency scanning | Quality Owner | TBD |
| Merge checks | GitHub branch protection | Quality Owner | TBD |

The Quality Owner will work with the team to select the tools, confirm implementation sprints, and document the exact CI configuration.

## Contribution Norm

- Every team member must complete at least one accepted contribution per sprint.
- Contributions may include coding, testing, documentation, design, research, deployment, or other approved project work.
- Work should be tracked through GitHub Issues, pull requests, or linked shared documents.
- Code contributions are accepted when reviewed and merged into the repository.
- Documentation and design contributions are accepted when reviewed and approved by the team.
- Research and planning contributions are accepted when the agreed deliverable is reviewed and recorded in the sprint notes.
- Pair programming is allowed, but each member's individual contribution must be clearly documented.
- The Project Manager tracks progress, and each member's accepted work is recorded in the sprint notes.
- Tasks should be sized so everyone has an opportunity to complete at least one accepted contribution per sprint.

## Pull Requests & Reviews

- Create a separate branch for each feature, bug fix, or documentation change.
- Use descriptive branch names, such as `feature/sensor-map` or `docs/readme-update`.
- Submit changes to the `main` branch through pull requests.
- Explain what was changed and how it was tested.
- Link the related GitHub Issue when applicable.
- Proposed policy: At least one other team member should approve a pull request before merging.
- Proposed review turnaround: Within two working days.
- Do not merge changes with unresolved review comments or failing required checks.

The team will confirm PR approval requirements and review turnaround expectations before adopting these policies.

## CI/CD

- CI/CD has not been configured yet.
- The Quality Owner is responsible for CI health and coordinating automated quality checks.
- The Deployment Owner manages deployment setup and environments.
- Once the technology stack is selected, the team will decide which CI/CD tools to use.
- Planned CI checks include linting, automated tests, and security scanning.
- The CI configuration location, required jobs, and instructions for viewing logs or rerunning checks will be documented after implementation.
- Required checks must pass before merging or releasing once they are enabled.

## Security & Secrets

- Never commit passwords, API keys, access tokens, or other credentials.
- Store sensitive configuration values using environment variables or an approved secrets manager.
- Do not commit `.env` files containing real credentials.
- Report security concerns privately to the Quality Owner.
- Notify the team immediately if credentials are accidentally exposed so they can be revoked or rotated.
- Review new dependencies and dependency updates before merging.
- Follow the AI and confidentiality rules in the Team Charter and `AGENTS.md`.

## Documentation Expectations

- Update `README.md` when setup or usage instructions change.
- Document significant technical decisions using Architecture Decision Records (ADRs) in `docs/decisions/`.
- Update relevant documentation when adding or modifying features.
- Use comments to explain code that is not immediately clear.
- The Documentation Owner is responsible for keeping project documentation current.
- The AI Coordinator is responsible for maintaining `AGENTS.md`.

## Release Process

- The Quality Owner oversees release quality and ensures the Definition of Done is satisfied.
- The Deployment Owner manages deployment environments and deployment procedures.
- The hosting platform and release process have not been finalized.
- Before the first release, the team will document versioning, release tags, deployment steps, and rollback procedures.
- Releases should be tested before being demonstrated to the project partner.

## Support & Contact

- Use Discord for team communication, questions, and blockers.
- Project Manager: Evan Seip — sprint planning, task tracking, and partner communication.
- AI Coordinator: Son Thai Do Nguyen — AI tools, `AGENTS.md`, and confidentiality.
- Quality Owner: Branden Rodriguez — testing, CI, code reviews, and Definition of Done.
- Facilitation Owner: Annika Etchison — meeting coordination and team discussions.
- Deployment Owner: Aron Meraz — deployment and environments.
- Documentation Owner: Thao Nguyen — project documentation and decision records.

If a problem cannot be resolved within the team, contact the course TA or instruction team when appropriate.
