# internet-basic README

This is a Visual Studio Code language extension for Internet Basic language, used by the Comet runtime.  You must have Visual Studio Code installed in order to use this extension.

To use this extension:
* First, download and install [Visual Studio Code](https://code.visualstudio.com/)
* Download the internet-basic [VSIX extension file](https://github.com/JustinSigSys/internet-basic/releases/download/v0.0.1/internet-basic-0.0.1.vsix)

Once you have Viusual Studio Code installed:
* Go to the extension browser (Click "Extensions" on the left-side menu or press ```CTRL-SHIFT-X```
* Click on the elipses "..." in the top right corner of the extensions window ("Views and More Actions...")
* Click "Install from VSIX..."
* Select the downloaded VSIX file
* Restart Visual Studio Code

## Features

 This is a bare bones attempt to get syntax highlighting to work properly for .ibs and .inc files.

## Requirements

**Visual Studio Code is required in order to use this extension**

Comet by Signature Systems is required to compile and run Internet Basic programs.

Console.exe is required to compile Internet Basic programs.

## Known Issues

This extension does not provide any tasks to compile/register/setup comet files.  Those must be created yourself.  See the sample tasks.json file at the bottom of this README.

## Release Notes

Initial release.  This release should provide syntax highlighting for all comet ibs and inc files.  Specifics of syntax highlighting is provided by your theme.

-----------------------------------------------------------------------

## Sample tasks.json

Below is a sample tasks.json file that should allow you to register and compile internet basic files, as well as set up your console.exe to point to the proper comet executables.

In order to open the tasks.json file:
* Press ```CTRL-SHIFT-P``` to bring up the Command Palette
* Click "Tasks: Open User Tasks"
* tasks.json should now be open - add the following code
* Save tasks.json

You can now run the tasks by pressing ```CTRL-SHIFT-P``` then selecting "Run task" and selecting the appropriate task.

You can also specify your default build task to be the "IB Compile" task, which will allow you to press ```CTRL-SHIFT-B``` to automaticaly compile the current file.

Remember to replace the path to console.exe with your specific path - usually in the comet installation folder.

```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "IB Compile",
            "type": "shell",
            "command": "\\path\\to\\console.exe",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "presentation": {
                "echo": true,
                "reveal": "always",
                "focus": false,
                "panel": "dedicated",
                "showReuseMessage": true,
                "clear": false
            },
            "args": [
                "-c",
                "${file}"
            ],
            "problemMatcher": []
        },
        {
            "label": "IB Register File",
            "type": "shell",
            "command": "\\path\\to\\console.exe",
            "presentation": {
                "echo": true,
                "reveal": "always",
                "focus": false,
                "panel": "dedicated",
                "showReuseMessage": true,
                "clear": false
            },
            "args": [
                "-q",
                "${file}"
            ]
        },
        {
            "label": "IB Comet Setup",
            "type": "shell",
            "command": "\\path\\to\\console.exe",
            "presentation": {
                "echo": true,
                "reveal": "always",
                "focus": false,
                "panel": "dedicated",
                "showReuseMessage": true,
                "clear": false
            },
            "args": [
                "-s"
            ],
            "problemMatcher": []
        }
    ]
}
```
