# 🧱 Hello World

> Every project has a story. This one begins not with a book, but with a problem.

This is a tribute to beginnings.

In every language, in every framework, "Hello, world" is the first spark — the moment code speaks back. This sample book is your invitation to begin — to build something real, reproducible, and yours.

This project demonstrates the basic structure and functionality of a Keystone-based book. Study this repository or fork it to experiment on your own.

## Getting Started

To get started with this sample:

```bash
git clone https://github.com/knight-owl-dev/keystone-hello-world.git
cd keystone-hello-world
make all
```

## Keystone Template Variants

This project was created using the [keystone-template-core-slim](https://github.com/knight-owl-dev/keystone-template-core-slim) Keystone template — the editor-agnostic version that uses a prebuilt Docker image. Choose this variant if you want faster builds, smaller images, and don't need to modify publishing internals.

Looking for a more integrated experience? Consider using the [keystone-template-core](https://github.com/knight-owl-dev/keystone-template-core) variant for more control and flexibility, or if you need to customize Pandoc.

### Requirements

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [GNU Make](https://www.gnu.org/software/make/)
- Learn the [Markdown](https://www.markdownguide.org/basic-syntax/) basic syntax
- Use any editor or IDE of your choice

### Cross-Platform Compatibility & Line Endings

If you're using Windows, run this project inside [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) for full compatibility. Keystone requires `LF` (Unix-style) line endings — this is enforced by [.editorconfig](/.editorconfig). Avoid `CRLF` endings to prevent formatting and build issues.

### Using the GNU Make Utility

This project has the [Makefile](Makefile) to simplify the workflow and assumes [Docker Desktop](https://www.docker.com/products/docker-desktop/) is installed.

> 💡 On Windows, open this project inside [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) and run `make` from a WSL terminal for the best results. This ensures consistent paths, permissions, and line endings. See [this](https://learn.microsoft.com/en-us/windows/wsl/filesystems#file-storage-and-performance-across-file-systems) article for more info.

You can run these commands from your terminal or integrate them into your flow:

| Target    | Description                                                                      |
|-----------|----------------------------------------------------------------------------------|
| `import`  | Imports a document (DOCX, ODT, RTF) from the artifacts folder                    |
| `publish` | Builds a specific format using [publish.sh](publish.sh)                          |
| `all`     | Builds PDF, EPUB and DOCX formats                                                |
| `clean`   | Prunes images and deletes generated PDFs/EPUBs from [artifacts](/artifacts/)     |
| `help`    | Displays a list of available `Make` targets and usage examples                   |

Example:

```shell
make publish
make publish format=epub
make all
make clean
make help
```

### Project structure

```text
.                       # Project root
├── .docker/            # Docker config
│   └── docker-compose.yaml
├── .keystone/          # Keystone metadata
│   └── sync.json       # Sync metadata
├── .licenses/          # License documents (Keystone, Pandoc)
├── appendix/           # Appendices (e.g., appendix-a.md)
│   └── appendix-a.md
├── artifacts/          # Output folder for built PDFs and EPUBs
├── assets/             # Images and cover art
├── chapters/           # Main content chapters (e.g., introduction.md, chapter-1.md)
│   ├── introduction.md
│   ├── chapter-1.md
│   └── chapter-2.md
├── drafts/             # Work-in-progress material
│   └── chapter-3.md
├── research/           # Notes, references, citations
│   └── about-research.md
├── .dockerignore       # Docker ignore file
├── .editorconfig       # Editor defaults
├── .env                # Project configuration
├── .gitattributes      # Git attributes
├── .gitignore          # Git ignore file
├── LICENSE.md          # License for this project
├── Makefile            # Build commands
├── NOTICE.md           # Project notices and third-party tool acknowledgments
├── pandoc.yaml         # Pandoc metadata (title, author, etc.)
├── README.md           # This file
└── publish.txt         # List of content files to include in order
```

## A Note of Gratitude

Keystone stands on the shoulders of giants.

This project would not be possible without the incredible tools and communities that power its every build:

- [Pandoc](https://pandoc.org/) — the universal document converter
- [LaTeX](https://www.latex-project.org/) — for professional-quality typesetting
- [Docker](https://www.docker.com/) — containerized reproducibility made simple
- [GNU Make](https://www.gnu.org/software/make/) — declarative builds that just work
- [Lua](https://www.lua.org/) — a lightweight, expressive scripting language used to extend Pandoc
- [Markdown](https://www.markdownguide.org/) — the plain-text format that changed writing forever

Each one of these projects represents **years of collective wisdom**, **generosity**, and **craft** — made available freely, **for all**.

To their maintainers and contributors: **thank you**. Keystone is a bridge, but you laid the foundation.

## License

This sample Keystone project is released under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

You are free to:

- Share and adapt this template for personal and non-commercial use
- Modify it to suit your book projects

However:

- Commercial use (including hosted services or SaaS platforms) is not permitted without express written permission
- Derivative works must be shared under the same license terms

See [.licenses/Keystone.md](.licenses/Keystone.md) for full details.

> ⚖️ Keystone builds upon Pandoc, which is licensed under the GNU General Public License (GPL).  
> For details, see [.licenses/Pandoc.md](.licenses/Pandoc.md).

## Attribution

Project Keystone is developed and maintained by [Knight Owl LLC](https://github.com/knight-owl-dev).
If you use this template or build upon it, a link back to this repository is appreciated.
Please also retain license and attribution notices in derivative works to help others trace the origin of the system.
