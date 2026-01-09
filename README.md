# Claude Skills

Custom Claude Code skills for personal productivity and automation.

## Overview

This directory contains custom skills that extend Claude Code's capabilities for specific tasks and workflows.

## Active Skills

### 1. job-application-assistant
**Purpose**: Dynamically tailor professional profiles for different job applications

**Repository**: https://github.com/mklemos/job-application-assistant (private)

**Features**:
- Role-specific framing strategies (Engineering, QA, PM, Sales, Ops, CS)
- Custom cover letter generation
- Resume bullet point tailoring
- Interview preparation materials
- MTM degree positioning guide

**Usage**: `/job-application-assistant`

**Created**: January 8, 2026

---

## Development Standards

⚠️ **All skills in this directory must follow the conventions documented in [CONVENTIONS.md](./CONVENTIONS.md)**

### Quick Rules
1. ✅ Every skill must be in `/Users/max/claude-skills/[skill-name]/`
2. ✅ Every skill must be version controlled with git
3. ✅ Every skill must be pushed to GitHub (private by default)
4. ✅ Every skill must have SKILL.md and README.md
5. ✅ Every skill must have a .gitignore

### Creating a New Skill

```bash
# 1. Create directory
mkdir /Users/max/claude-skills/new-skill-name
cd /Users/max/claude-skills/new-skill-name

# 2. Initialize git
git init

# 3. Create .gitignore
# (see CONVENTIONS.md for template)

# 4. Create skill files
# - SKILL.md
# - README.md
# - references/, assets/, etc.

# 5. Initial commit
git add .
git commit -m "Initial commit: New Skill Name"

# 6. Push to GitHub
gh repo create new-skill-name --private --source=. --push
```

See [CONVENTIONS.md](./CONVENTIONS.md) for complete details.

---

## Directory Structure

```
/Users/max/claude-skills/
├── README.md                         # This file
├── CONVENTIONS.md                    # Development standards
├── job-application-assistant/        # Job application skill
│   ├── .git/                         # Git repository
│   ├── SKILL.md                      # Skill instructions
│   ├── README.md                     # Usage guide
│   ├── references/                   # Supporting data
│   └── assets/                       # Templates
└── [future skills]/
```

---

## Skill Ideas / Backlog

Ideas for future skills:
- Code review assistant
- Documentation generator
- Meeting notes summarizer
- Project planning assistant
- Learning path creator
- [Add your ideas here]

---

**Last Updated**: January 8, 2026
