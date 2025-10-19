# Claude Code Skill Creator

Create custom Claude skills with a single command.

## What is this?

A Claude Code plugin that adds the `/create-skill` command. Use it to create skills that help Claude understand your project better.

## Install

```bash
/plugin marketplace add Alon2904/claude-code-skill-creator
```

That's it. You now have `/create-skill` available everywhere.

## Usage

### Create a skill for your project (recommended)

Navigate to your project and run the command:

```bash
cd ~/my-fastapi-project
/create-skill
```

Claude will:
1. Ask what skill you want
2. Analyze your project code
3. Create a skill at `.claude/skills/` in your project
4. The skill understands YOUR code, YOUR patterns

**Example:**
```
/create-skill
> "Create a skill that helps write tests for our FastAPI endpoints"

✅ Skill created at .claude/skills/api-test-helper/
```

Now when you ask Claude to write tests, it knows:
- Your test structure and fixtures
- Your database models
- Your API patterns and conventions
- How to write tests that fit your project

### Create a skill to share

Want to create a general-purpose skill to share with others?

```bash
cd ~/any-folder
/create-skill
> "JSON validator and formatter"

✅ Skill created and packaged as json-validator.zip
```

Share the .zip with your team or upload to Claude.ai.

## How it works

**When run in your project:**
- Skills are created at `.claude/skills/` in your project
- Claude has full context of your codebase
- Skills are tailored to your specific code

**When run elsewhere:**
- Skills are packaged as .zip files
- Easy to share and distribute

## Example

See `examples/json-validator/` for a complete skill example.

## What gets created?

When you run `/create-skill`, you get:

- **SKILL.md** - The main skill file with instructions for Claude
- **scripts/** (optional) - Helper scripts for automation
- **references/** (optional) - Reference documentation
- **assets/** (optional) - Templates or boilerplate files
- **[skill-name].zip** - Packaged skill ready to share

## Credits

Built on [Anthropic's Skills System](https://github.com/anthropics/skills)

Uses Anthropic's official skill creation scripts.

## License

MIT License - see [LICENSE](LICENSE)
