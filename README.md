# Config and extensions for VSCode

## Settings
The `settings.json` file is a global settings for the user's profile VSCode instance.
User's profile are overriden by Workspace settings.
Workspace settings are overriden by Folder settings.

The file located at: 
- Windows: `%appdata%\Code\User\settings.json`
- Linux: `$HOME/.config/Code/User/settings.json` (This may avry based on the package manager used to install VSCode)

## Extensions
To install the extension, run the following command (make sure `code` is in the PATH):
- PowerShell
```PowerShell
Get-Content extensions.txt | ForEach-Object { code --install-extension $_ }
```

- cmd
```shell
for /F "tokens=*" %i in (extensions.txt) do code --install-extension %i
```

- bash
```shell
xargs -L 1 code --install-extension < extensions.txt
```