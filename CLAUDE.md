# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Mintlify-based documentation site** for the BYU-Idaho Support Agent platform. The documentation covers user guides, AI/RAG learning materials, technical specifications, and resource information. It uses MDX files for content and is deployed automatically through Mintlify's hosting platform.

The Support Agent itself is a separate application (React + TypeScript frontend, Python + FastAPI backend) using the OpenAI Agents SDK, deployed on Azure Container Apps. This repository contains ONLY the documentation.

## Development Commands

### Update CLI

```bash
# Update to latest Mintlify CLI version
mintlify update

# Or reinstall if update command unavailable
npm install -g mintlify@latest
```

### Deployment

Changes are deployed automatically when pushed to the main branch. Mintlify's GitHub App handles CI/CD. No manual deployment commands are needed.

## Project Structure

### Content Organization

```txt
/
├── docs.json              # Mintlify configuration and navigation structure
├── getting-started/       # Quick start guides and overview
├── learn/
│   ├── basics/           # AI fundamentals (RAG, chunking, etc.)
│   └── advanced/         # Advanced topics (docs-as-code, LLM weaknesses)
├── technical/            # Technical specs, infrastructure, release notes
├── resources/            # BYU-Idaho info, beta disclosure, additional resources
├── templates/            # MDX templates for new articles
└── assets/              # Images, logos, and other static assets
```

### Key Files

- **docs.json**: Defines navigation structure, theme, branding, and all site configuration
- **templates/standard-article.mdx**: Template for creating new documentation pages
- **templates/release-template.mdx**: Template for release notes

## Content Architecture

### MDX Frontmatter

**REQUIRED**: Every content file MUST include frontmatter at the top of the file:

```mdx
---
title: Short Title (Title Case)
description: One sentence, attention grabbing description.
---
```

**Frontmatter Rules**:

- `title`: Use Title Case, keep concise and clear
- `description`: Single sentence that captures the essence of the content, engaging and informative

### Navigation Structure

The `docs.json` file controls all navigation through a tab-based structure:

- **Getting Started**: Quickstart and overview
- **Learn**: AI basics and advanced topics (RAG, chunking, docs-as-code)
- **Technical**: Infrastructure, specifications, release notes
- **Resources**: BYU-Idaho info, beta disclosure, additional resources

### Content Guidelines

1. **Use MDX syntax**: Standard Markdown with JSX component support
2. **File naming**: Use kebab-case for all file names (e.g., `what-is-rag.mdx`)
3. **Reference paths**: Always use relative paths from docs.json structure
4. **Images**: Store in `/assets/` or `/img/` directories
5. **Links**: Use normal Markdown syntax. Do NOT include `{:target="_blank"}` (not supported)

### BYU-Idaho Context

**Support Contact Information** (standardized across docs):

- Phone: [208-496-1411](tel:812084961411)
- Email: <ask@byui.edu>
- Hours: Monday-Friday 7:00 AM - 8:00 PM; Saturday 11:00 AM - 8:00 PM (Mountain Time)

**Platform Details**:

- Support Agent URL: <https://supportagent.byui.edu>
- Documentation URL: <https://byui.mintlify.app/>
- Tech Stack: React + TypeScript (frontend), Python + FastAPI (backend)
- AI Framework: OpenAI Agents SDK (GPT-5.2)
- Hosting: Azure Container Apps
- Vector DB: Pinecone
- Authentication: Azure Easy Auth with Okta/Church Login

## Common Tasks

### Creating New Documentation

1. Choose appropriate template from `/templates/`
2. Copy template to correct directory based on content type
3. Update frontmatter with title, description, tags
4. Write content following MDX conventions
5. Add page reference to `docs.json` navigation structure
6. Stage all changes, generate commit message, then commit and push to remote

### Adding to Navigation

Edit `docs.json` and add page reference under the appropriate tab and group:

```json
{
  "group": "Group Name",
  "pages": [
    "folder/new-page"  // Reference without .mdx extension
  ]
}
```

### Editing Release Notes

