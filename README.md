# psconf

APIs
https://learn.microsoft.com/en-us/windows/win32/api/winsvc/nf-winsvc-openscmanagerw
https://learn.microsoft.com/en-us/windows/win32/api/winsvc/nf-winsvc-createservicew

PowerShell module
https://github.com/PowerShell/PowerShell/blob/master/src/Microsoft.PowerShell.Commands.Management/commands/management/Service.cs


To create a parameter ComputerName
Find a line 2037 and paste code below
        /// <summary>
        /// ComputerName where the service must be created.
        /// </summary>
        /// <value></value>
        [Parameter]
        [ValidateNotNullOrEmpty]
        public string ComputerName
        {
            get { return computerName; }

            set { computerName = value; }
        }

        internal string computerName = null;

Find line 2150. Change value null to ComputerName and build your module (link below)
hScManager = NativeMethods.OpenSCManagerW(
    null,

Build your module
https://github.com/PowerShell/PowerShell/blob/master/docs/building/windows-core.md