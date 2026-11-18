# {{ cookiecutter.project_name }}

An Obsidian vault for {{ cookiecutter.wiki_domain }}. The repository stores
content only; Vibe, Graphify, and the general wiki workflow come from the
pinned `eed-wiki-runtime` Dev Container.

## Layout

- `raw/` stores immutable source files; `raw/assets/` is the Obsidian
  attachment folder.
- `wiki/` contains the maintained, interlinked final wiki.
- `.vibe/skills/{{ cookiecutter.skill_slug }}/SKILL.md` contains only
  domain-specific terminology, taxonomy, and language guidance.
- `graphify-out/` is generated locally and excluded from Git.

Open this repository in VS Code and select **Reopen in Container**. The
container image is pinned to
`ghcr.io/eed85/eed-wiki-runtime:{{ cookiecutter.runtime_image_tag }}` and is
pulled without a local build. Set `MISTRAL_API_KEY` in the host environment
before starting the container. `OPENAI_API_KEY`, `OPENAI_BASE_URL`, and
`OPENAI_MODEL` configure Graphify's OpenAI-compatible document backend.

For general ingestion, querying, linting, and graph workflows, follow the
runtime's `wiki-hosting` skill. Use this project's skill only for domain
conventions.

## Updating the template

This repository was generated from
[eed-wiki-template](https://github.com/EED85/eed-wiki-template). Keep
`.cruft.json` and run `cruft update` to merge template improvements into this
wiki. Review the changes and resolve any conflicts before committing. Local
content and custom domain rules remain the responsibility of this repository.
