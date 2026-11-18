# eed-wiki-template

Cookiecutter template for content-only Obsidian wiki repositories. It creates
a vault with source storage, a structured final wiki, a domain-specific Vibe
skill, and a Dev Container pinned to a prebuilt `eed-wiki-runtime` image.

## Create a wiki

To create a project on the host, install
[Cruft](https://cruft.github.io/cruft/) (Cookiecutter-based, with template
update support) and generate it:

```powershell
pipx install cruft
cruft create https://github.com/EED85/eed-wiki-template
```

Answer the prompts for the project name and slug, domain, language, and runtime
image version. The generated folder is the Obsidian vault. Replace the example
slug below with the one you selected, then initialize the vault as a Git
repository and publish it:

```powershell
Set-Location .\my-knowledge-wiki
git init -b main
git add -A
git commit -m "Create wiki from eed-wiki-template"
gh repo create my-knowledge-wiki --public --source . --remote origin --push
```

The generated project pins the `eed-wiki-runtime` image in
`.devcontainer/devcontainer.json`. The runtime image must be published and
public before opening the vault in a Dev Container. Set `MISTRAL_API_KEY` in
your host environment, then open the project in VS Code and choose **Reopen in
Container**. The project is content-only; it does not build an image.

## Keep an existing wiki up to date

Open the generated wiki in its Dev Container. Cruft is included in the runtime
image, so commit or stash local work first, then run this in the container
terminal from the project directory:

```powershell
cruft update
```

Cruft compares the project with this template and merges upstream changes while
preserving local edits where possible. Review the diff and resolve conflicts
before committing the update. Keep `.cruft.json` in Git; it records the
template reference required for future updates. Vanilla Cookiecutter creates
projects but does not provide this update workflow.

Cruft updates the template-managed files. To move to a newer runtime image,
update the image tag in the generated `.devcontainer/devcontainer.json`
explicitly and commit that change.

The generated domain skill is intentionally small. Keep domain vocabulary,
taxonomy, and language there; defer ingest, query, lint, and Graphify mechanics
to the runtime's global `wiki-hosting` skill.
