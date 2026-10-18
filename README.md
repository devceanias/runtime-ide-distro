# Runtime ⸻ IDE Distribution

Public distribution repository for the **Oceanias Runtime** IDE plugins.

This repository is a static, GitHub Pages–hosted plugin feed. It contains no
source code. It exists so that installed IDE plugins can check for and download
updates through the IDE's native plugin manager.

## What Oceanias Runtime IDE is

Oceanias Runtime IDE is a native IDE frontend for the private **Oceanias
Runtime** repository. It makes Git/DVC asset management usable by developers who
do not work with DVC or the Runtime CLI directly.

The plugin is a **frontend only**. It delegates all Runtime policy, credential
handling, encryption, DVC sequencing, Git safety, and installation side effects
to the Runtime CLI (`./runtime ide ...`) that lives in the checkout you open. The
plugin does **not** replace the CLI, and it does **not** replace the CLI's setup
or authentication. You still install and authenticate the Runtime CLI exactly as
the Runtime repository documents.

## Why this repository is public

The plugin source lives in the private `devceanias/runtime` repository. IDE
plugin managers cannot authenticate against a private repository, so release
artifacts (the plugin ZIP and the update feed) are published here, publicly.
This repository holds **only** released binaries and their update metadata — no
source, no secrets, no private configuration.

## Supported IDEs

| Ecosystem | Status | Feed |
| --- | --- | --- |
| JetBrains (IntelliJ IDEA, and IntelliJ Platform IDEs) | Available | `https://devceanias.github.io/runtime-ide-distro/jetbrains/updatePlugins.xml` |
| Visual Studio Code | Not yet available | — |

The JetBrains plugin targets IntelliJ Platform build **251 (2025.1) and newer**
and is verified against the current 2025.1.x baseline. It is intended for
JetBrains IDEs that provide the platform and language modules (IntelliJ IDEA in
particular).

## Install in IntelliJ IDEA

1. Open **Settings/Preferences → Plugins**.
2. Open the gear menu (⚙) → **Manage Plugin Repositories…**.
3. Add this repository URL:

   ```text
   https://devceanias.github.io/runtime-ide-distro/jetbrains/updatePlugins.xml
   ```

4. Apply. Open the **Marketplace** tab, search for **Runtime**, and install it.
   You can also install a specific build from **Installed → Install Plugin from
   Disk…** using the ZIP from the `jetbrains/` directory of this repository.
5. Restart the IDE when prompted.

Open a checkout of the Runtime repository (or a subdirectory of it). The
**Runtime** tool window activates when the repository's `runtime` command and
`.dvc/config` are present.

## Updates

IntelliJ checks the repository URL above for new versions the same way it checks
the JetBrains Marketplace. When a newer version is published here, the plugin
appears with an **Update** button under **Settings/Preferences → Plugins →
Installed**. No separate update mechanism is bundled in the plugin; updates use
IntelliJ's native plugin update support.

## Repository layout

```text
.
├── README.md
├── .nojekyll
└── jetbrains/
    ├── updatePlugins.xml          # JetBrains custom plugin repository feed
    └── oceanias-runtime-ide-*.zip # one ZIP per released version
```

Additional IDE ecosystems (for example `vscode/`) will be added as sibling
directories without changing the JetBrains layout.

Released version ZIPs are **immutable**: a published version is never deleted or
overwritten with different contents. The feed is updated only after the
corresponding ZIP has been published.

## Releases

Releases are produced automatically from the private Runtime repository by its
GitHub Actions release workflow. Do not edit the files under `jetbrains/` by
hand; the workflow owns them.

## Maintainers

This repository is served by GitHub Pages from the `main` branch root
(**Settings → Pages → Deploy from a branch → `main` / `/ (root)`**). The
`.nojekyll` file is required so the feed and ZIPs are served byte-for-byte.
Publishing and recovery procedures live with the source in the private Runtime
repository.
