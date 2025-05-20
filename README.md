# VSCode Context Menu Registry Setup

This repository contains a Windows Registry file (`vscode_context_menu_top.reg`) to add "Open with VS Code" and "Open Folder as VS Code Project" options to the right-click context menu in Windows Explorer. These options allow you to quickly open files or folders in Visual Studio Code (VS Code) directly from the context menu, with the entries prioritized near the top of the menu.

## Purpose
The `vscode_context_menu_top.reg` file adds the following context menu options:
- **For files**: "Open with VS Code" when right-clicking any file.
- **For folders**: "Open Folder as VS Code Project" when right-clicking a folder.
- **For folder background**: "Open Folder as VS Code Project" when right-clicking inside a folder (on the background).

These entries are prefixed with `!` to appear near the top of the context menu for quick access.

## Prerequisites
- Visual Studio Code installed on your system.
- Administrator privileges may be required to modify the Windows Registry.

## Installation
1. **Verify VS Code Path**:
   - Ensure the path to `Code.exe` in the `.reg` file matches your VS Code installation. The default path in the file is:
     ```
     C:\Program Files\Microsoft VS Code\Code.exe
     ```
   - If VS Code is installed elsewhere (e.g., user-specific installation), update the path in `vscode_context_menu_top.reg`. For example:
     ```
     C:\Users\YourUsername\AppData\Local\Programs\Microsoft VS Code\Code.exe
     ```
   - To find the path, locate `Code.exe` in your VS Code installation folder.

2. **Apply the Registry File**:
   - Double-click `vscode_context_menu_top.reg`.
   - Confirm the prompt to add the entries to the Windows Registry.

3. **Verify**:
   - Right-click a file or folder in Windows Explorer.
   - Look for `!OpenWithVSCode` (for files) or `!VSCodeProject` (for folders) near the top of the context menu.

## File Structure
- `vscode_context_menu_top.reg`: The registry file that adds the context menu entries.

## Troubleshooting
- **Option not appearing**: Ensure the path to `Code.exe` in the `.reg` file is correct. Check if you have permission to modify the registry.
- **Duplicate entries**: If old VS Code context menu entries exist, remove them using `regedit`:
  - Open `regedit` (type `regedit` in the Start menu).
  - Navigate to `HKEY_CLASSES_ROOT\*\shell` and delete any old `Open with VS Code` key.
  - Navigate to `HKEY_CLASSES_ROOT\Directory\shell` and delete any old `vscode` key.
  - Navigate to `HKEY_CLASSES_ROOT\Directory\Background\shell` and delete any old `vscode` key.
- **Backup**: Always export your registry (File > Export in `regedit`) before making changes.

## Notes
- The `!` prefix in the menu names ensures the options appear near the top of the context menu due to alphabetical sorting.
- To make the options appear only in the extended context menu (Shift + right-click), add `"Extended"=""` to each shell key in the `.reg` file.

## Warning
- Modifying the Windows Registry can cause system issues if done incorrectly. Proceed with caution and ensure you have a backup of your registry.
- This script is designed for Windows only. For macOS, consider using Automator or third-party tools like [OpenInCode](https://github.com/sozercan/OpenInCode).

## License
This project is provided as-is, with no warranty. Use at your own risk.
