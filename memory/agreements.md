# Working agreements

Universal rules for humans and agents working on this project. Canonical vendor-neutral guidance lives here — not in Cursor rules alone.

## Repository truth

- Inspect repository state before making claims about files, branches, configuration or behaviour.
- Current repository evidence overrides remembered assumptions or chat history.
- Record uncertainty honestly. Use states such as unknown, assumed, proposed, investigating, accepted, rejected, superseded or deferred.
- Do not invent architecture, deployment, product decisions or infrastructure that does not exist in the repository.

## Repository identity

- Do not include personal identity in repository content unless it is deliberately public and relevant to the project.
- Use neutral role language by default, such as the maintainer, the project owner or the user.
- Do not write Git commit email addresses into documentation.
- Prefer a privacy-safe no-reply address for public repositories where the Git host supports one.
- Do not commit unnecessary personally identifiable information.
- Do not include private or unnecessary real names, personal emails, private addresses, telephone numbers, family details or private employment information.
- Do not include local usernames, filesystem paths, device names, hardware specifications, hostnames, private IP addresses or private service URLs.
- Redact logs and diagnostics before committing them.
- Private repositories are not exempt from privacy discipline.

## Secrets and security

- Never commit secrets, credentials or real environment values.
- Use ignored local configuration, secret stores and safe example files.
- Validate untrusted input.
- Use least privilege where relevant.
- Treat security as proportionate but never optional.
- Consider privacy and retention when processing user data.

## Git identity and authority

- Use the maintainer's configured privacy-safe Git identity for commits.
- Inspect author and committer metadata before pushing.
- Warn if the configured identity appears to expose a personal email address.
- Do not print unsafe identity values in full.
- Do not commit using an unreviewed privacy-unsafe identity.
- Do not commit, push, merge, tag, release, deploy, rewrite history or perform destructive Git operations unless explicitly authorised for that task.
- Inspect branch and working-tree state first.
- Use descriptive commit messages.
- Do not add Cursor, cursoragent, ChatGPT or another AI as author, committer or co-author.
- Do not add `Co-authored-by` trailers.
- Do not expose PII through commit metadata.

## Scope and implementation

- Make the smallest useful, testable change.
- Investigate before risky, broad or ambiguous implementation.
- Avoid unrelated refactors.
- Prefer clear maintainable code over clever code.
- Remove dead code and avoid unnecessary duplication.
- Refactor while context is fresh when it directly supports the active work.
- Do not introduce speculative abstractions merely because a project may grow.

## Accessibility and usability

- User interfaces should aim for WCAG AA.
- Apply semantic structure, keyboard access, visible focus, accessible names, readable contrast and usable error handling from the start.
- Accessibility is not a later bolt-on.
- Usability includes responsive, speedy performance.
- Avoid unnecessary dependencies and payload.
- Measure performance before complex optimisation.

## Data separation

- Keep maintained data and content separate from presentation and executable logic where practical.
- JSON, YAML, Markdown, text files, APIs or databases may be appropriate.
- Do not hard-code significant maintainable data into UI or business logic without a good reason.

## Testing and verification

- Every implementation should have a repeatable way to verify it.
- Add automated tests where they provide value.
- Use build, lint, type, accessibility, integration or manual checks proportionately.
- Do not create a large test suite for ceremony.
- Do not leave the project in a state where testing would later require a structural rebuild.

## Documentation and memory

- Keep canonical memory concise.
- One durable fact should have one authoritative home.
- Historical evidence should remain retrievable but outside normal context.
- Update current memory when meaningful reality changes.
- Do not create permanent files for trivial tasks or decisions.

## Specialist guidance

Deeper project-specific guidance may appear under `specialist/` only when a real need exists. Follow relevant specialist guidance when it exists and when current project truth points to it for the active task.
