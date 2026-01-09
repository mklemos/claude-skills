# Claude Skills - Development Conventions

## Directory Structure Standard

All custom Claude Code skills must be created in:
```
/Users/max/claude-skills/
```

Each skill should be in its own subdirectory:
```
/Users/max/claude-skills/             # Parent git repo (PUBLIC)
├── .git/                             # Tracks conventions/registry only
├── .gitignore                        # Excludes all subdirectories (*/  )
├── README.md                         # Skill registry
├── CONVENTIONS.md                    # This file
├── skill-name-1/                     # Independent git repo (PRIVATE)
│   ├── .git/                         # Own git history
│   ├── SKILL.md                      # Main skill instructions
│   ├── README.md                     # Usage documentation
│   └── .gitignore                    # Git exclusions
└── skill-name-2/                     # Another independent git repo
    └── ...
```

### Nested Repository Approach

**Important**: This directory uses nested git repositories intentionally:

- **Parent repo** (`/Users/max/claude-skills/.git`):
  - Tracks: README.md, CONVENTIONS.md (registry/standards)
  - Ignores: All subdirectories (`*/` in .gitignore)
  - Purpose: Version control for conventions
  - Visibility: PUBLIC (no personal data)

- **Child repos** (e.g., `job-application-assistant/.git`):
  - Completely independent repositories
  - Own git history, own GitHub remote
  - Purpose: Version control for individual skills
  - Visibility: PRIVATE by default (contains personal data)

**Why this works**:
- Parent's `.gitignore` contains `*/` which excludes all subdirectories
- Each skill repo is isolated and doesn't interfere with parent
- Provides organized directory structure + separate version control
- Conventions are public, skills are private

**When working**:
- `cd /Users/max/claude-skills && git status` → shows conventions only
- `cd /Users/max/claude-skills/skill-name && git status` → shows skill only

## Version Control Requirements

### Every skill MUST be version controlled:

1. **Initialize Git** on creation:
   ```bash
   cd /Users/max/claude-skills/new-skill-name
   git init
   ```

2. **Create .gitignore** before first commit:
   - Exclude large files
   - Exclude sensitive data
   - Exclude OS/IDE files
   - Exclude cache/temp files

3. **Make initial commit**:
   ```bash
   git add .
   git commit -m "Initial commit: [Skill Name]"
   ```

4. **Push to GitHub** (private by default):
   ```bash
   gh repo create skill-name --private --source=. --description "Description" --push
   ```

### Why Version Control?

- ✅ Track changes over time
- ✅ Revert mistakes easily
- ✅ Backup to GitHub
- ✅ Access from any machine
- ✅ Document evolution with commit messages
- ✅ Branch for experiments

## Skill Structure Standards

### Required Files

Every skill must have:

1. **SKILL.md** - Main instructions for Claude Code
   - YAML metadata header
   - Clear description of what the skill does
   - Reference materials list
   - Output format specification

2. **README.md** - User-facing documentation
   - How to use the skill
   - Example usage
   - Configuration options
   - Troubleshooting

3. **.gitignore** - Version control exclusions
   - At minimum: OS files, cache, sensitive data

### Recommended Structure

```
skill-name/
├── SKILL.md                          # Main skill instructions
├── README.md                         # Usage guide
├── .gitignore                        # Git exclusions
├── references/                       # Supporting data/context
│   └── *.md
├── assets/                           # Templates, examples
│   └── *.md
└── [skill-specific directories]
```

## Naming Conventions

### Directory Names
- Use lowercase with hyphens: `job-application-assistant`
- Be descriptive but concise
- Avoid abbreviations unless widely understood

### File Names
- Use lowercase with hyphens for multi-word names
- Markdown files: `*.md`
- Data files: descriptive names with appropriate extensions

### Git Commit Messages
- Start with verb: "Add", "Update", "Fix", "Improve", "Remove"
- Be specific: "Update profile with Q1 2026 experience"
- Not generic: "Updates" or "Changes"

## Security & Privacy

