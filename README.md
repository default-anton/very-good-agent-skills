# very-good-agent-skills

Small, reusable agent skills you can copy into local skill directories.

## Included

- `agents-md`: rules for creating and editing `AGENTS.md`
- `git-commit`: workflow and constraints for creating git commits

## Install

Copy a skill directory into your tool's skills directory.

Example:

```bash
curl -L https://codeload.github.com/default-anton/very-good-agent-skills/tar.gz/refs/heads/main \
  | tar -xz
cp -R very-good-agent-skills-main/agents-md ~/.codex/skills/
```

## License

MIT
