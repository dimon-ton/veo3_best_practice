# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **documentation repository** for creating AI-generated videos using Google Veo 3 (Flow.ai) and integrating them with TikTok Shop for e-commerce purposes. The content targets Thailand's market with bilingual support (Thai and English).

## Project Structure & Module Organization

This is a documentation-only repository. Documentation is organized into the `docs/` directory by category. The `research/` folder contains supporting notes and source material.

Structure:
- `docs/guides/`: General concepts and best practices
- `docs/workflows/`: Step-by-step tutorials
- `docs/templates/`: Copy-paste prompt templates
- `research/`: Experimental notes and raw findings

## Key Documentation Files

- **`docs/guides/flow-ai-prompt-guide.md`** (Thai) - Comprehensive prompt writing guide with 8 TikTok Shop templates, Canvas prompting technique, and JSON format examples
- **`docs/guides/tiktok-shop-best-practices.md`** (English) - Complete Veo3 video generation guide, TikTok Shop technical requirements, and Thailand affiliate strategies
- **`docs/workflows/image-to-video-workflow.md`** - Step-by-step workflow for creating videos from images
- **`docs/templates/two-scene-prompts.md`** - Ready-to-use prompt templates for 16-second videos

## Build, Test, and Development Commands

There are no build tools, tests, or runtime commands for this repository. Edits are made directly to Markdown files using your preferred editor.

## Coding Style & Naming Conventions

- **Format**: Markdown only.
- **Headings**: Use clear, hierarchical headings (`#`, `##`, `###`) with short, descriptive titles.
- **Lists**: Prefer bullet lists for steps, checklists, and prompt templates.
- **Bilingual content**: Keep Thai content in Thai docs and English content in English docs; avoid mixing languages within a single section unless required.
- **File names**: Use descriptive, kebab-case filenames for new docs (e.g., `product-demo-prompts.md`).

## Content Focus

When editing or creating documentation in this repository, keep edits aligned with the repository's purpose: practical prompt engineering for Veo 3 video generation, TikTok Shop requirements, and Thailand market context. Provide ready-to-use templates and concrete examples whenever possible.

Key focus areas:
1. **E-commerce Video Creation** - Focus on practical prompt engineering for product videos that convert
2. **Platform Requirements** - TikTok Shop specs: 1080x1920 (9:16 vertical), MP4, 20-60 seconds, under 500MB
3. **Thailand Market** - Include Thai language keywords, cultural references, and local platform nuances
4. **Template-Based** - Provide ready-to-use prompt templates that users can copy and modify

## Language Guidelines

- **Thai content** - Use for Thai-language guides targeting Thailand's TikTok Shop sellers
- **English content** - Use for international audiences and technical documentation
- Maintain consistency with existing bilingual structure

## Testing Guidelines

No automated tests or validation tooling are used. When editing, manually verify:
- Links resolve correctly.
- Example prompts are complete and copyable.
- TikTok Shop specs remain accurate (9:16, 1080x1920, MP4, 20–60s, <500MB).

## Commit & Pull Request Guidelines

This folder is not a Git repository, so there is no commit history to derive conventions from. If you add Git later, use concise, present-tense commit messages that mention the updated document (e.g., "Update Veo3 workflow prompts").

## Architecture

This is a flat documentation repository with all markdown files in the root directory. No build system, dependencies, or code files.
