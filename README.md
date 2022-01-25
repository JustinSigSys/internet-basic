# internet-basic README

This is a language extension for the Internet Basic language, used by the Comet runtime.

## Features

 This is a bare bones attempt to get syntax highlighting to work properly for .ibs and .inc files.

## Requirements

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
* Hold CTRL-SHIFT-P
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