Release notes follow a specific structure defined in `templates/release-template.mdx` and are stored in `technical/release-notes/`. Include version, date, features, improvements, and fixes.

## Using the Writing Agent

For all content creation, editing, and improvement tasks, use the **writing-agent** subagent. This specialized agent is designed for professional writing and should be your primary tool for documentation work.

### When to Use the Writing Agent

Use the writing-agent for:

- **Creating new documentation pages** from scratch or templates
- **Writing technical content** (specifications, guides, tutorials)
- **Editing existing content** for clarity, tone, and structure
- **Reviewing and refining** drafts for grammar, consistency, and readability
- **Improving documentation** based on user feedback or requirements
- **Rewriting sections** to match BYU-Idaho's voice and style

### How to Invoke the Writing Agent

Use the Task tool with `subagent_type='writing-agent'`:

```txt
Task(
  subagent_type='writing-agent',
  description='Create new RAG tutorial',
  prompt='Create a comprehensive tutorial page about RAG (Retrieval-Augmented Generation)
         for the learn/basics/ directory. Target audience is students unfamiliar with AI.
         Include practical examples and follow the standard-article.mdx template structure.'
)
```

### Best Practices

1. **Be Specific**: Provide clear context about the content type, target audience, and desired outcome
2. **Reference Templates**: Point the agent to relevant templates (`templates/standard-article.mdx`)
3. **Specify Location**: Indicate which directory the content belongs in
4. **Include Guidelines**: Mention tone (professional, educational), length, and key points to cover
5. **Provide Context**: Share existing related documentation or requirements

### Example Invocations

**Creating New Content:**

```txt
"Use the writing-agent to create a new page in learn/advanced/ about vector embeddings.
Target audience: technical users familiar with AI basics. Follow standard-article template.
Include examples relevant to the Support Agent's Pinecone implementation."
```

**Editing Existing Content:**

```txt
"Use the writing-agent to review and improve technical/infrastructure.mdx.
Focus on clarity for non-technical stakeholders. Ensure all Azure service names are accurate.
Maintain professional tone consistent with BYU-Idaho standards."
```

**Refining Release Notes:**

```txt
"Use the writing-agent to draft release notes for the December 2025 update.
Include: new multi-language support, improved response accuracy, bug fixes for mobile layout.
Follow templates/release-template.mdx structure."
```

### Writing Agent Context

When invoking the writing-agent, it will have access to:

- All documentation files in the repository
- Templates and style guides
- BYU-Idaho context and standards
- Technical specifications and architecture docs

The agent will ensure:

- **Required frontmatter** at the top of every file with proper title and description
- Consistency with existing documentation tone and style
- Proper MDX formatting and syntax
- Accuracy of technical details
- Adherence to BYU-Idaho branding and voice
- Professional, clear, and accessible writing

**Critical**: Every article created or edited by the writing-agent MUST include frontmatter:

```mdx
---
title: Short Title (Title Case)
description: One sentence, attention grabbing description.
---
```

## Important Notes

### Docs-as-Code Workflow

This project follows a docs-as-code methodology:

- Documentation lives in version control (Git)
- Changes go through pull requests and review
- Automated deployment on merge to main
- Plain text (MDX) for all content
- CI/CD for validation and publishing

### Mintlify-Specific Features

- Automatic OpenAPI spec integration support
- Built-in search functionality
- Contextual actions (copy, ChatGPT, Claude, Perplexity)
- Feedback system (thumbs rating, suggest edits, raise issues)
- Preview deployments for pull requests (Pro plan)

### Content Focus Areas

Documentation covers three main domains:

1. **User Education**: How to use the Support Agent (getting started guides)
2. **AI/RAG Concepts**: Educational content about AI, RAG, chunking, and best practices
3. **Technical Details**: Infrastructure, specifications, and release information

### File Organization

- All content uses `.mdx` extension (not `.md`)
- Assets go in `/assets/` directory
- Templates are reference materials, not directly deployed
- Navigation is explicit in `docs.json` (files not auto-discovered)
