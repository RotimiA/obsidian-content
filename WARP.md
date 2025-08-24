# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Repository Overview

This is the Modern-Wisdom Obsidian vault - a knowledge management system designed for content creation, note-taking, and organization. It's built on Obsidian.md and uses Git for version control.

## Architecture & Structure

### Core Directory Structure
- `content-vault/` - Main content directory with organized subdirectories
  - `posts/` - Blog posts, articles, and written content
  - `audio/` - Audio recordings and transcripts
  - `dashboards/` - Dashboard notes and overview files
  - `templates/` - Template files for consistent note creation
  - `Untitled/` - Working directory for draft content
- `.obsidian/` - Obsidian configuration and plugins
- `Welcome.md` - Default welcome file

### Plugin Ecosystem

The vault uses several community plugins that enhance functionality:

**Core Community Plugins:**
- `dataview` - Query and display vault data dynamically
- `templater-obsidian` - Advanced templating system
- `obsidian-git` - Git integration for version control
- `obsidian-importer` - Import content from external sources
- `obsidian-linter` - Markdown formatting and style enforcement

**Core Obsidian Features Enabled:**
- File explorer, global search, graph view
- Backlinks and outgoing links
- Daily notes and templates
- Canvas for visual organization
- Audio recorder for voice notes
- Tag pane and bookmarks

## Common Commands

### Git Operations
```bash
# Check repository status
git status

# Stage and commit all changes
git add .
git commit -m "Update notes"

# Push changes to remote (when configured)
git push origin master
```

### Obsidian Vault Management
```bash
# Open vault in Obsidian (from terminal)
open -a "Obsidian" .

# Create new markdown file with proper frontmatter
touch "content-vault/posts/$(date +%Y%m%d)-new-post.md"

# Find all markdown files
find . -name "*.md" -not -path "./.obsidian/*"

# Search content across all notes
grep -r "search term" content-vault/ --include="*.md"
```

### Content Organization
```bash
# Create new post with timestamp
mkdir -p content-vault/posts
echo "# New Post - $(date +%Y-%m-%d)" > "content-vault/posts/$(date +%Y%m%d)-new-post.md"

# Create audio transcription file
mkdir -p content-vault/audio
touch "content-vault/audio/$(date +%Y%m%d)-recording-transcript.md"

# List recent files by modification date
find content-vault/ -name "*.md" -type f -exec ls -t {} + | head -10
```

## Development Workflow

### Content Creation Process
1. Use templates from `content-vault/templates/` for consistent formatting
2. Draft content goes in `content-vault/Untitled/` initially
3. Move finalized content to appropriate subdirectory (`posts/`, `audio/`, etc.)
4. Use Obsidian's linking system `[[note name]]` for connections
5. Apply tags for categorization and discovery

### Git Integration Workflow
The `obsidian-git` plugin enables automatic version control:
- Changes are tracked and can be committed from within Obsidian
- Manual git operations can be performed via terminal
- Supports collaborative workflows when connected to remote repository

### Plugin-Specific Features

**Dataview Queries:** Use dataview syntax for dynamic content lists
```markdown
```dataview
LIST FROM "content-vault/posts"
WHERE date(file.name) > date(today) - dur(30 days)
SORT file.mtime DESC
```

**Templater Usage:** Access advanced templating via command palette (Cmd+P)
- Templates are stored in `content-vault/templates/`
- Use `<% %>` syntax for dynamic content generation

## File Naming Conventions

Based on the vault structure, follow these patterns:
- Posts: `YYYYMMDD-descriptive-title.md`
- Audio: `YYYYMMDD-recording-name.md` or `YYYYMMDD-transcript.md`
- Templates: `template-name.md`
- Dashboards: `dashboard-name.md` or `overview-topic.md`

## Key Features for WARP Users

- **Version Control:** Full git integration means all changes are tracked
- **Plugin Ecosystem:** Rich functionality through community plugins
- **Template System:** Consistent content creation via templater
- **Cross-linking:** Build knowledge graphs with `[[]]` syntax
- **Search & Discovery:** Global search, tags, and dataview queries
- **Audio Integration:** Built-in audio recorder and transcript management
- **Flexible Organization:** Directory-based structure with tag-based discovery

## Working with This Vault

When making changes:
1. Always work within the `content-vault/` directory for content
2. Use existing directory structure (`posts/`, `audio/`, `dashboards/`, `templates/`)
3. Leverage Obsidian's linking and tagging for discoverability
4. Commit changes regularly using git integration or terminal commands
5. Respect the plugin configurations for consistent formatting (linter rules are configured but disabled by default)
