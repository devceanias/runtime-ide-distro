# Runtime ⸻ IDE Plugins

Public distribution repository for IDE plugins for **Oceanias Runtime**.

Plugin source lives in the private `devceanias/runtime` repository. This
repository hosts compiled release artifacts and update feeds so the plugins can
be installed and updated through supported IDEs.

## Supported IDEs

| IDE | Status |
| --- | --- |
| JetBrains IDEs | Available |
| Visual Studio Code | Planned |

## Install (JetBrains IDEs)

1. Open **Settings → Plugins**.
2. Open the gear menu and choose **Manage Plugin Repositories**.
3. Add this repository URL:

   `https://runtime.oceanias.net/jetbrains/updatePlugins.xml`

4. Search for **Runtime** in the **Marketplace** tab and install it.
5. Restart the IDE if prompted.

The Runtime plugin is a frontend for the Oceanias Runtime CLI. It needs a
Runtime checkout with the CLI set up, and it does not replace the CLI's setup or
authentication.

## Updates

JetBrains IDEs update Runtime through the repository URL above, using the IDE's
built-in plugin manager.

## Releases

Releases are built and published from the private Runtime repository by GitHub
Actions. Artifacts are grouped by IDE ecosystem:

```text
jetbrains/
├── updatePlugins.xml
└── oceanias-runtime-ide-<version>.zip
```

Visual Studio Code will have its own `vscode/` directory and a separate
distribution mechanism; it will not use the JetBrains repository feed.
