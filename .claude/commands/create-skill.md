# Create Skill Command

This command automates the complete workflow for creating a new Claude skill based on user requirements.

## Workflow

Follow these steps in order to create a custom skill:

### Step 0: Detect Context and Determine Location

First, determine where we are and where the skill should be created:

1. **Check current directory structure**:
   - Look for `skills/skill-creator/scripts/init_skill.py` → We're in the skill-creator repo
   - Look for `.claude/commands/create-skill.md` → Could be anywhere
   - Check current working directory name

2. **Ask user where to create the skill**:
   Use AskUserQuestion to present options:

   - **Option A: skills/custom/** (if we're in skill-creator repo)
     - Good for general-purpose, shareable skills
     - Can be registered in this repo's marketplace

   - **Option B: .claude/skills/** (if we're in a user's project)
     - Good for project-specific skills
     - Claude has full context of the project
     - Can be registered in project's local marketplace

   - **Option C: Custom path**
     - Let user specify any location
     - Ask for full or relative path

3. **Store the chosen path** for use in subsequent steps as `$SKILL_BASE_PATH`

4. **Locate helper scripts**:
   Try these paths in order:
   - `skills/skill-creator/scripts/` (if skill-creator repo)
   - `scripts/` (if copied locally)
   - If not found, offer to download them or provide manual instructions

### Step 1: Gather Requirements

Ask the user what skill they want to create. Gather:
- **Purpose**: What should the skill do?
- **Use cases**: When should Claude use this skill?
- **Required capabilities**: Any scripts, references, or assets needed?
- **Skill name**: If not provided, generate a suitable hyphen-case name from the description

Example questions:
- "What should this skill help you accomplish?"
- "What types of tasks or files will this skill handle?"
- "Will you need any scripts, reference documentation, or template assets?"

### Step 2: Generate Skill Name

If the user hasn't provided a skill name, generate one following these rules:
- Use hyphen-case (e.g., "json-to-csv")
- Lowercase letters, digits, and hyphens only
- Max 40 characters
- Descriptive and clear
- No starting/ending hyphens or consecutive hyphens

Confirm the generated name with the user.

### Step 3: Initialize Skill Scaffold

Run the init script to create the basic structure using the path determined in Step 0:

```bash
python $SCRIPT_PATH/init_skill.py <skill-name> --path $SKILL_BASE_PATH
```

Where:
- `$SCRIPT_PATH` is the location found in Step 0 (e.g., `skills/skill-creator/scripts`)
- `$SKILL_BASE_PATH` is the location chosen in Step 0 (e.g., `skills/custom` or `.claude/skills`)

This creates:
- `$SKILL_BASE_PATH/<skill-name>/` directory
- `SKILL.md` with template
- `scripts/example.py`
- `references/api_reference.md`
- `assets/example_asset.txt`

### Step 4: Customize SKILL.md

Read the generated `SKILL.md` file and customize it based on user requirements:

1. **Update frontmatter**:
   - Keep the `name` field as-is (matches directory name)
   - Replace the description with a clear, specific description of when Claude should use this skill
   - Add any optional fields if needed (license, allowed-tools, metadata)

2. **Update Overview section**:
   - Replace TODO with 1-2 sentences explaining what the skill enables

3. **Choose structure pattern**:
   - Workflow-Based: For sequential processes
   - Task-Based: For tool collections
   - Reference/Guidelines: For standards or specifications
   - Capabilities-Based: For integrated systems

   Delete the "Structuring This Skill" guidance section after choosing

4. **Add main content**:
   - Replace TODO sections with actual instructions, examples, and guidelines
   - Include code samples, decision trees, or workflows as appropriate
   - Reference any scripts, assets, or references being included

5. **Update Resources section**:
   - Keep explanations for scripts/, references/, assets/ that are being used
   - Remove explanations for directories that aren't needed

### Step 5: Customize Supporting Files

Based on user requirements:

**For scripts/ directory**:
- If custom scripts are needed, replace `example.py` with actual implementation
- If no scripts needed, delete the scripts/ directory entirely
- Make scripts executable: `chmod +x scripts/*.py`

**For references/ directory**:
- If reference documentation is needed, replace `api_reference.md` with actual content
- If no references needed, delete the references/ directory entirely

**For assets/ directory**:
- If template files/assets are needed, add them and delete `example_asset.txt`
- If no assets needed, delete the assets/ directory entirely

### Step 6: Ask Clarifying Questions

During customization, ask the user for clarification on:
- Specific implementation details for scripts
- Content for reference documentation
- Whether certain features should be included
- Examples they'd like to see in the documentation

Use the AskUserQuestion tool when needed to gather this information efficiently.

### Step 7: Clean Up

Remove all TODO markers and template placeholder text from files.

### Step 8: Ask About Registration

Ask the user: "Would you like to register this skill in a marketplace.json so it's available to Claude?"

If **yes**:
1. **Determine marketplace.json location** based on where skill was created:
   - If `$SKILL_BASE_PATH` is `skills/custom` → Use `.claude-plugin/marketplace.json`
   - If `$SKILL_BASE_PATH` is `.claude/skills` → Use `.claude-plugin/marketplace.json` in project root
   - If custom path → Ask user where marketplace.json should be

2. **Read or create marketplace.json**:
   - If it doesn't exist, create a new one:
   ```json
   {
     "name": "custom-skills-collection",
     "owner": {
       "name": "YOUR_NAME",
       "email": "YOUR_EMAIL"
     },
     "metadata": {
       "description": "Custom skills collection",
       "version": "1.0.0"
     },
     "plugins": [
       {
         "name": "custom-skills",
         "description": "User-created custom skills",
         "source": "./",
         "strict": false,
         "skills": []
       }
     ]
   }
   ```

3. **Check if "custom-skills" plugin exists** in the plugins array
4. **Add the new skill path** to the skills array:
   - Calculate relative path from marketplace.json to skill
   - Example: `"./custom/<skill-name>"` or `"./skills/<skill-name>"`
5. **Update the marketplace.json file**

If **no**:
- Skip registration
- Inform user: "You can manually register this skill later by adding its path to marketplace.json"

### Step 9: Validate and Package

Run the package script which automatically validates before packaging:

```bash
python $SCRIPT_PATH/package_skill.py $SKILL_BASE_PATH/<skill-name>
```

This will:
- Validate the skill structure
- Check frontmatter format
- Create a distributable .zip file in current directory

If validation fails, fix the issues and retry.

### Step 10: Show Summary

Display a summary of what was created:

```
✅ Skill created successfully!

📁 Location: $SKILL_BASE_PATH/<skill-name>/
📦 Package: <skill-name>.zip
📋 Registered: [Yes/No]

Files created:
- SKILL.md
- [List any scripts, references, or assets that were actually created]

Next steps:
1. Review the skill in $SKILL_BASE_PATH/<skill-name>/
2. Test the skill by mentioning it in a conversation with Claude
3. Share the .zip file if you want to distribute it to others

[If project-specific skill in .claude/skills/]
💡 Tip: Since this skill was created in your project, Claude will have
full context of your codebase when using it. The skill can reference
your specific APIs, patterns, and conventions.

[If shareable skill in skills/custom/]
💡 Tip: To share this skill, others can install it via:
- Upload the .zip to Claude.ai
- Add to their marketplace.json
- Copy the skill folder to their project
```

## Important Notes

- Always use existing scripts (init_skill.py, package_skill.py) rather than reimplementing
- Follow the skill structure patterns from existing skills in the skills/ directory
- Keep SKILL.md concise (<5k words); move detailed content to references/
- Use imperative/infinitive form in instructions, not second person
- Ensure all paths are relative to the project root
- Scripts should be executable and include --help information
- Validate before packaging to catch errors early

## Error Handling

If any step fails:
1. Display the error message clearly
2. Suggest fixes based on the error
3. Ask if the user wants to retry or make changes
4. Don't proceed to next steps until current step succeeds

## Examples

**Example 1: Simple instruction-only skill**
- User wants a skill for code review best practices
- No scripts or assets needed
- Just SKILL.md with guidelines and examples

**Example 2: Script-heavy skill**
- User wants a skill for image processing
- Needs Python scripts for resize, convert, compress
- SKILL.md explains when/how to use each script
- references/ contains detailed API docs

**Example 3: Template-based skill**
- User wants a skill for creating API documentation
- assets/ contains markdown templates
- SKILL.md explains the template structure
- No scripts needed
