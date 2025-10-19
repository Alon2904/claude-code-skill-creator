# Quick Start Guide

Get up and running with Claude Code Skill Creator in minutes. Choose your path based on what you want to create.

## 🎯 Choose Your Path

Click the path that best describes what you want to do:

- [I want to create skills for my existing project →](#path-1-project-specific-skills)
- [I want to create and share general-purpose skills →](#path-2-shareable-skills)
- [I want to learn and experiment →](#path-3-learning--experimentation)

---

## Path 1: Project-Specific Skills

**Best for:** Creating skills tailored to YOUR codebase with full project context.

**Time:** 5 minutes

### Step 1: Install the Command in Your Project

```bash
# Navigate to your project
cd /path/to/your-project

# Create the .claude directory structure
mkdir -p .claude/commands

# Download the create-skill command
curl -o .claude/commands/create-skill.md \
  https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/main/.claude/commands/create-skill.md
```

### Step 2: Install Helper Scripts

```bash
# Create scripts directory
mkdir -p scripts

# Download helper scripts from Anthropic's official repo
curl -o scripts/init_skill.py \
  https://raw.githubusercontent.com/anthropics/skills/main/skill-creator/scripts/init_skill.py

curl -o scripts/package_skill.py \
  https://raw.githubusercontent.com/anthropics/skills/main/skill-creator/scripts/package_skill.py

curl -o scripts/quick_validate.py \
  https://raw.githubusercontent.com/anthropics/skills/main/skill-creator/scripts/quick_validate.py

# Make them executable
chmod +x scripts/*.py
```

### Step 3: Create Your First Skill

Open your project in Claude Code and run:

```
/create-skill
```

Claude will ask: "What skill would you like to create?"

**Try this example:**
```
Create a skill that helps write unit tests for our API endpoints
```

When asked where to create the skill, choose: `.claude/skills/`

### Step 4: Watch the Magic ✨

Claude will:
1. ✅ Analyze your project structure
2. ✅ Generate a skill name (e.g., `api-test-helper`)
3. ✅ Create SKILL.md with project-specific instructions
4. ✅ Add helper scripts if needed
5. ✅ Validate the skill
6. ✅ Package as .zip

### Step 5: Test Your Skill

```
Use the api-test-helper skill to write tests for the /users GET endpoint
```

Claude will now use your custom skill with full knowledge of your project!

### What You Get

```
your-project/
├── .claude/
│   ├── commands/
│   │   └── create-skill.md
│   └── skills/
│       └── api-test-helper/
│           ├── SKILL.md
│           └── [optional: scripts/, references/, assets/]
├── scripts/
│   ├── init_skill.py
│   ├── package_skill.py
│   └── quick_validate.py
└── [your existing project files]
```

### Next Steps

- Create more skills: Just run `/create-skill` again
- Share with your team: Commit `.claude/skills/` to git
- Customize skills: Edit SKILL.md files as needed

[Learn more about this pattern →](PATTERNS.md#pattern-b-local-project-tool)

---

## Path 2: Shareable Skills

**Best for:** Creating general-purpose skills to share with the community.

**Time:** 2 minutes

### Step 1: Fork This Repository (Optional but Recommended)

```bash
# On GitHub, fork: YOUR_GITHUB_USERNAME/claude-code-skill-creator
# Then clone your fork
git clone --recursive https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator.git
cd claude-code-skill-creator
```

### Step 2: Add as Marketplace in Claude Code

```bash
# In Claude Code, run:
/plugin marketplace add YOUR_GITHUB_USERNAME/claude-code-skill-creator
```

### Step 3: Install the Skill Creator Tool

```bash
/plugin install skill-creator-tool@claude-code-skill-creator
```

### Step 4: Create Your First Skill

```
/create-skill
```

Claude will ask: "What skill would you like to create?"

**Try this example:**
```
Create a skill for validating and formatting JSON files
```

When asked where to create the skill, choose: `skills/custom/`

### Step 5: Watch the Magic ✨

Claude will:
1. ✅ Generate skill name (e.g., `json-validator`)
2. ✅ Create complete SKILL.md
3. ✅ Add any needed scripts/references/assets
4. ✅ Validate the skill
5. ✅ Package as .zip
6. ✅ Register in marketplace.json

### Step 6: Share Your Skill

**Option 1: Via Your Marketplace**
```bash
# Commit and push to your fork
git add .
git commit -m "Add json-validator skill"
git push

# Others can install with:
/plugin install json-validator@YOUR_USERNAME-claude-code-skill-creator
```

**Option 2: Via Zip File**
Share the generated `.zip` file directly with others.

**Option 3: Submit to Anthropic**
Submit your skill to the official Anthropic skills repository!

### Next Steps

- Create more skills: Run `/create-skill` again
- Share on GitHub: Push to your repository
- Get feedback: Share in Claude community

[Learn more about this pattern →](PATTERNS.md#pattern-a-global-marketplace)

---

## Path 3: Learning & Experimentation

**Best for:** Exploring how skills work and prototyping ideas.

**Time:** 1 minute

### Step 1: Clone the Repository

```bash
git clone --recursive https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator.git
cd claude-code-skill-creator
```

The `--recursive` flag also downloads Anthropic's official skills.

### Step 2: Open in Claude Code

```bash
# Open in your editor with Claude Code
code .
```

### Step 3: Explore the Examples

Browse the `skills/` directory to see official Anthropic skills:
- `skills/skill-creator/` - Meta-skill for creating skills
- `skills/document-skills/` - PDF, DOCX, XLSX skills
- `skills/algorithmic-art/` - Creative skills
- And many more!

### Step 4: Create a Test Skill

```
/create-skill
```

**Try this simple example:**
```
Create a skill that generates TODO comments in different programming languages
```

When asked where to create it, choose: `skills/custom/`

### Step 5: Experiment!

- ✅ Create different types of skills
- ✅ Try adding scripts
- ✅ Add reference documentation
- ✅ Include asset files
- ✅ Learn the skill patterns

### Step 6: Move to Production

When you create something useful:
- Copy to a real project (Path 1)
- Push to your marketplace fork (Path 2)
- Share the .zip file with others

### Next Steps

- Read existing skills for inspiration
- Try complex skills with multiple components
- Experiment with different structures

[Learn more about this pattern →](PATTERNS.md#pattern-c-sandboxlearning)

---

## Common First Skills to Create

Need ideas? Try creating these common skills:

### Beginner Skills

**1. Git Commit Message Helper**
```
Create a skill that helps write conventional commit messages
```

**2. README Generator**
```
Create a skill for generating comprehensive README files
```

**3. Code Comment Generator**
```
Create a skill that writes clear, helpful code comments
```

### Intermediate Skills

**4. API Documentation Generator**
```
Create a skill that generates API documentation from code
```

**5. Test Data Generator**
```
Create a skill for generating realistic test data
```

**6. Database Migration Helper**
```
Create a skill that helps write database migration scripts
```

### Advanced Skills

**7. Project-Specific Analyzer**
```
Create a skill that analyzes our codebase and suggests improvements
```

**8. Custom Linter**
```
Create a skill that checks our code against our team's style guide
```

**9. Deployment Script Generator**
```
Create a skill that generates deployment scripts for our infrastructure
```

---

## Troubleshooting

### Command not found: `/create-skill`

**Problem:** Claude doesn't recognize the command

**Solutions:**
- **Path 1:** Make sure you created `.claude/commands/create-skill.md` in your project
- **Path 2:** Run `/plugin install skill-creator-tool@claude-code-skill-creator`
- **Path 3:** Make sure you're in the cloned repository directory

### Python scripts not found

**Problem:** Error when trying to run init_skill.py or package_skill.py

**Solutions:**
- **Path 1:** Run Step 2 again to download the scripts
- **Path 2/3:** The scripts should be in `skills/skill-creator/scripts/` from the submodule
- Check the scripts are executable: `chmod +x scripts/*.py`

### Skill validation fails

**Problem:** Created skill doesn't validate

**Common issues:**
- Skill name must be hyphen-case (e.g., `my-skill` not `MySkill`)
- SKILL.md must start with `---` for YAML frontmatter
- `name` and `description` are required in frontmatter
- Skill directory name must match the `name` in frontmatter

**Fix:** Claude will usually fix these automatically, but you can also edit SKILL.md manually

### Permission denied when running scripts

**Problem:** Can't execute init_skill.py or package_skill.py

**Solution:**
```bash
chmod +x scripts/*.py
# or
chmod +x skills/skill-creator/scripts/*.py
```

### Git submodule is empty

**Problem:** `skills/` directory is empty after cloning

**Solution:**
```bash
git submodule update --init --recursive
```

---

## Tips for Success

### 🎯 Be Specific
Instead of: "Create a skill for testing"
Try: "Create a skill that helps write pytest tests for FastAPI endpoints"

### 🧠 Use Project Context (Path 1)
The more Claude knows about your project, the better the skill:
- Mention your frameworks (FastAPI, React, Django, etc.)
- Reference your coding standards
- Describe your project structure

### 📚 Start Simple, Then Enhance
Create a basic skill first, then:
- Add scripts for complex operations
- Add references for detailed documentation
- Add assets for templates or boilerplate

### 🔄 Iterate
Skills aren't set in stone:
- Edit SKILL.md to refine instructions
- Add new sections as you learn what works
- Remove unnecessary parts

### 🤝 Share and Learn
- Share your skills with others
- Get feedback from your team
- Contribute to the community

---

## What's Next?

Now that you're set up, explore:

- **[Usage Patterns](PATTERNS.md)** - Deep dive into each pattern
- **[Examples](examples/)** - See example skills and workflows
- **[Contributing](CONTRIBUTING.md)** - Help improve this tool
- **[Anthropic Skills Docs](https://github.com/anthropics/skills)** - Official skills documentation

---

## Need Help?

- 🐛 [Report an issue](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/issues)
- 💬 [Start a discussion](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/discussions)
- 📖 [Read the full documentation](README.md)

Happy skill creating! 🎉
