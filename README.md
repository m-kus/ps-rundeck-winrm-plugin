# PS WinRM Plugin for Rundeck

Powershell file-copier plugin for Rundeck

### Build and install
Just create a zip archive of ps-rundeck-winrm-plugin folder and place in `%RUNDECK_ROOT%/libext`.

### Use
1. Set `service.FileCopier.default.provider=ps-winrm-fc` in your `%RUNDECK_ROOT%/projects/%PROJECT_NAME%/etc/project.properties`
2. Configure your project -> Simple Configuration -> set password storage key

### Requirements
* Rundeck should run on Windows host with Powershell 3+
* Execution policy both on server and remote node should be 'Unrestricted', or you can sign scripts, if needed higher secure level
* Remote user (on remote node) should be in 'Remote Management Users' group

### Limitations
* Plugin replaces `bat` with `ps1` extension to support powershell scripts
* SSL is used by default, remote node certificate should be installed on local machine
* Authentication type is default

Pull requests are welcome!
