---
name: {{ cookiecutter.skill_slug }}
description: Use when creating or updating pages in the {{ cookiecutter.project_name }} wiki; provides domain-specific terminology, taxonomy, and language preferences.
---

# {{ cookiecutter.project_name }}

This project skill contains only domain-specific guidance. Follow the
runtime's global `wiki-hosting` skill for source ingestion, wiki maintenance,
queries, linting, and Graphify operations.

## Domain

- Subject: {{ cookiecutter.wiki_domain }}
- Preferred language: {{ cookiecutter.wiki_language }}
- Final wiki: `wiki/`
- Immutable source files and attachments: `raw/`

## Taxonomy and terminology

Add the domain's preferred terms, categories, and naming conventions here.
Keep durable wiki pages in `wiki/entities/`, `wiki/concepts/`, or
`wiki/synthesis/`, and update `wiki/index.md` when adding pages.
