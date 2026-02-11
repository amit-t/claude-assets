# Claude Assets

A comprehensive collection of specialized skills and workflows for Claude AI, organized into modular, domain-specific packages that extend Claude's capabilities across various professional and creative tasks.

## Overview

This repository contains a curated library of Claude skills designed to transform Claude from a general-purpose AI into a specialized agent equipped with domain-specific knowledge, tools, and workflows. Each skill is a self-contained package that provides specialized capabilities for specific use cases.

## Structure

### Skills (`skills/`)

Modular packages organized by domain:

- **AI** (`ai/`) - Agent workflows, MCP builders, prompt engineering, and skill creation tools
- **Design** (`design/`) - Algorithmic art, canvas design, frontend design, and theme creation
- **Marketing** (`marketing/`) - Content creation, social media, email sequences, and profile optimization
- **Product Management** (`product-management/`) - PRD writing, idea validation, and interview guides
- **Tools** (`tools/`) - Document processing (DOCX, PDF, PPTX, XLSX) and file manipulation

### Workflows (`workflows/`)

Pre-configured workflow combinations organized by domain:

- **Marketing** - Complete content creation pipelines with specialized agents and skills
- **AI**, **Design**, **Engineering**, **Leadership**, **Product Management**, **Tools** - Domain-specific workflow templates

## Quick Start

1. Browse the `skills/` directory to find relevant capabilities for your domain
2. Each skill contains:
   - `SKILL.md` - Core instructions and capabilities
   - `scripts/` - Executable tools and utilities
   - `references/` - Documentation and guides
   - `assets/` - Templates and resources

3. Use the skill creator tools in `skills/ai/skill-creator/` to develop new skills

## Skill Categories

**Content & Marketing**: Social media optimization, email sequences, YouTube content creation, business profiles

**Document Processing**: Advanced PDF, DOCX, PPTX, and XLSX manipulation with form handling and formatting

**Design & Creative**: Algorithmic art generation, canvas design with extensive font libraries, theme creation

**AI Development**: MCP server building, agent workflows, prompt engineering patterns

**Product Management**: Requirements documentation, idea validation, customer research

## Development

The repository includes comprehensive tooling for skill development:

- **Skill Creator** - Templates and validation for new skill development
- **MCP Builder** - Tools for creating Model Context Protocol servers
- **Evaluation Scripts** - Testing and quality assurance for skills

## License

Individual skills may have specific licenses. See LICENSE.txt files in each skill directory for details.