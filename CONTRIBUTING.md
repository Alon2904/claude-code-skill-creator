# Contributing to Claude Code Skill Creator

Thank you for your interest in contributing! This document provides guidelines for contributing to this project.

## Ways to Contribute

### 🐛 Report Bugs
Found a bug? Please [open an issue](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/issues/new) with:
- Clear title describing the bug
- Steps to reproduce
- Expected vs. actual behavior
- Your environment (OS, Claude Code version, Python version)
- Screenshots if applicable

### 💡 Suggest Features
Have an idea? [Open a feature request](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/issues/new) with:
- Clear description of the feature
- Use case: why would this be useful?
- Examples of how it would work
- Any alternatives you've considered

### 📚 Improve Documentation
Documentation can always be better:
- Fix typos or unclear explanations
- Add more examples
- Improve setup instructions
- Translate to other languages

### 🎨 Add Examples
Share example skills you've created:
- Add to `examples/sample-skills/`
- Include a README explaining the skill
- Make sure it's well-documented

### 🔧 Submit Code
See the [Development section](#development) below.

## Development

### Prerequisites

- Git
- Python 3.7+
- Claude Code
- Familiarity with the [Agent Skills Spec](https://github.com/anthropics/skills/blob/main/agent_skills_spec.md)

### Setup Development Environment

1. **Fork the repository**
   ```bash
   # Fork on GitHub, then clone your fork
   git clone --recursive https://github.com/YOUR_USERNAME/claude-code-skill-creator.git
   cd claude-code-skill-creator
   ```

2. **Set up remote**
   ```bash
   git remote add upstream https://github.com/ORIGINAL_OWNER/claude-code-skill-creator.git
   ```

3. **Create a branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

### Making Changes

1. **Test your changes**
   - Test the `/create-skill` command thoroughly
   - Try all three usage patterns
   - Ensure validation and packaging still work
   - Check that documentation is accurate

2. **Follow conventions**
   - Use clear, descriptive commit messages
   - Follow existing code style
   - Update documentation if needed
   - Add examples if relevant

3. **Update documentation**
   If your change affects:
   - How to use the tool → Update README.md and QUICKSTART.md
   - Usage patterns → Update PATTERNS.md
   - Examples → Add to examples/

### Submitting Changes

1. **Commit your changes**
   ```bash
   git add .
   git commit -m "Brief description of changes

   Longer explanation if needed:
   - Change 1
   - Change 2
   - Closes #123 (if fixing an issue)"
   ```

2. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

3. **Create a Pull Request**
   - Go to GitHub and create a PR from your fork
   - Fill out the PR template
   - Link any related issues
   - Describe your changes clearly

### PR Guidelines

**Good PR:**
- ✅ Clear title: "Add JSON validator example skill"
- ✅ Description explains what and why
- ✅ Tests passing (if applicable)
- ✅ Documentation updated
- ✅ One logical change per PR

**Avoid:**
- ❌ Vague titles: "Fix stuff" or "Updates"
- ❌ Multiple unrelated changes in one PR
- ❌ No description
- ❌ Breaking changes without discussion

## Code Style

### Markdown Files
- Use clear headings (##, ###)
- Include code blocks with language hints: ```bash, ```json
- Keep line length reasonable (~80-100 chars when possible)
- Use relative links for internal documentation

### Python Scripts (if contributing)
- Follow PEP 8
- Add docstrings to functions
- Include comments for complex logic
- Use meaningful variable names

### Command File (.claude/commands/create-skill.md)
- Use imperative language ("Do this", not "You should do this")
- Include examples
- Keep instructions clear and concise
- Test that Claude can follow the instructions

## Types of Contributions Needed

### High Priority
- [ ] More example skills in `examples/sample-skills/`
- [ ] Video tutorials
- [ ] Improvements to error messages
- [ ] Better validation feedback

### Medium Priority
- [ ] Translations of documentation
- [ ] More workflow examples
- [ ] Integration tests
- [ ] FAQ section

### Nice to Have
- [ ] Skill templates
- [ ] GUI tool for skill creation
- [ ] Skill testing framework
- [ ] Automated skill marketplace

## Questions?

- 💬 [Start a discussion](https://github.com/YOUR_GITHUB_USERNAME/claude-code-skill-creator/discussions)
- 📧 Open an issue with the "question" label
- 📖 Check existing documentation

## Code of Conduct

Be respectful and constructive:
- ✅ Be welcoming to newcomers
- ✅ Provide constructive feedback
- ✅ Focus on the code, not the person
- ✅ Assume good intentions
- ❌ Don't be rude or dismissive
- ❌ Don't harass or discriminate

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Recognition

Contributors will be recognized in:
- GitHub contributors page
- Release notes (for significant contributions)
- CONTRIBUTORS.md file (if we create one)

Thank you for contributing! 🎉
