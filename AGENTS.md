# AI Agent Rules for Obsidian & Code integration

## Workspace Structure
- / (Root): Python/NodeJS Source Code
- /Vault_Storage: Obsidian Knowledge Base (Notes)

## Rules for Writing Documentation
1. When modifying or creating files in `/Vault_Storage`, always use standard Markdown.
2. Use Obsidian WikiLinks `[[Note Name]]` instead of relative markdown paths when referencing other notes.
3. NEVER expose any credentials, passwords, or API Keys in code files. If found, log a reminder inside `Vault_Storage/my-project-notes/secrets.md` instead.
4. Do not touch or modify the `.obsidian/` configuration directory.
