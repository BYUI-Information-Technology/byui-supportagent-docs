# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Mintlify-based documentation site** for the BYU-Idaho Support Agent platform. The primary audience for this documentation site are the students, faculty, staff, and administrators at Brigham Young University-Idaho. The documentation covers user guides, AI/RAG learning materials, technical specifications, and resource information. It uses MDX files for content and is deployed automatically through Mintlify's hosting platform.

The Support Agent itself is a separate application (React + TypeScript frontend, Python + FastAPI backend) using the OpenAI Agents SDK, deployed on Azure Container Apps (available at [supportagent.byui.edu](https://supportagent.byui.edu/)). This repository contains ONLY the documentation.

## Content Overview

The documentation is organized into five main navigation sections, each serving a distinct purpose and audience:

### 1. Getting Started (`getting-started/`)

**Purpose:** First-time user onboarding and platform introduction.

**Current Content:** Quick start guides, platform overview, multi-agent architecture explanation, access instructions, and what makes the Support Agent special.

**Target Audience:** New users (students, faculty, staff) encountering the Support Agent for the first time.

**Vision:** Minimize time-to-value by helping users understand what the Support Agent is, how to access it, and how to get the most out of it. Content should answer: "What is this?", "Why should I use it?", and "How do I get started?"

**Content Types:** Overviews, quick start guides, feature highlights, FAQs for new users.

### 2. Learn

Educational content helping users understand AI concepts, technology, and best practices. Organized by complexity and topic.

#### 2a. Basics of Artificial Intelligence (`learn/basics/`)

**Purpose:** Foundational AI concepts for complete beginners.

**Current Content:** How LLMs are trained, model alignment, context windows, hallucinations, basic AI terminology.

**Target Audience:** Students and users with little to no AI background who want to understand how the technology works.

**Vision:** Demystify AI technology through accessible, jargon-free explanations. Build foundational knowledge that helps users become more effective AI users. Each article should answer one fundamental question about how AI works, using university-relevant examples. Topics should be self-contained but cross-reference related concepts.

**Future Topics:** Prompt engineering basics, tokens and tokenization, temperature and randomness, AI safety and ethics, understanding AI limitations, how AI "thinks" vs. human thinking.

#### 2b. Advanced Topics (`learn/advanced/`)

**Purpose:** Complex AI concepts for users with foundational knowledge.

**Current Content:** Docs-as-code methodology, LLM weaknesses and vulnerabilities, advanced patterns.

**Target Audience:** Technical users, developers, IT staff, and curious students who want deeper understanding.

**Vision:** Provide nuanced, technical explanations of AI system design, limitations, and advanced use cases. Content should help users understand not just how things work, but why design decisions were made and what tradeoffs exist. Suitable for those making technology decisions or building AI-integrated systems.

**Future Topics:** Vector embeddings deep dive, semantic search architecture, AI system observability and monitoring, multi-agent orchestration patterns, prompt injection and security, fine-tuning vs. RAG tradeoffs, production AI system design.

#### 2c. Retrieval Augmentation (`learn/rag/`)

**Purpose:** Deep dive into RAG (Retrieval-Augmented Generation) technology powering the Support Agent.

**Current Content:** What is RAG, chunking strategies, how RAG improves accuracy.

**Target Audience:** Users curious about how the Support Agent retrieves accurate information, developers building similar systems.

**Vision:** Make RAG technology understandable and demystify how the Support Agent stays accurate. Help readers understand why RAG is effective at reducing hallucinations and how it differs from base LLMs. Content should connect technical concepts to user-facing benefits.

**Future Topics:** Vector databases explained, embedding models, semantic vs. keyword search, chunk size optimization, retrieval strategies (dense, sparse, hybrid), re-ranking techniques, knowledge base management, RAG evaluation metrics.

#### 2d. Tips & Tricks (`learn/tips-tricks/`)

**Purpose:** Practical advice for getting better results from AI systems.

**Current Content:** To be developed - prompt engineering techniques, effective questioning strategies, troubleshooting common issues.

**Target Audience:** All users who want to improve their AI interaction skills.

**Vision:** Actionable, practical guidance that immediately improves user experience. Think "cookbook" style: specific problems with specific solutions. Focus on patterns users encounter daily with the Support Agent and how to handle them effectively.

**Future Topics:** Writing better prompts, asking follow-up questions, when to escalate to humans, handling ambiguous responses, verifying AI answers, using the Support Agent for research, best practices by use case (registration help, policy questions, technical support).

### 3. Technical (`technical/`)

**Purpose:** Technical specifications, architecture documentation, and system details.

**Current Content:** Infrastructure overview, system architecture, technology stack details, API documentation (if applicable).

**Target Audience:** Developers, IT staff, technical stakeholders, governance teams, and integration partners.

**Vision:** Provide complete technical transparency for those who need to understand how the system works, integrate with it, audit it, or maintain it. Should answer questions from IT professionals, developers, and technical decision-makers.

**Future Topics:** API documentation, webhook integrations, system architecture diagrams, data flow documentation, security and compliance details, disaster recovery, performance metrics, scalability documentation.

### 4. Release Notes (`technical/release-notes/`)

**Purpose:** Version history and changelog tracking.

**Current Content:** Chronological release documentation with version numbers, dates, features, improvements, bug fixes.

**Target Audience:** All users who want to know what's new, IT staff tracking changes, governance teams monitoring updates.

**Vision:** Transparent communication about platform evolution. Each release should clearly communicate what changed, why it matters, and any action users need to take. Follow semantic versioning and maintain clear, scannable format.

**Format:** Follow `templates/release-template.mdx` structure. Include version number, release date, categories (Features, Improvements, Bug Fixes, Breaking Changes if applicable), and link to relevant documentation for new features.

### 5. Resources (`resources/`)

**Purpose:** Supplementary information, institutional context, and additional support materials.

**Current Content:** BYU-Idaho specific information, beta program disclosure, contact information, external resources.

**Target Audience:** All users seeking additional context, legal information, or alternative support channels.

**Vision:** Provide institutional context, legal disclosures, contact information, and resources that don't fit other categories. Include information about BYU-Idaho, the AI initiative, governance, privacy policies, and how to get help beyond the Support Agent.

**Future Topics:** AI governance at BYU-Idaho, privacy and data policies, accessibility information, training resources, feedback channels, roadmap and future plans, research and publications, case studies.

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

## Content Creation Workflow

### Research-Based Content Creation

When creating content that requires research or exploration of complex topics, follow this two-stage workflow:

#### Stage 1: Research

Use the **Explore** or **general-purpose** subagent to gather information, understand the topic, and collect relevant details.

**When to use research workflow:**

- Creating content about new or unfamiliar topics
- Exploring technical concepts that require investigation
- Gathering examples, use cases, or best practices
- Understanding how existing systems or technologies work
- Finding relevant sources and references

**How to invoke:**

```txt
Task(
  subagent_type='Explore',  // or 'general-purpose' for complex research
  description='Research vector embeddings',
  prompt='Research vector embeddings and how they work in RAG systems.
         Focus on: what they are, how they're generated, why they're useful for semantic search,
         and how they're used in the Support Agent. Gather technical details but also
         beginner-friendly explanations. Find relevant examples and analogies.'
)
```

#### Stage 2: Writing

After research is complete, use the **writing-agent** to create the article based on the research findings.

**Critical Requirements:**

1. **Audience-Appropriate Content** - Tailor complexity to the target section:
   - `learn/basics/` - Beginner level, jargon-free, foundational concepts
   - `learn/advanced/` - Technical depth, assumes AI knowledge
   - `learn/rag/` - Moderate technical level, focused on RAG concepts
   - `learn/tips-tricks/` - Practical, actionable, all skill levels
   - `technical/` - Technical audience, developers and IT staff

2. **BYU-Idaho Context** - Always frame content for BYU-Idaho students and employees:
   - Use university-relevant examples (registration, campus systems, student scenarios)
   - Reference the Support Agent where applicable
   - Connect concepts to how they impact the BYU-Idaho experience
   - Maintain institutional voice and values

**How to invoke:**

```txt
Task(
  subagent_type='writing-agent',
  description='Write vector embeddings article',
  prompt='Based on the research about vector embeddings, create a comprehensive article
         for learn/basics/ directory.

         RESEARCH CONTEXT: [Paste or reference key findings from research stage]

         TARGET AUDIENCE: Complete beginners (learn/basics/) - BYU-Idaho students with
         no AI background who want to understand how the Support Agent works.

         REQUIREMENTS:
         - Explain vector embeddings in beginner-friendly language
         - Use university-relevant analogies (library search, student records, etc.)
         - Connect to how the Support Agent uses embeddings
         - Include link to related RAG article
         - Follow standard-article.mdx template
         - Include required frontmatter

         TONE: Educational, accessible, professional - appropriate for BYU-Idaho documentation.'
)
```

#### Example Research-to-Writing Workflow

**User Request:** "Create an article about prompt engineering for the Tips & Tricks section"

**Step 1 - Research:**

```txt
Task(
  subagent_type='general-purpose',
  description='Research prompt engineering techniques',
  prompt='Research prompt engineering best practices, common techniques, and strategies
         for getting better AI responses. Focus on practical techniques students can use
         with the Support Agent. Gather examples of good vs. bad prompts.'
)
```

**Step 2 - Writing:**

```txt
Task(
  subagent_type='writing-agent',
  description='Write prompt engineering guide',
  prompt='Create a practical prompt engineering guide for learn/tips-tricks/ directory.

         RESEARCH FINDINGS: [Include key research findings about prompt engineering]

         TARGET AUDIENCE: All skill levels (tips-tricks section) - BYU-Idaho students
         and employees who want to get better results from the Support Agent.

         FOCUS: "Cookbook style" - specific problems with specific solutions
         - How to write clear, specific questions
         - Adding context to prompts
         - Breaking complex questions into parts
         - Examples using BYU-Idaho scenarios (registration, financial aid, etc.)

         Include before/after examples showing weak prompts improved to strong prompts.
         Reference the Support Agent throughout.
         Follow standard-article.mdx template.'
)
```

### Single-Stage Writing (No Research Required)

For straightforward content where research isn't needed, proceed directly to the writing-agent.

**When to skip research:**

- Editing or improving existing content
- Writing about well-understood topics
- Creating content based on user-provided information
- Drafting release notes or documentation updates

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
5. **Provide