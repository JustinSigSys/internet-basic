# Internet Basic Extension for Visual Studio Code

This extension provides basic syntax highlighting in the Visual Studio Code editor.  Using the sample tasks.json file below you can also use Visual Studio Code to compile Internet Basic programs.  [Visual Studio Code](https://code.visualstudio.com/) is a free code editor provided by Microsoft.

To use this extension:
* First, download and install [Visual Studio Code](https://code.visualstudio.com/)
* Download the internet-basic [VSIX extension file](https://github.com/JustinSigSys/internet-basic/releases/download/v0.0.1/internet-basic-0.0.1.vsix)

Once you have Viusual Studio Code installed:
* Go to the extension browser (Click "Extensions" on the left-side menu or press ```CTRL-SHIFT-X```)
* Click on the elipses "..." in the top right corner of the extensions window ("Views and More Actions...")
* Click "Install from VSIX..."
* Select the downloaded VSIX file
* Restart Visual Studio Code

## Features

This is a bare bones attempt to get syntax highlighting to work properly for .ibs and .inc files.

## Requirements

**Visual Studio Code is required in order to use this extension**

Comet by Signature Systems is required to compile and run Internet Basic programs.

Console.exe is required to compile Internet Basic programs, and is provided by the Comet workstation installation.

## Known Issues

This extension does not provide any tasks to compile/register/setup comet files.  Those must be created yourself.  See the sample tasks.json file at the bottom of this README.

## Release Notes

Initial release.  This release should provide syntax highlighting for all comet ibs and inc files.  Specifics of syntax highlighting is provided by your theme.

-----------------------------------------------------------------------

## Sample tasks.json

Below is a sample tasks.json file that should allow you to register and compile internet basic files, as well as set up your console.exe to point to the proper comet executables.

In order to get your tasks file set up, we will need to make use of the [Command Palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette), which allows us to access VS Code's functionality through typing and selecting the commands we are interested in.  To use the Command Palette, start by pressing ```CTRL-SHIFT-P```, which will bring up a box with a cursor inside, and a drop-down list of options.  As you type, VS Code will display any commands that match.  For instance, after typing "build" in the Command Palette, the drop-down list will contain options for "Tasks: Run Build Task" as well as "Tasks: Configure Default Build Task" (which we will use below).

Note: When you first open the Command Palette with ```CTRL-SHIFT-P```, the text field already contains a right bracket ">" which specifies that VS Code is searching for matching commands.  If you start typing any of the commands below and file names start showing up instead, or you do not see the proper commands in the drop-down list, make sure you haven't accidentally removed the ">" from the beginning of the text field.

So let's get started by setting up your tasks.json file.

In order to open the tasks.json file:
* Press ```CTRL-SHIFT-P``` to bring up the Command Palette
* Type/select "Tasks: Open User Tasks"
* tasks.json should now be open - add the code at the bottom of this section
* Save tasks.json

Verify the tasks were set up:
* Press ```CTRL-SHIFT-P``` to bring up the Command Palette
* Type/select "Tasks: Run Task"
* You should see and be able to select the following tasks:
    - IB Compile - compiles the current open Internet Basic file
    - IB Register File - registers the current file in Comet
    - IB Comet Setup - specify the path and arguments used to launch Comet (if it is not already open when running tasks)

Next, if you want to set up the shortcut ```CTRL-SHIFT-B``` to compile the current open file:
* Press ```CTRL-SHIFT-P``` to bring up the Command Palette
* Type/select "Tasks: Configure Default Build Task"
* Select "IB Compile" from the subsequent drop-down list

That's it!  You should be all set to compile IB programs using Visual Studio Code.

```
{
    // Remember to replace the path to console.exe with your specific path.
    // (usually in the comet installation folder)
    // For example, "c:\\comet\\console.exe"
    // Remember to use double backslashes "\\" inside of strings
    //
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
