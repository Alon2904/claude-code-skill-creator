# Usage Patterns for Claude Code Skill Creator

This tool supports three different usage patterns. Choose the one that best fits your needs.

## 🤔 Which Pattern Should I Use?

### Pattern A: Global Marketplace
**✓ Use this if you want to:**
- Create general-purpose skills (JSON parser, Git helper, markdown formatter, etc.)
- Share skills with other developers
- Build a centralized library of reusable skills
- Contribute to the community

**Examples:**
- A skill for converting between data formats
- A skill for generating boilerplate code
- A skill for common Git workflows
- Documentation templates

---

### Pattern B: Local Project Tool ⭐ RECOMMENDED
**✓ Use this if you want to:**
- Create project-specific skills with full codebase context
- Have Claude understand YOUR project when designing the skill
- Build skills that use your specific APIs, patterns, or conventions
- Keep skills alongside your project code

**Examples:**
- "Analyze our database schema and suggest optimizations"
- "Generate API documentation following our standards"
- "Write tests for our FastAPI endpoints"
- "Create deployment scripts for our infrastructure"

**Why This Is Powerful:**
When you create a skill within your project, Claude has access to your entire codebase. This means the skill can be tailored specifically to your project's architecture, coding standards, and business logic. It's like having a custom assistant that knows your project intimately.

---

### Pattern C: Sandbox/Learning
**✓ Use this if you want to:**
- Learn how skills work
- Prototype and experiment
- Test ideas before committing
- Explore the skill system

**Examples:**
- Following tutorials
- Creating test skills
- Experimenting with skill structures
- Learning skill design patterns

---

## Pattern A: Global Marketplace

### What You Get
- Create skills in a dedicated marketplace repository
- Skills are automatically registered and discoverable
- Easy sharing and distribution to other developers
- Centralized skill library

### Setup Instructions

**Step 1: Add This Repository as a Marketplace**
```bash
# In Claude Code, run:
/plugin marketplace add YOUR_GITHUB_USERNAME/claude-code-skill-creator
```

**Step 2: Install the Skill Creator Tool**
```bash
/plugin install skill-creator-tool@claude-code-skill-creator
```

**Step 3: You're Ready!**
Now the `/create-skill` command is available globally in Claude Code.

### Creating a Skill

1. **Run the command from anywhere:**
   ```
   /create-skill
   ```

2. **Choose location when prompted:**
   Select "skills/custom/" when asked where to create the skill

3. **Follow the guided workflow:**
   - Describe what your skill should do
   - Claude will generate and customize all files
   - Skill will be created in `skills/custom/` directory

4. **Registration:**
   - Skill is automatically added to marketplace.json
   - Other users can discover and install it

### Sharing Your Skills

**Option 1: Via Marketplace**
```bash
# Others can install your skill with:
/plugin install your-skill-name@YOUR_USERNAME-skill-creator
```

**Option 2: Via Zip File**
- The packaged `.zip` file is created automatically
- Share the file directly with others
- They can upload to Claude.ai or extract to their projects

**Option 3: Via GitHub**
- Skills are in your public repository
- Others can clone and use immediately
- Fork-friendly for contributions

### Example Workflow

```bash
# You run
/create-skill

# Claude asks: "What skill would you like to create?"
> A skill for validating and formatting JSON files

# Claude asks: "Where should this skill be created?"
> skills/custom/

# Claude creates the skill, customizes it, packages it
✅ Skill created: skills/custom/json-validator/
📦 Package: json-validator.zip
📋 Registered in marketplace.json

# Others can now install it
/plugin install json-validator@yourname-skill-creator
```

---

## Pattern B: Local Project Tool ⭐

### What You Get
- Skills created directly in YOUR project
- Claude has full context of your codebase when creating the skill
- Skills can reference your specific code, APIs, and patterns
- Seamless integration with your project structure

### Setup Instructions

**Step 1: Copy the Command to Your Project**

```bash
# Create the commands directory if it doesn't exist
mkdir -p .claude/commands

# Download the create-skill command
curl -o .claude/commands/create-skill.md \
  https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/main/.claude/commands/create-skill.md
```

**Step 2: Copy the Helper Scripts**

```bash
# Create scripts directory
mkdir -p scripts

# Download the helper scripts
curl -o scripts/init_skill.py \
  https://raw.githubusercontent.com/anthropics/skills/main/skill-creator/scripts/init_skill.py

curl -o scripts/package_skill.py \
  https://raw.githubusercontent.com/anthropics/skills/main/skill-creator/scripts/package_skill.py

curl -o scripts/quick_validate.py \
  https://raw.githubusercontent.com/anthropics/skills/main/skill-creator/scripts/quick_validate.py

# Make scripts executable
chmod +x scripts/*.py
```

**Step 3: You're Ready!**
The `/create-skill` command is now available in your project.

### Creating a Project-Specific Skill

1. **Navigate to your project in Claude Code**
   ```bash
   cd /path/to/your-project
   ```

2. **Run the command:**
   ```
   /create-skill
   ```

3. **Choose location when prompted:**
   Select ".claude/skills/" (recommended) or a custom location

4. **Describe your skill with project context:**
   - "Create a skill that helps write tests for our FastAPI application"
   - "Generate migration scripts for our PostgreSQL database"
   - "Document our GraphQL schema following our standards"

5. **Claude uses YOUR codebase as context:**
   - Analyzes your project structure
   - Understands your coding patterns
   - References your specific APIs
   - Follows your conventions

### Example Workflow

