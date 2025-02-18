#!/bin/bash
cat << 'EOF' > cursor_reset_readme.md
# Cursor Reset Script

This is a PowerShell script designed to reset the device identifiers of the Cursor IDE. The script supports Cursor version 0.45.x (tested on version 0.45.8).

---

## ⚠️ Disclaimer

This project is intended solely for educational and research purposes, specifically to study the device identification mechanism of Cursor IDE. It is strongly recommended to purchase a legitimate license for Cursor to support the developers.

Using this script may violate Cursor's Terms of Service. The author is not responsible for any issues resulting from the use of this script, including but not limited to:
- Invalidation of software licenses
- Account suspension
- Other unknown risks

If you value Cursor's contributions, please support the official version and pay for the developers' work.

---

## Usage

⚠️ To avoid immediate invalidation of a new account, please strictly follow the steps below:

### **For Windows**
1. Sign out of your current account in Cursor IDE.
2. Completely close Cursor IDE.
3. Open Command Prompt or PowerShell with Administrator privileges.
4. Copy and paste the following command into the terminal:
   ```bash
       powershell -ExecutionPolicy Bypass -Command "[Net.ServicePointManager]:: SecurityProtocol = [Net.SecurityProtocolType]::Tls12; iwr -Uri 'https://raw.githubusercontent.com/hamflx/cursor-reset/main/reset.ps1' -UseBasicParsing | iex"
   ```
5. After the reset is complete, open Cursor IDE and log in with a new account (do not use the previous account).
   
If the script gets stuck at "Waiting for Cursor process to exit...", force-terminate all Cursor processes by running the following command:
```bash
taskkill /f /im cursor.exe
```


For macOS
Sign out of your current account in Cursor IDE.
Completely close Cursor IDE.
Open Terminal and execute the following command:
```bash
curl -fsSL https://raw.githubusercontent.com/hamflx/cursor-reset/main/reset.sh | bash
```
Open Cursor IDE and log in with a new account (do not use the previous account).
To restore to the original state, use this command:

```bash
curl -fsSL https://raw.githubusercontent.com/hamflx/cursor-reset/main/reset.sh | bash -s -- --restore
```
If the script gets stuck at "Waiting for Cursor process to exit...", force-terminate Cursor processes by running the following command:

```bash
pkill -9 Cursor
```
⚠️ Important Notes

For Windows
The script modifies the system registry key HKLM\SOFTWARE\Microsoft\Cryptography\MachineGuid.
Other software may use this registry key as a device identifier.
If you have purchased a legitimate Cursor license or any other software that depends on this registry key for licensing, modifying it may invalidate those licenses.
The original MachineGuid will automatically be backed up in the %USERPROFILE%\MachineGuid_Backups directory. If you need to restore the original value, you can locate the backup file in this directory and restore it via the registry editor.

For macOS
The script modifies the following files:
~/Library/Application Support/Cursor/User/globalStorage/storage.json
/Applications/Cursor.app/Contents/Resources/app/out/main.js
/Applications/Cursor.app/Contents/Resources/app/out/vs/code/node/cliProcessMain.js
All modified files will automatically be backed up (with a .bak file extension).
To restore the original files, you can use the --restore parameter when running the script.
Execution Results
After successful execution, the script will display the following information:

The location of backup files
The newly generated MachineGuid
The new values for:
telemetry.machineId
telemetry.macMachineId
telemetry.devDeviceId
telemetry.sqmId
System Requirements

For Windows
Windows operating system
PowerShell
Administrator privileges
Cursor IDE version 0.45.x (tested on version 0.45.8)
For macOS
macOS 10.13 or higher
Cursor IDE version 0.45.x EOF
echo "Markdown content saved to 'cursor_reset_readme.md'."

```css
This script will create a Markdown file named `cursor_reset_readme.md` containing the above content. Save the script to a file (e.g., `generate_readme.sh`), and run it to generate the Markdown file.
```






