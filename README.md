# Claude Code Skill Creator

**Interactive `/create-skill` command for Claude Code** - Automate the creation of custom Claude skills with guided workflows, validation, and packaging.

## What Is This?

This tool extends [Anthropic's skill system](https://github.com/anthropics/skills) with an interactive command that automates the entire skill creation process. Instead of manually creating files and following specifications, just run `/create-skill` and let Claude guide you through creating professional, validated skills.

### Key Features

✨ **Interactive Creation** - Guided workflow asks questions and customizes everything for you
🎯 **Context-Aware** - Works in your projects with full codebase context, or standalone
📦 **Auto-Validation** - Validates skill structure and packaging automatically
🔧 **Script Generation** - Creates helper scripts, references, and assets as needed
📝 **Smart Customization** - Claude writes skill content based on your requirements
🚀 **Multiple Patterns** - Use as marketplace, project tool, or sandbox

## Quick Start

Choose the pattern that fits your needs:

### For Creating Project-Specific Skills (Recommended ⭐)

Perfect when you want Claude to have full context of YOUR codebase:

```bash
# Copy the command to your project
mkdir -p .claude/commands
curl -o .claude/commands/create-skill.md \
  https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/main/.claude/commands/create-skill.md

# In Claude Code:
/create-skill
```

[Full Setup Instructions for Pattern B →](PATTERNS.md#pattern-b-local-project-tool)

### For Creating Shareable General-Purpose Skills

Perfect for building a library of reusable skills:

```bash
# In Claude Code:
/plugin marketplace add YOUR_GITHUB_USERNAME/claude-code-skill-creator
/plugin install skill-creator-tool@claude-code-skill-creator

# Then create skills:
/create-skill
```

[Full Setup Instructions for Pattern A →](PATTERNS.md#pattern-a-global-marketplace)

### For Learning and Experimentation

Perfect for exploring and prototyping:

```bash
git clone --recursive https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator.git
cd claude-code-skill-creator

# In Claude Code:
/create-skill
```

[Full Setup Instructions for Pattern C →](PATTERNS.md#pattern-c-sandboxlearning)

## Why Use This Tool?

### Before: Manual Skill Creation
```bash
mkdir my-skill
cd my-skill
# Create SKILL.md with proper YAML frontmatter
# Write all instructions manually
# Create scripts/, references/, assets/ if needed
# Validate frontmatter format
# Package as .zip
# Register in marketplace.json
```

### After: Automated with `/create-skill`
```bash
/create-skill
> I want a skill for analyzing JSON files
# Claude creates everything automatically
✅ Skill created, validated, and packaged!
```

## What Gets Created?

When you run `/create-skill`, you'll get:

📄 **SKILL.md** - Complete skill file with:
- Proper YAML frontmatter
- Custom instructions based on your requirements
- Examples and guidelines
- Resource documentation

🔧 **Helper Scripts** (optional) - Python/Bash scripts for automation

📚 **Reference Documentation** (optional) - Detailed guides and API docs

🎨 **Asset Files** (optional) - Templates, boilerplate, or resources

📦 **Packaged .zip** - Ready to share or distribute

✅ **Validation** - Automatically checks skill structure

## Usage Patterns

This tool supports three different usage patterns. **Choose the one that fits your needs:**

### Pattern A: Global Marketplace
Create and share general-purpose skills through a centralized marketplace.

**Best for:** JSON parsers, Git helpers, documentation templates, code formatters

[Learn More →](PATTERNS.md#pattern-a-global-marketplace)

### Pattern B: Local Project Tool ⭐ RECOMMENDED
Create project-specific skills with full codebase context.

**Best for:** "Analyze our database schema", "Generate our API docs", "Write tests for our endpoints"

**Why powerful:** Claude sees your entire project when creating the skill, so it can reference YOUR specific code, APIs, and patterns.

[Learn More →](PATTERNS.md#pattern-b-local-project-tool)

### Pattern C: Sandbox/Learning
Clone and experiment in a safe environment.

**Best for:** Learning how skills work, prototyping ideas, exploring examples

[Learn More →](PATTERNS.md#pattern-c-sandboxlearning)

**Not sure which to choose?** Check out our [detailed comparison →](PATTERNS.md#comparison-table)

## Example Skills You Can Create

💡 **Simple instruction-only skills:**
- Code review best practices
- Documentation style guide
- Git workflow helper

🔧 **Script-heavy skills:**
- Image processing (resize, convert, compress)
- Database migration generator
- Log file analyzer

📋 **Template-based skills:**
- API documentation generator
- Project scaffolding
- README templates

🎯 **Project-specific skills:**
- "Test writer for our FastAPI app"
- "Migration script generator for our DB schema"
- "Documentation following our standards"

## How It Works

1. **You run** `/create-skill`
2. **Claude asks** what you want to create
3. **Claude generates**:
   - Skill name (or you provide one)
   - Complete SKILL.md file
   - Helper scripts if needed
   - Reference documentation if needed
   - Asset files if needed
4. **Claude validates** the skill structure
5. **Claude packages** as a .zip file
6. **Optionally registers** in marketplace.json
7. **You're done!** ✅

## Documentation

- **[Usage Patterns](PATTERNS.md)** - Detailed guide to all three usage patterns
- **[Quick Start Guide](QUICKSTART.md)** - Step-by-step setup for each pattern
- **[Contributing](CONTRIBUTING.md)** - How to contribute to this project
- **[Examples](examples/)** - Sample skills and workflows

## Requirements

- **Claude Code** - This is a Claude Code plugin/tool
- **Python 3.7+** - For helper scripts (validation, packaging)
- **Git** - For cloning the repository (Pattern C)

## Credits

This tool extends and builds upon:
- [Anthropic's Skills Repository](https://github.com/anthropics/skills) - The official skills collection and specification
- [Agent Skills Spec](https://github.com/anthropics/skills/blob/main/agent_skills_spec.md) - The skills specification
- Anthropic's `skill-creator` skill - Provides the init and validation scripts

**Special thanks to the Anthropic team** for creating the skills system and providing the foundation that makes this tool possible.

## What Makes This Different?

This isn't a fork or replacement of Anthropic's skills repo. Instead, it:

✅ **Extends** the official skills system with automation
✅ **Uses** Anthropic's scripts and specifications
✅ **Adds** interactive creation workflow
✅ **Enables** context-aware skill generation
✅ **Maintains** compatibility with the official spec

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- Reporting issues
- Suggesting improvements
- Submitting pull requests
- Code style guidelines

## License

MIT License - see [LICENSE](LICENSE) for details.

The Anthropic skills (in the `skills/` submodule) are licensed under Apache 2.0 by Anthropic.

## Support

- 🐛 [Report a bug](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/issues/new?template=bug_report.md)
- 💡 [Request a feature](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/issues/new?template=feature_request.md)
- 📖 [Read the docs](PATTERNS.md)
- 💬 [Discussions](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/discussions)

## Roadmap

- [ ] Add more example skills
- [ ] Create video tutorials
- [ ] Support for skill templates
- [ ] Integration with Claude.ai skill upload
- [ ] Skill testing framework
- [ ] Community skill marketplace

## Frequently Asked Questions

**Q: Do I need to fork Anthropic's skills repo?**
A: No! This tool uses Anthropic's repo as a git submodule. You get official skills + our creation tool.

**Q: Will my skills work with Claude.ai?**
A: Yes! Skills created with this tool follow the official Agent Skills Spec, so they work everywhere.

**Q: Can I create skills for my team's private projects?**
A: Yes! Use Pattern B to create project-specific skills. They can be committed to your team's repository.

**Q: How do I update to get new Anthropic skills?**
A: Run `git submodule update --remote` to pull the latest official skills.

**Q: Can I contribute skills back to Anthropic's repo?**
A: Yes! Create the skill here, then submit it to their repository following their contribution guidelines.

---

**Ready to create your first skill?** → [Choose your pattern](PATTERNS.md) or [Jump to Quick Start](QUICKSTART.md)