```bash
# In your FastAPI project
/create-skill

# Claude asks: "What skill would you like to create?"
> A skill that helps write unit tests for our FastAPI endpoints

# Claude asks: "Where should this skill be created?"
> .claude/skills/

# Claude analyzes your project and creates a custom skill
# The skill knows about:
# - Your FastAPI app structure
# - Your testing framework (pytest)
# - Your database models
# - Your authentication system
# - Your coding standards

✅ Skill created: .claude/skills/api-test-helper/

# Now you can use it
> Use the api-test-helper skill to write tests for the /users endpoint
```

### Project Structure After Setup

```
your-project/
├── .claude/
│   ├── commands/
│   │   └── create-skill.md       # The tool
│   └── skills/                   # Your custom skills
│       └── api-test-helper/      # Example skill
│           └── SKILL.md
├── scripts/
│   ├── init_skill.py
│   ├── package_skill.py
│   └── quick_validate.py
├── src/
│   └── [your project code]
└── [other project files]
```

### Why This Pattern Is Powerful

**Context-Aware Creation:**
Claude sees your entire codebase when creating the skill. This means:
- Skill instructions reference YOUR actual code
- Examples use YOUR project's patterns
- Scripts integrate with YOUR tooling
- Documentation follows YOUR standards

**Project-Specific Intelligence:**
The skill becomes a domain expert in YOUR project:
- Knows your architecture
- Understands your conventions
- Follows your best practices
- Uses your specific technologies

**Example Comparisons:**

**Generic Skill (Pattern A):**
```markdown
## Writing Tests
Use pytest to write tests for your API endpoints.
Example: test_endpoint()
```

**Project-Specific Skill (Pattern B):**
```markdown
## Writing Tests for Our API
Use our TestClient from `tests/conftest.py` with the
test database fixture. Follow our pattern in `tests/test_users.py`.

Example for creating endpoint tests:
```python
def test_endpoint(test_client, test_db):
    # Uses your actual fixtures and patterns
```

### Sharing Project-Specific Skills

Even though these skills are tailored to your project, you can still share them:

1. **Within your team:**
   - Commit `.claude/skills/` to your repository
   - Team members get the skills automatically

2. **With other projects:**
   - Package the skill as `.zip`
   - Share with teams working on similar projects
   - They can adapt it to their needs

3. **As templates:**
   - Extract the skill to a template repository
   - Others can fork and customize for their projects

---

## Pattern C: Sandbox/Learning

### What You Get
- Local clone for experimentation
- All examples and documentation included
- Safe environment to learn and test
- No commitment or setup required

### Setup Instructions

**Clone the Repository:**
```bash
git clone --recursive https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator.git
cd claude-code-skill-creator
```

The `--recursive` flag also clones the Anthropic skills submodule.

### Using the Sandbox

1. **Open in Claude Code:**
   ```bash
   code .  # or open in your editor with Claude Code
   ```

2. **Run /create-skill:**
   ```
   /create-skill
   ```

3. **Experiment freely:**
   - Create test skills in `skills/custom/`
   - Try different skill structures
   - Explore the examples
   - Learn the patterns

4. **Copy successful skills:**
   - When you create something useful, copy it to:
     - Your projects (Pattern B)
     - Your marketplace repo (Pattern A)
     - Share the `.zip` file

### Example Learning Path

**Week 1: Explore Examples**
- Browse `skills/` directory
- Read existing skill SKILL.md files
- Understand different patterns

**Week 2: Create Simple Skills**
```
/create-skill
> A skill for generating TODO comments
```

**Week 3: Create Complex Skills**
```
/create-skill
> A skill with Python scripts for image processing
```

**Week 4: Advanced Features**
- Add custom scripts
- Create reference documentation
- Include template assets

---

## Comparison Table

| Feature | Pattern A: Marketplace | Pattern B: Project Tool | Pattern C: Sandbox |
|---------|----------------------|------------------------|-------------------|
| **Setup Time** | 2 minutes | 5 minutes | 1 minute |
| **Best For** | General-purpose skills | Project-specific skills | Learning |
| **Claude Has Project Context** | ❌ No | ✅ Yes | ⚠️ Limited |
| **Easy Sharing** | ✅ Built-in | ⚠️ Manual | ❌ No |
| **Skill Registration** | ✅ Automatic | ⚠️ Optional | ❌ No |
| **Team Collaboration** | ✅ Via marketplace | ✅ Via git repo | ❌ Individual |
| **Customization** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Distribution** | ✅ Easy | ⚠️ Manual | ❌ Local only |

---

## Frequently Asked Questions

### Can I use multiple patterns?
**Yes!** You can:
- Use Pattern A for general-purpose skills
- Use Pattern B in your projects for specific skills
- Use Pattern C for learning and prototyping

### Can I move skills between patterns?
**Yes!** Skills are just folders with SKILL.md files. You can:
- Copy from sandbox to your project
- Copy from project to marketplace
- Package and share anywhere

### Do I need to choose one pattern forever?
**No!** Start with what makes sense now:
- Learning? → Pattern C
- Have a project? → Pattern B
- Want to share? → Pattern A

You can change later.

### Which pattern do you recommend?
- **For developers working on projects:** Pattern B (project-specific)
- **For creating shareable skills:** Pattern A (marketplace)
- **For beginners:** Pattern C (sandbox) then move to B or A

### Can team members share skills?
- **Pattern A:** Yes, via marketplace installation
- **Pattern B:** Yes, via git repository (commit .claude/skills/)
- **Pattern C:** Manual sharing of .zip files

---

## Next Steps

Choose your pattern and get started:

- [Pattern A: Marketplace Setup →](QUICKSTART.md#pattern-a-marketplace)
- [Pattern B: Project Tool Setup →](QUICKSTART.md#pattern-b-project-tool)
- [Pattern C: Sandbox Setup →](QUICKSTART.md#pattern-c-sandbox)

Or learn more:
- [Main README](README.md)
- [Quick Start Guide](QUICKSTART.md)
- [Contributing](CONTRIBUTING.md)
