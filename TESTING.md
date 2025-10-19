# Testing Guide for Claude Code Skill Creator Plugin

This guide explains how to test your plugin locally before publishing.

## Prerequisites

- Claude Code installed and configured
- This repository cloned locally

## Testing Methods

### Method 1: Test from Local Directory (Recommended)

The easiest way to test during development:

1. **Navigate to a test project** (not this plugin directory):
   ```bash
   cd ~/your-test-project
   ```

2. **Install plugin from local path**:
   ```bash
   /plugin add file:///Users/aloncohen/Documents/claude-skills
   ```

   Replace the path with your actual plugin directory path. Use `pwd` in the plugin directory to get the full path.

3. **Verify installation**:
   ```bash
   /plugin list
   ```

   You should see `claude-code-skill-creator` in the list.

4. **Test the command**:
   ```bash
   /create-skill
   ```

   Claude should respond with the workflow from `commands/create-skill.md`.

5. **Remove when done testing**:
   ```bash
   /plugin remove claude-code-skill-creator
   ```

### Method 2: Test from GitHub

After pushing changes to GitHub:

1. **Remove old installation** (if exists):
   ```bash
   /plugin marketplace remove Alon2904/claude-code-skill-creator
   ```

2. **Install from GitHub**:
   ```bash
   /plugin marketplace add Alon2904/claude-code-skill-creator
   ```

3. **Test the command**:
   ```bash
   /create-skill
   ```

## What to Test

### 1. Command Availability
- [ ] `/create-skill` command is recognized
- [ ] Command loads the workflow from `commands/create-skill.md`
- [ ] Claude asks for skill requirements

### 2. Skill Creation Workflow
- [ ] Claude asks what skill you want to create
- [ ] Claude asks where to create it (.claude/skills/ or custom path)
- [ ] Skill name generation works (kebab-case)
- [ ] Init script runs successfully
- [ ] SKILL.md is created and customized
- [ ] Supporting files (scripts, references, assets) are created if needed

### 3. Helper Scripts
- [ ] `skills/skill-creator/scripts/init_skill.py` exists and is executable
- [ ] `skills/skill-creator/scripts/package_skill.py` exists and is executable
- [ ] Scripts run without errors

### 4. Package Creation
- [ ] Validation runs before packaging
- [ ] .zip file is created successfully
- [ ] .zip contains all required files

## Testing Checklist

Run through these scenarios:

### Scenario 1: Project-Specific Skill
```bash
cd ~/your-test-project
/create-skill
> "Create a skill for writing FastAPI tests"
> Choose: Current Project (.claude/skills/)
```

**Expected:**
- Skill created at `.claude/skills/fastapi-test-helper/`
- SKILL.md contains relevant instructions
- Packaged as .zip

### Scenario 2: Shareable Skill
```bash
cd ~/temp-directory
/create-skill
> "JSON validator and formatter"
> Choose: For Sharing (custom path)
```

**Expected:**
- Skill created in specified path
- Generic instructions (not project-specific)
- Packaged as json-validator.zip

### Scenario 3: Skill with Scripts
```bash
/create-skill
> "Database migration helper with script"
> Include scripts: Yes
```

**Expected:**
- scripts/ directory created
- Example script replaced with actual implementation
- Scripts are executable (chmod +x)

## Common Issues

### Issue: `/create-skill` not found
**Solution:**
- Run `/plugin list` to verify installation
- Reinstall plugin
- Check that `commands/create-skill.md` exists in plugin

### Issue: Init script not found
**Solution:**
- Verify `skills/skill-creator/scripts/init_skill.py` exists
- Check that skills directory is included in git (not ignored)

### Issue: Package validation fails
**Solution:**
- Check SKILL.md frontmatter format
- Ensure all required directories exist
- Review validation error messages

## Development Workflow

1. **Make changes** to plugin files
2. **Test locally** using Method 1 (file path)
3. **Verify functionality** with test scenarios
4. **Commit changes** to git
5. **Push to GitHub**
6. **Test from GitHub** using Method 2
7. **Update version** in plugin.json and marketplace.json
8. **Create release** (optional)

## Quick Test Command

Run this one-liner to test the full workflow:

```bash
cd /tmp && /plugin remove claude-code-skill-creator 2>/dev/null; /plugin add file:///Users/aloncohen/Documents/claude-skills && /create-skill
```

Replace the path with your plugin directory.

## Automated Testing (Future)

Consider adding:
- Unit tests for Python scripts
- Integration tests for workflow
- CI/CD pipeline for validation
