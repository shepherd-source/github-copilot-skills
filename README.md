# GitHub Copilot Skills

> A curated collection of specialized skills for GitHub Copilot that extend its capabilities with domain-specific knowledge, workflows, and tool integrations.

## 🚀 Quick Start

### Installation

Copy skills to your Copilot skills directory:

**Windows:**
```powershell
git clone https://github.com/shepherd-source/github-copilot-skills.git
Copy-Item -Path "github-copilot-skills\skills\*" -Destination "$env:USERPROFILE\.copilot\skills\" -Recurse
```

**macOS/Linux:**
```bash
git clone https://github.com/shepherd-source/github-copilot-skills.git
cp -r github-copilot-skills/skills/* ~/.copilot/skills/
```

Then restart VS Code.

### Using Skills

Skills activate automatically based on your context. For example:
- **"Convert this Markdown to PDF"** → activates `pandoc` skill
- **"Create a presentation from these slides"** → activates `pandoc` skill

## 📚 Available Skills

| Skill | Description | Prerequisites |
|-------|-------------|---------------|
| **[pandoc](skills/pandoc/)** | Universal document converter supporting 40+ formats: Markdown, PDF, Word, HTML, LaTeX, EPUB, PowerPoint, and more | [Pandoc](https://pandoc.org/installing.html) |

## 💡 What Are Skills?

Skills teach GitHub Copilot how to:
- Use specialized tools and CLIs effectively
- Follow domain-specific best practices  
- Execute complex multi-step workflows
- Apply industry standards automatically

Each skill includes comprehensive documentation, command references, examples, and troubleshooting guides.

## 🎯 How Skills Work

Skills are loaded by GitHub Copilot when relevant to your request. They provide:
- **Tool expertise** - Deep knowledge of specific CLIs and tools
- **Workflow automation** - Multi-step processes executed correctly
- **Best practices** - Industry standards applied automatically
- **Examples & troubleshooting** - Practical guidance for common scenarios

## 🤝 Contributing

Contributions welcome! To add a skill:

1. Fork this repository
2. Create `skills/your-skill-name/SKILL.md`
3. Include frontmatter with `name` and `description`
4. Add comprehensive documentation with examples
5. Submit a pull request

See existing skills for structure and formatting examples.

## 📖 Creating Your Own Skills

Each skill follows this structure:

```markdown
---
name: skill-name
description: Brief description of what the skill does and when to use it
---

# Skill Title

Comprehensive documentation...
```

Place your skill file at: `skills/skill-name/SKILL.md`

## 📜 License

MIT License

## 🌟 Star This Repo

If you find these skills helpful, please ⭐ star this repository!

---

**More skills coming soon!** Watch this repo for updates.
