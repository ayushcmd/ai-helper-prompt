<div align="center">

# AI Helper Prompt

**A curated collection of AI prompts for developer workflows, with a lightweight GitHub-powered text editor.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Repo](https://img.shields.io/badge/GitHub-ayushcmd%2Fai--helper--prompt-181717?logo=github)](https://github.com/ayushcmd/ai-helper-prompt)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

</div>

## Overview

AI Helper Prompt is a repository of reusable instructions for AI-assisted software development. Its prompt files cover tasks such as refactoring, code reviews, security analysis, technical documentation, and GitHub project maintenance.

The repository also includes **TXT // EDITOR**, a static, browser-based interface in [`index.html`](index.html) that can browse and edit supported text files in a GitHub repository using the GitHub REST API.

> [!NOTE]
> The prompts are text templates intended to be pasted into an AI assistant alongside your own code or project context. The repository does **not** currently include an integrated AI model, automatic prompt optimizer, or autonomous agent.

## Features

### Prompt collection

- Reusable prompts for software engineering and repository workflows.
- Instructions for modularization, Clean Code and SOLID refactoring.
- Prompts for code documentation, API references and GitHub README content.
- Security review prompts and specialized development tasks.
- Plain-text files that can be copied, edited, and adapted to different projects.

### TXT // EDITOR

- Browse a GitHub repository's folders and supported text files.
- Open and copy the contents of a selected file.
- Edit existing files and commit changes through the GitHub API.
- Create new files using a GitHub personal access token (PAT).
- Select the repository owner, name and branch.
- Remember the selected repository settings in the browser.

The editor currently displays files ending in `.txt`, `.md`, `.csv`, `.json`, `.js`, `.html`, or `.css`. Other formats are not included in its file browser.

## Repository layout

```text
ai-helper-prompt/
├── index.html             # Browser-based GitHub TXT editor
├── GirHub/                # GitHub and repository-maintenance prompts
│   └── readme/            # README, API and documentation prompts
├── Vibe_code/             # Refactoring and code-review prompts
├── Доп_код/               # Additional development prompts
├── adwmg/                 # Additional snippets and assets
├── Additional files/      # Additional documentation and assets
├── CONTRIBUTING.md        # Contribution guidelines
├── SECURITY.md            # Vulnerability reporting policy
└── LICENSE                # MIT License
```

This tree highlights the main parts of the project rather than every individual file.

## Getting started

### Use a prompt

1. Browse a category folder on GitHub.
2. Open a `.txt` prompt that matches your task.
3. Copy it into your preferred AI assistant.
4. Include the relevant source code, constraints, or project description requested by that prompt.
5. Review and test any AI-generated code before using it.

### Run the text editor locally

The editor is a standalone HTML page; no package installation or build step is required.

```bash
git clone https://github.com/ayushcmd/ai-helper-prompt.git
cd ai-helper-prompt
python -m http.server 8000
```

Open `http://localhost:8000` in your browser. You can also open `index.html` directly, but running it through a local HTTP server is a more consistent option.

In the editor, enter:

- **User:** the GitHub repository owner's username.
- **Repo:** the repository name, without the owner prefix.
- **Branch:** the target branch (defaults to `main`).
- **Token (PAT):** optional when reading public repositories; required to create or save files.

Click **Load Files**, select a folder and then a file. Use **Copy Content** to copy it or **Edit** and **Save** to commit an update when authenticated. The **+ New** control creates a file at a path you provide.

> [!IMPORTANT]
> Saving or creating files writes directly to the selected GitHub branch. For proposed changes, work on a dedicated branch and submit a pull request instead of editing the default branch directly.

## Authentication and security

The current editor sends requests directly from your browser to the GitHub REST API. A PAT is needed for write operations; read-only access to public repositories generally does not require a token, subject to GitHub API limits.

**Known limitation:** the existing implementation saves the PAT in browser `localStorage` as `txtEditor_token` and restores it on later visits. This means the token persists locally and may be exposed to other scripts with access to the same origin. Avoid using the editor with a high-privilege or long-lived token, particularly on shared devices or untrusted deployments.

If you use a token, prefer a short-lived, fine-grained token scoped to the specific repository with only the necessary repository contents permissions. Clear the saved token when finished. A safer authentication and token-storage approach is planned, but **is not implemented yet**.

Never commit tokens, credentials or private code into this repository. See [SECURITY.md](SECURITY.md) for responsible vulnerability reporting.

## Limitations

- Prompt files are not automatically executed or refined by an AI model.
- Search, filters, favorites, reusable placeholder forms and prompt version history are not currently built into the editor.
- The editor does not provide a dedicated file-delete control or a pull-request creation workflow.
- Its desktop-oriented three-column layout has limited mobile optimization.
- File updates may fail if a file has changed remotely since it was loaded; reload before retrying.

## Roadmap

The following are **planned improvements**, not currently available features:

- [ ] Improve PAT handling and authentication safety.
- [ ] Add repository and prompt search, tags and category filters.
- [ ] Introduce a responsive prompt-library dashboard.
- [ ] Add favorites, recent prompts and better file-editing feedback.
- [ ] Support reusable prompt variables and template metadata.
- [ ] Add prompt import/export and improved version management.
- [ ] Explore optional AI-assisted prompt refinement.
- [ ] Add automated tests and stronger documentation for maintainers.

Suggestions and implementation proposals are welcome through [GitHub Issues](https://github.com/ayushcmd/ai-helper-prompt/issues).

## Contributing

Bug reports, improvements to existing prompts, new prompt templates, usability fixes and documentation contributions are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a pull request.

When adding a prompt, use a descriptive filename and make the instructions explicit about their inputs, desired outputs and constraints. Avoid adding personal information or secrets to example prompts.

## License

Distributed under the **MIT License**. See [LICENSE](LICENSE) for the complete license text.

---

Maintained by [@ayushcmd](https://github.com/ayushcmd).
