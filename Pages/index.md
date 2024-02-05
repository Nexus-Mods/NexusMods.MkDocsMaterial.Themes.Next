---
hide:
  - toc
---

<div align="center">
	<h1>The Nexus MkDocs Theme</h1>
	<img src="../Images/Nexus-Icon.png" width="150" align="center" />
	<br/> <br/>
    A Theme for MkDocs Material.
    <br/>
    That resembles the <i>Future</i> look of <i>NexusMods</i>.
</div>

## About

This it the NexusMods theme for Material-MkDocs, inspired by the look of [Next](https://next.nexusmods.com), 
the future iteration of the NexusMods site.  

The overall wiki theme should look fairly close to the actual site appearance.

## Setup From Scratch

- Add [this repository](https://github.com/Nexus-Mods/NexusMods.MkDocsMaterial.Themes.Next) as submodule to `docs/Nexus`.
- Save the following configuration as `mkdocs.yml` in your repository root.

```yaml
site_name: Nexus NX MkDocs Theme
site_url: https://github.com/Nexus-Mods/NexusMods.MkDocsMaterial.Themes.Next

repo_name: Nexus-Mods/NexusMods.MkDocsMaterial.Themes.Next
repo_url: https://github.com/Nexus-Mods/NexusMods.MkDocsMaterial.Themes.Next

extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/Nexus-Mods
    - icon: fontawesome/brands/twitter
      link: https://twitter.com/NexusSites

extra_css:
  - Nexus/Stylesheets/extra.css

markdown_extensions:
  - admonition
  - tables
  - pymdownx.details
  - pymdownx.highlight
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
  - pymdownx.tasklist
  - def_list
  - meta
  - md_in_html
  - attr_list
  - footnotes
  - pymdownx.tabbed:
      alternate_style: true
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg

theme:
  name: material
  palette:
    scheme: nexus-slate
  features:
    - navigation.instant

plugins:
  - search

nav:
  - Home: index.md
```

- Add a GitHub Actions workload in `.github/workflows/DeployMkDocs.yml`.

```yaml
name: MkDocs Build and Deploy

on:
  workflow_dispatch:
  push:
    branches: [ main ]
    paths:
      - "mkdocs.yml"
      - "docs/**"
  pull_request:
    branches: [ main ]
    paths:
      - "mkdocs.yml"
      - "docs/**"

jobs:
  build-and-deploy:
    permissions:
      contents: read
      pages: write
      id-token: write
    uses: Nexus-Mods/NexusMods.App.Meta/.github/workflows/mkdocs-build-and-deploy.yaml@main
```

- Push to GitHub, this should produce a GitHub Pages site. 

Your page should then be live.

!!! tip

    Refer to [Contributing](contributing.md#website-live-preview) for instructions on how to locally edit and modify the wiki.

## Extra

!!! info

    Most documentation pages will also include additional plugins; some which are used in the pages here.  
    Here is a sample complete mkdocs.yml you can copy to your project for reference.  


## Technical Questions

If you have questions/bug reports/etc. feel free to [Open an Issue](https://github.com/Nexus-Mods/NexusMods.MkDocsMaterial.Themes.Next/issues/new).

Happy Documenting 🧡