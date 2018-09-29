## Terminal Emulator Magisk Module Template

This template is for Making a script with visual elements which can be executed in a Terminal app in Android, **as a Magisk Module**.  
This provides you with useful functions that might help you easily accomplish stuff for the functions that you're making in you script.

### Magisk Modules that uses this template
* [Terminal Debloater](https://github.com/Magisk-Modules-Repo/terminal_debloater)
* [Terminal App Systemizer](https://github.com/Magisk-Modules-Repo/terminal_systemizer)
* Others

### Stuff included
* Root checking (if the script is running as root)
* Debugging functions (to help you fix errors and bugs in your script)
* Determine if the device has *A/B partitioning scheme*
* Sets Busybox applets (Magisk, osm0sis') for you to not anymore call `busybox` to use them
* Imports Magisk's `util_functions.sh` so that you can use the stuff in it
* Gets the Device Info (Brand, Model, etc) for you to use if needed
* Provides basic ANSI color codes for you to use
* Useful functions and variables

### How to include in a Magisk Module
1. Place `script` (rename to anything you want) in /system/bin or xbin or anywhere you want
2. Add `mod-util.sh` in **common** folder of the Magisk module
3. Add this in **config.sh**'s `set_permissions` function
>cp -af $INSTALLER/common/mod-util.sh $MODPATH/mod-util.sh
set_perm $MODPATH/mod-util.sh 0 0 0777
4. Add your Module's id in ID of the script

### Functions in mod-util.sh

Function | How to use | Example | Output
--- | --- | --- | ---
`title_div` | `title_div <message>` | `title_div Example` | Outputs a bar with a message:  **Example ==========**
`set_file_prop` | `set_file_prop <property> <value> <file.prop>` | `set_file_prop ro.example true /cache/example.prop` | **none**
`ProgressBar` | `ProgressBar <progress> <total threshold>` | `ProgressBar 4 10` | Outputs a progress bar that's animated:  **Progress: [====      ]**
`Spinner` | `Spinner <message>` | `Spinner Example` | Outputs spinner loading animation  **Example: [/]** (this is spinning btw)
`e_spinner` | `cmd && e_pinner <message>` | `cmd && e_spinner Example` | Outputs spinner loading animation until the process of `cmd` is finished  **Example: [/]** (this is spinning btw)
`test_connection` | `test_connection` | `test_connection` | Tells you if internet's ok or not
`upload_logs` | `upload_logs` | `upload_logs` | Generates termbin.com link of the logs uploaded
`mod_head` | `mod_head` | `mod_head` | Outputs heading you can use in your script based on your module's `name` `id` `version` `versionCode` `author`, and also the Busybox used


Contact me in [Telegram](https://t.me/veez21) if needed