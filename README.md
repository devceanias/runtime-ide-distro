# Runtime ⸻ IDE Plugins

Distribution repository for Oceanias Runtime IDE plugins.

Plugin source code is maintained in the private `devceanias/runtime` repository. This public repository hosts compiled releases and update feeds so plugins can be installed and updated directly through supported IDEs.

## Supported IDEs

| IDE | Status | Installation |
| --- | --- | --- |
| JetBrains IDEs | Available | [Plugin repository](https://devceanias.github.io/runtime-ide-distro/jetbrains/updatePlugins.xml) |
| Visual Studio Code | Planned | — |

## Installation

### JetBrains IDEs

1. Open **Settings → Plugins** in your IDE.
2. Click the gear icon and select **Manage Plugin Repositories**.
3. Add the following URL:

   `https://devceanias.github.io/runtime-ide-distro/jetbrains/updatePlugins.xml`

4. Search for **Runtime** in the **Marketplace** tab and install the plugin.
5. Restart your IDE if prompted.

The plugin requires a checkout of Oceanias Runtime with its CLI configured. It provides a graphical interface for working with Runtime files and operations without needing to run commands manually.

### Updates

Updates are delivered through the IDE's built-in plugin manager. Once installed, Runtime can be updated like any other IDE plugin.

## Releases

Plugin releases are built and published from the private Runtime repository using GitHub Actions.

Release artifacts are organized by IDE ecosystem:

```text
jetbrains/
├── updatePlugins.xml
└── oceanias-runtime-ide-<version>.zip
```

Additional IDE integrations will have their own directories as they become available.