### Default to Private
All skills containing personal information should be **private GitHub repositories** by default.

### .gitignore Essentials
Always exclude:
- Personal documents (PDFs, etc.)
- API keys, secrets, credentials
- Large data files (can be regenerated)
- System files (.DS_Store, etc.)
- Cache directories

## Development Workflow

### Creating a New Skill

1. **Create directory**:
   ```bash
   mkdir -p /Users/max/claude-skills/new-skill-name
   cd /Users/max/claude-skills/new-skill-name
   ```

2. **Initialize git**:
   ```bash
   git init
   ```

3. **Create .gitignore** (before adding files):
   ```bash
   # Create .gitignore with common exclusions
   ```

4. **Develop skill files**:
   - SKILL.md
   - README.md
   - references/, assets/, etc.

5. **Initial commit**:
   ```bash
   git add .
   git commit -m "Initial commit: [Skill Name]"
   ```

6. **Push to GitHub**:
   ```bash
   gh repo create skill-name --private --source=. --push
   ```

### Updating an Existing Skill

1. **Make changes** to files

2. **Review changes**:
   ```bash
   git status
   git diff
   ```

3. **Commit with descriptive message**:
   ```bash
   git add [files]
   git commit -m "Update: description of changes"
   ```

4. **Push to GitHub**:
   ```bash
   git push
   ```

## Testing New Skills

Before considering a skill "complete":

1. ✅ Test with real-world example
2. ✅ Verify all reference files are accessible
3. ✅ Check for typos and broken links
4. ✅ Ensure .gitignore excludes sensitive data
5. ✅ Confirm GitHub repo is private (if needed)
6. ✅ Document usage in README.md

## Maintenance

### Regular Updates
- Update skills when circumstances change (new job, new projects, etc.)
- Commit changes with clear messages
- Push to GitHub regularly

### Deprecation
If a skill becomes obsolete:
1. Add "DEPRECATED" to README.md
2. Document why and what to use instead
3. Keep in git history but archive GitHub repo

## Example .gitignore Template

```gitignore
# Personal/Sensitive Files
*.pdf
*.docx
secrets/
private/
credentials/

# Large Data Files
data/
exports/
backups/

# OS Files
.DS_Store
.DS_Store?
._*
Thumbs.db

# IDE/Editor
.vscode/
.idea/
*.swp
*.swo

# Cache
__pycache__/
*.pyc
node_modules/
.cache/

# Logs
*.log
```

## Git Best Practices

### Commit Messages
- **Good**: "Add framing strategies for PM roles"
- **Good**: "Update profile with UCSB graduation date"
- **Bad**: "Updates"
- **Bad**: "WIP"

### When to Commit
- After completing a logical unit of work
- Before trying risky changes (so you can revert)
- When adding new features
- When fixing bugs

### Branches
- `master` - stable, working version
- `experiment` - trying new approaches
- `update-YYYY-MM` - major updates

## Repository Settings

### GitHub Repository Checklist
- [ ] Private visibility (for personal skills)
- [ ] Descriptive name
- [ ] Clear description
- [ ] README.md visible on GitHub
- [ ] .gitignore excludes sensitive data
- [ ] Regular commits pushed

## Skill Registry

Maintain a list of active skills:

### Active Skills
1. **job-application-assistant**
   - Repository: https://github.com/mklemos/job-application-assistant
   - Purpose: Dynamically tailor professional profiles for job applications
   - Created: January 8, 2026
   - Status: Active

### Planned Skills
<!-- Add planned skills here -->

### Archived Skills
<!-- Skills no longer in use -->

---

## Quick Reference

```bash
# Create new skill
mkdir /Users/max/claude-skills/new-skill && cd $_
git init
# [create files]
git add .
git commit -m "Initial commit: New Skill"
gh repo create new-skill --private --source=. --push

# Update existing skill
cd /Users/max/claude-skills/existing-skill
# [make changes]
git add .
git commit -m "Update: description"
git push
```

---

**Last Updated**: January 8, 2026
**Maintained By**: Max Klemos
