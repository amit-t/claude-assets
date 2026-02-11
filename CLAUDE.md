# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Structure

This is a collection of Claude skills and workflows organized by domain. Skills are reusable capabilities, workflows are multi-skill orchestrated processes.

### Key Directories
- `skills/` - Domain-organized capabilities (ai, design, marketing, tools, etc.)
- `workflows/` - Multi-skill processes organized by same domains

## Architecture Overview

### Skills Structure
Skills follow a standard pattern:
- `SKILL.md` - Main definition with description and process steps
- `scripts/` - Executable utilities (Python/JavaScript)
- `reference/` - Supporting documentation and guides
- `templates/` - Reusable templates

### Critical Skills

**MCP Builder (`skills/ai/mcp-builder/`)**
- Creates Model Context Protocol servers for LLM tool integration
- 4-phase process: Research → Implementation → Review → Evaluation
- Evaluation harness: `scripts/evaluation.py`
- Dependencies: `anthropic>=0.39.0`, `mcp>=1.1.0`

**Document Tools (`skills/tools/`)**
- DOCX: Complete document manipulation with tracked changes
- PDF: Form processing and field extraction  
- PPTX: Presentation editing and HTML conversion
- XLSX: Spreadsheet recalculation

## Common Commands

### MCP Development
```bash
# Evaluate MCP server
python skills/ai/mcp-builder/scripts/evaluation.py -t stdio -c python -a server.py eval.xml

# Test with MCP Inspector
npx @modelcontextprotocol/inspector
```

### Document Processing
```bash
# DOCX workflow
python skills/tools/docx/ooxml/scripts/unpack.py file.docx output_dir/
python skills/tools/docx/ooxml/scripts/pack.py input_dir/ output.docx

# Convert to markdown (preserves tracked changes)
pandoc --track-changes=all document.docx -o output.md

# Document to images
soffice --headless --convert-to pdf document.docx
pdftoppm -jpeg -r 150 document.pdf page
```

### Python Dependencies
```bash
# Install MCP requirements
pip install anthropic>=0.39.0 mcp>=1.1.0

# Install GIF creator requirements  
pip install pillow>=10.0.0 imageio>=2.31.0 imageio-ffmpeg>=0.4.9 numpy>=1.24.0
```

## Development Patterns

### Working with Documents
1. Read complete `SKILL.md` before starting (critical for DOCX/PDF workflows)
2. For DOCX edits: Use redlining workflow for tracked changes
3. Follow unpack → edit → pack cycle for complex modifications

### MCP Server Development
1. Read `skills/ai/mcp-builder/SKILL.md` completely for 4-phase process
2. Load framework docs via WebFetch (TypeScript/Python SDK README files)
3. Prioritize comprehensive API coverage over workflow-specific tools
4. Create 10 evaluation questions using `reference/evaluation.md` guide

### Skill Creation
- Use `skills/ai/skill-creator/scripts/` for packaging and validation
- Follow domain organization (ai, design, marketing, tools, etc.)
- Include proper `SKILL.md` with description, process steps, and examples