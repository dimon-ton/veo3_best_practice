# Repository Guidelines

## Project Structure & Module Organization

This is a documentation-only repository. All primary guides live in the root directory as Markdown files. The `research/` folder contains supporting notes and source material.

Examples:
- Root docs: `flow_ai_prompt_guide_tiktok_shop.md`, `image_to_video_workflow.md`, `veo3_tiktok_shop_best_practices.md`
- Research notes: `research/veo3-longer-videos-tiktok-shop-2025-01-14.md`

## Build, Test, and Development Commands

There are no build tools, tests, or runtime commands for this repository. Edits are made directly to Markdown files using your preferred editor.

## Coding Style & Naming Conventions

- **Format**: Markdown only.
- **Headings**: Use clear, hierarchical headings (`#`, `##`, `###`) with short, descriptive titles.
- **Lists**: Prefer bullet lists for steps, checklists, and prompt templates.
- **Bilingual content**: Keep Thai content in Thai docs and English content in English docs; avoid mixing languages within a single section unless required.
- **File names**: Use descriptive, kebab-case filenames for new docs (e.g., `product-demo-prompts.md`).

## Testing Guidelines

No automated tests or validation tooling are used. When editing, manually verify:
- Links resolve correctly.
- Example prompts are complete and copyable.
- TikTok Shop specs remain accurate (9:16, 1080x1920, MP4, 20–60s, <500MB).

## Commit & Pull Request Guidelines

This folder is not a Git repository, so there is no commit history to derive conventions from. If you add Git later, use concise, present-tense commit messages that mention the updated document (e.g., "Update Veo3 workflow prompts").

## Content Focus

Keep edits aligned with the repository’s purpose: practical prompt engineering for Veo 3 video generation, TikTok Shop requirements, and Thailand market context. Provide ready-to-use templates and concrete examples whenever possible.
