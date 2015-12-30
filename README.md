# PS WinRM Plugin for Rundeck

Powershell file-copier plugin for Rundeck

### Build and install
Just create a zip archive of ps-rundeck-winrm-plugin folder and place in `%RUNDECK_ROOT%/libext`.

### Use
1. Set `service.FileCopier.default.provider=ps-winrm-fc` in your `%RUNDECK_ROOT%/projects/%PROJECT_NAME%/etc/project.properties`
2. Configure your project -> Simple Configuration -> set password storage key

### Requirements
* WinRM should be configured correctly both on local and remote node (see https://github.com/xebialabs/overthere/#winrm-winrm_internal-and-winrm_native)
* Rundeck should run on Windows host with Powershell 3+
* Powershell execution policy both on server and remote node should be `Unrestricted`, or you can sign scripts, if needed higher secure level, or run powershell.exe with `-ExecutionPolicy Bypass`
* Remote user (on remote node) should be in 'Remote Management Users' group

### Limitations
* Plugin replaces `bat` with `ps1` extension to support powershell scripts
* SSL is used by default, remote node certificate should be installed on local machine
* Authentication type is default

### Tips
* If you're running rundeck on windows host, you can use winrs as node executor. Select script-exec in project configuration and set command to `winrs /r:https://${node.hostname} /u:${node.username} /p:${node.password} ${exec.command}`. All preferences you can set via `winrm set winrm/config/*`
* To use inline powershell scripts, check advanced options, set command: `Powershell -NoProfile -File`

Pull requests are welcome!
