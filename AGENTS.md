# Repository scope

- Keep project-level, version-independent material in this Hub: objectives, design principles, conceptual architecture, project evolution, research topics, publications, and citation guidance.
- Keep executable behavior and version-specific contracts in the corresponding implementation repository. For v3 this includes code behavior, APIs, YAML schemas, commands, environment variables, deployment, exact metric formulas and events, operational limitations, and validation records.
- When a topic spans both repositories, summarize the stable concept here and link to the implementation repository for canonical details.

# Documentation

- English is the default language. Maintain a matching `.kr.md` file for every public Markdown document and keep both versions synchronized.
- Keep official paper titles, author names, venue names, and DOI links unchanged in translated documents.

# Validation

- On Windows, do not run generated Go test binaries or commands that may display an execution-permission dialog, including `*.test.exe` such as `peer.test.exe`.
- Use static document checks on Windows and run executable validation in the project's Linux container or on a Linux host.
