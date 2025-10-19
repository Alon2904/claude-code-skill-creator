# Examples

This directory contains example workflows and sample skills demonstrating different usage patterns of the Claude Code Skill Creator.

## Directory Structure

### sample-skills/
Complete working skills that demonstrate different patterns:
- **json-validator/** - Simple validation skill (instruction-only)
- **api-test-helper/** - Project-specific skill example (with scripts)
- **readme-generator/** - Template-based skill (with assets)

Each sample skill includes:
- Complete SKILL.md file
- Any helper scripts, references, or assets
- README explaining the skill's purpose and usage

### workflows/
Step-by-step examples of creating skills:
- **pattern-a-marketplace.md** - Creating a general-purpose skill for sharing
- **pattern-b-project.md** - Creating a project-specific skill with context
- **pattern-c-sandbox.md** - Experimenting and learning

## Using These Examples

### To Learn
1. Browse the sample skills
2. Read their SKILL.md files
3. Understand the structure and patterns
4. See how different skills are organized

### To Test
1. Copy a sample skill to try it:
   ```bash
   cp -r examples/sample-skills/json-validator skills/custom/
   ```

2. Test the skill in Claude:
   ```
   Use the json-validator skill to validate this JSON: {"name": "test"}
   ```

### To Adapt
1. Use a sample as a template
2. Run `/create-skill` and customize
3. Reference the examples for structure ideas

## Sample Skills Overview

### JSON Validator (Simple)
**Purpose:** Validate and format JSON data
**Pattern:** Instruction-only skill
**Complexity:** Beginner
**Files:** Just SKILL.md

### API Test Helper (Moderate)
**Purpose:** Write tests for API endpoints
**Pattern:** Project-specific with scripts
**Complexity:** Intermediate
**Files:** SKILL.md + Python scripts

### README Generator (Advanced)
**Purpose:** Generate comprehensive README files
**Pattern:** Template-based skill
**Complexity:** Advanced
**Files:** SKILL.md + markdown templates in assets/

## Creating Your Own

After reviewing these examples, create your own:

```bash
/create-skill
```

Describe what you want to create, and Claude will guide you through the process!

## Need More Help?

- [Quick Start Guide](../QUICKSTART.md)
- [Usage Patterns](../PATTERNS.md)
- [Main README](../README.md)
