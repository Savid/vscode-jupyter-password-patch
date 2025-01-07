# VSCode Jupyter Password Patch

This repository contains a patch for the [VSCode Jupyter extension](https://github.com/microsoft/vscode-jupyter) that adds support for storing Jupyter server passwords in VSCode settings.

## What it does

The patch adds a new configuration option `jupyter.passwords` that allows you to store passwords for remote Jupyter servers in your VSCode settings. This is useful if you frequently connect to password-protected Jupyter servers and don't want to enter the password each time.

## How it works

1. The repository watches the upstream VSCode Jupyter repository for changes
2. When a new commit is detected on the main branch:
   - The code is cloned
   - The patch is applied
   - A new VSIX package is built
   - A release is created tagged with the upstream commit hash

## Installation

1. Download the latest VSIX from the [Releases page](../../releases)
2. Install it in VSCode:
   - Open VSCode
   - Press Ctrl+Shift+P (Cmd+Shift+P on macOS)
   - Type "Install from VSIX" and select it
   - Choose the downloaded VSIX file

## Configuration

Add your Jupyter server passwords to your VSCode settings:

```json
{
  "jupyter.passwords": {
    "http://example.com:8888": "your_password_here"
  }
}
```

The key should be the full URL of your Jupyter server.

## Security Note

Passwords are stored in your VSCode settings file. While settings marked as "machine" scope are stored separately from your user settings, you should still be cautious about storing sensitive information.
