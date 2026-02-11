# GitHub Copilot Skills

Expert skills that teach GitHub Copilot how to use specialized tools and follow best practices.

## Install

**Windows:**
```powershell
git clone https://github.com/shepherd-source/github-copilot-skills.git
Copy-Item "github-copilot-skills\skills\*" "$env:USERPROFILE\.copilot\skills\" -Recurse
```

**macOS/Linux:**
```bash
git clone https://github.com/shepherd-source/github-copilot-skills.git
cp -r github-copilot-skills/skills/* ~/.copilot/skills/
```

Restart VS Code, then ask Copilot: *"Convert this Markdown to PDF"*

## Skills

### [Pandoc](skills/pandoc/) - Universal Document Converter

Converts between 40+ formats with proper syntax, troubleshooting, and real-world examples.

**Try it:**
- "Convert doc.md to PDF with table of contents"
- "Create a reveal.js presentation from slides.md"
- "Generate an EPUB book with citations from paper.md"

**Requires:** [Pandoc](https://pandoc.org/installing.html)

## License

MIT
