﻿# Restart-Computer

## SYNOPSIS
Restarts ("reboots") the operating system on local and remote computers.

## DESCRIPTION
The Restart-Computer cmdlet restarts the operating system on the local and remote computers.

You can use the parameters of Restart-Computer to run the restart operations as a background job, to specify the authentication levels and alternate credentials, to limit the operations that run concurrently, and to force an immediate restart.

Beginning in Windows PowerShell 3.0, you can wait for the restart to complete before running the next command, specify a waiting timeout and query interval, and wait for particular services to be available on the restarted computer.
This feature makes it practical to use Restart-Computer in scripts and functions.
You can also use the WSMan protocol to restart the computer, in case DCOM calls are blocked, such as by an enterprise firewall.

This cmdlet requires Windows PowerShell remoting only when you use the AsJob parameter in a command.

## PARAMETERS

### AsJob [switch]

```powershell
[Parameter(ParameterSetName = 'Set 2')]
```

Runs the command as a background job.

Note: To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of Windows, you must open Windows PowerShell with the "Run as administrator" option.
For more information, see about_Remote_Requirements (http://go.microsoft.com/fwlink/?LinkID=135187).

When you use the AsJob parameter, the command immediately returns an object that represents the background job.
You can continue to work in the session while the job completes.
The job is created on the local computer and the results from remote computers are automatically returned to the local computer.
To manage the job, use the Job cmdlets.
To get the job results, use the Receive-Job cmdlet.

For more information about Windows PowerShell background jobs, see about_Jobs (http://go.microsoft.com/fwlink/?LinkID=113251) and about_Remote_Jobs (http://go.microsoft.com/fwlink/?LinkID=135184).


### ComputerName [String[]]

```powershell
[Parameter(
  Position = 1,
  ValueFromPipeline = $true,
  ValueFromPipelineByPropertyName = $true)]
```

Specifies one or more remote computers.
The default is the local computer.

Type the NETBIOS name, an IP address, or a fully qualified domain name of a remote computer.
To specify the local computer, type the computer name, a dot (.), or "localhost".

This parameter does not rely on Windows PowerShell remoting.
You can use the ComputerName parameter even if your computer is not configured to run remote commands.


### Credential [PSCredential]

```powershell
[Parameter(Position = 2)]
```

Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one from the Get-Credential cmdlet.


### Delay [Int16]

```powershell
[Parameter(ParameterSetName = 'Set 1')]
```

Determines how often Windows PowerShell queries the service that is specified by the For parameter to determine whether it is available after the computer is restarted.
Specify a delay between queries, in seconds.
The default value is 5 (seconds).

This parameter is valid only with the Wait and For parameters.

This parameter is introduced in Windows PowerShell 3.0.


### For [WaitForServiceTypes]

```powershell
[Parameter(ParameterSetName = 'Set 1')]
[ValidateSet(
  'PowerShell',
  'WinRM',
  'Wmi')]
```

Waits until the specified service or feature is available after the computer is restarted.
Specify one of the valid values.
This parameter is valid only with the Wait parameter.

Valid values are:

-- Default: Waits for Windows PowerShell to restart.

-- PowerShell: Can run commands in a Windows PowerShell remote session on the computer.

-- WMI: Receives a reply to a Win32_ComputerSystem query for the computer.

-- WinRM: Can establish a remote session to the computer by using WS-Management.

This parameter is introduced in Windows PowerShell 3.0.


### Force [switch]

Forces an immediate restart of the computers.


### Impersonation [ImpersonationLevel]

```powershell
[ValidateSet(
  'Default',
  'Anonymous',
  'Identify',
  'Impersonate',
  'Delegate')]
```

Specifies the impersonation level to use when calling WMI. (Restart-Computer uses WMI.) The default value is "Impersonate".

Valid values are:


-- Default:      Default impersonation.

-- Anonymous:    Hides the identity of the caller.

-- Identify:     Allows objects to query the credentials of the caller.

-- Impersonate:  Allows objects to use the credentials of the caller.


### InformationAction [System.Management.Automation.ActionPreference]

```powershell
[ValidateSet(
  'SilentlyContinue',
  'Stop',
  'Continue',
  'Inquire',
  'Ignore',
  'Suspend')]
```


Note: To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of Windows, you must open Windows PowerShell with the "Run as administrator" option.
For more information, see about_Remote_Requirements (http://go.microsoft.com/fwlink/?LinkID=135187).

When you use the AsJob parameter, the command immediately returns an object that represents the background job.
You can continue to work in the session while the job completes.
The job is created on the local computer and the results from remote computers are automatically returned to the local computer.
To manage the job, use the Job cmdlets.
To get the job results, use the Receive-Job cmdlet.

For more information about Windows PowerShell background jobs, see about_Jobs (http://go.microsoft.com/fwlink/?LinkID=113251) and about_Remote_Jobs (http://go.microsoft.com/fwlink/?LinkID=135184).


### InformationVariable [System.String]


Note: To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of Windows, you must open Windows PowerShell with the "Run as administrator" option.
For more information, see about_Remote_Requirements (http://go.microsoft.com/fwlink/?LinkID=135187).

When you use the AsJob parameter, the command immediately returns an object that represents the background job.
You can continue to work in the session while the job completes.
The job is created on the local computer and the results from remote computers are automatically returned to the local computer.
To manage the job, use the Job cmdlets.
To get the job results, use the Receive-Job cmdlet.

For more information about Windows PowerShell background jobs, see about_Jobs (http://go.microsoft.com/fwlink/?LinkID=113251) and about_Remote_Jobs (http://go.microsoft.com/fwlink/?LinkID=135184).


### ThrottleLimit [Int32]

```powershell
[Parameter(ParameterSetName = 'Set 2')]
```

Specifies the maximum number of concurrent connections that can be established to run this command.
If you omit this parameter or enter a value of 0, the default value, 32, is used.

The throttle limit applies only to the current command, not to the session or to the computer.


### Timeout [Int32]

```powershell
[Parameter(ParameterSetName = 'Set 1')]
```

Specifies the duration of the wait, in seconds.
When the timeout elapses, Restart-Computer returns the command prompt, even if the computers are not restarted.
The default value, -1, represents an indefinite timeout.

The Timeout parameter is valid only with the Wait parameter.

This parameter is introduced in Windows PowerShell 3.0.


### Wait [switch]

```powershell
[Parameter(ParameterSetName = 'Set 1')]
```

Suppresses the Windows PowerShell prompt and blocks the pipeline until all of the computers have restarted.
You can use this parameter in a script to restart computers and then continue processing when the restart is complete.

By default, the Wait parameter waits indefinitely for the computers to restart, but you can use the Timeout parameter to adjust the timing and the For and Delay parameters to wait for particular services to be available on the restarted computers.

The Wait parameter is not valid when you are restarting the local computer.
If the value of the ComputerName parameter contains the names of remote computers and the local computer, Restart-Computer generates a non-terminating error for the Wait parameter on the local computer, but it waits for the remote computers to restart.

This parameter is introduced in Windows PowerShell 3.0.


### DcomAuthentication [AuthenticationLevel]

```powershell
[ValidateSet(
  'Default',
  'None',
  'Connect',
  'Call',
  'Packet',
  'PacketIntegrity',
  'PacketPrivacy',
  'Unchanged')]
```

Specifies the authentication level that is used for the WMI connection. (Restart-Computer uses WMI.) The default value is Packet.

Valid values are:

-- Call:            Call-level COM authentication

-- Connect:         Connect-level COM authentication

-- Default:         Windows Authentication

-- None:            No COM authentication

-- Packet:          Packet-level COM authentication.

-- PacketIntegrity: Packet Integrity-level COM authentication

-- PacketPrivacy:   Packet Privacy-level COM authentication.

-- Unchanged:       The authentication level is the same as the previous command.

For more information about the values of this parameter, see "AuthenticationLevel Enumeration" on [MSDN]() at http://go.microsoft.com/fwlink/?LinkID=235229.

This parameter is introduced in Windows PowerShell 3.0.


### Protocol [String]

```powershell
[Parameter(ParameterSetName = 'Set 1')]
[ValidateSet(
  'DCOM',
  'WSMan')]
```

Specifies which protocol to use to restart the computers.
Valid values are WSMan and DCOM.
The default value is DCOM.

This parameter is introduced in Windows PowerShell 3.0.


### WsmanAuthentication [String]

```powershell
[Parameter(ParameterSetName = 'Set 1')]
[ValidateSet(
  'Default',
  'Basic',
  'Negotiate',
  'CredSSP',
  'Digest',
  'Kerberos')]
```

Specifies the mechanism that is used to authenticate the user's credentials when using the WSMan protocol.

Valid values are Basic, CredSSP, Default, Digest, Kerberos, and Negotiate.
The default value is Default.
For more information about the values of this parameter, see "AuthenticationMechanism Enumeration" on [MSDN]() at http://go.microsoft.com/fwlink/?LinkID=235230.

Caution: Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.
This mechanism increases the security risk of the remote operation.
If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.

This parameter is introduced in Windows PowerShell 3.0.


### Confirm [switch]

Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.


### WhatIf [switch]

Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.



## INPUTS
### System.String

You can pipe computer names to Restart-Computer.

In Windows PowerShell 2.0, the ComputerName parameter takes input from the pipeline only by property name.
In Windows PowerShell 3.0, the ComputerName parameter takes input from the pipeline by value.

## OUTPUTS
### None or System.Management.Automation.RemotingJob

When you use the AsJob parameter, the cmdlet returns a job object.
Otherwise, it does not generate any output.

## NOTES
This cmdlet uses the Win32Shutdown  method of the WMI WIN32_OperatingSystem class.

In Windows PowerShell 2.0, the AsJob parameter does not work reliably when you are restarting/stopping remote computers.
In Windows PowerShell 3.0, the implementation is changed to resolve this problem.

## EXAMPLES
### -------------------------- EXAMPLE 1 --------------------------

```powershell
PS C:\>Restart-Computer

```
This command restarts the local computer.


### -------------------------- EXAMPLE 2 --------------------------

```powershell
PS C:\>Restart-Computer -ComputerName Server01, Server02, localhost

```
This command restarts two remote computers, Server01 and Server02, and the local computer, identified as "localhost".


### -------------------------- EXAMPLE 3 --------------------------

```powershell
The first command uses the AsJob parameter to run the command as a background job. The command saves the resulting job object in the $j variable.
PS C:\>$j = Restart-Computer -ComputerName Server01, Server02 -AsJob

The second command uses a pipeline operator to send the job object in $j to the Receive-Job cmdlet, which gets the job results. The command saves the results in the $Results variable.
PS C:\>$Results = $j | Receive-Job

The third command displays the result saved in the $Results variable.Because the AsJob parameter creates the job on the local computer and automatically returns the results to the local computer, you can run the Receive-Job command as a local command.
PS C:\>$Results

```
These commands run a Restart-Computer command as a background job on two remote computers, and then get the results.


### -------------------------- EXAMPLE 4 --------------------------

```powershell
PS C:\>Restart-Computer -ComputerName Server01 -Impersonation Anonymous -Authentication PacketIntegrity

```
This command restarts the Server01 remote computer.
The command uses customized impersonation and authentication settings.


### -------------------------- EXAMPLE 5 --------------------------

```powershell
The first command uses the Get-Content cmdlet to get a list of computers in the domain from the Domain01.txt file. It saves the list in the $s variable.
PS C:\>$s = Get-Content Domain01.txt


The second command gets the credentials of a domain administrator and saves them in the $c variable.
PS C:\>$c = Get-Credential Domain01\Admin01

The third command restarts the computers. It uses the ComputerName parameter to submit the list of computers in the $s variable, the Force parameter to force an immediate restart, and the Credential parameter to submit the credentials saved in the $c variable. It also uses the ThrottleLimit parameter to limit the command to 10 concurrent connections.
PS C:\>Restart-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c

```
These commands force an immediate restart of all of the computers in Domain01.


### -------------------------- EXAMPLE 6 --------------------------

```powershell
PS C:\>Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2

```
This command restarts the Server01 remote computer and then waits up to 5 minutes (300 seconds) for Windows PowerShell to be available on the restarted computer before continuing.

The command uses the Wait, For, and Timeout parameters to specify the conditions of the wait.
It uses the Delay parameter to reduce the interval between queries to the remote computer that determine whether it is restarted.


### -------------------------- EXAMPLE 7 --------------------------

```powershell
PS C:\>Restart-Computer -ComputerName Server01 -Protocol WSMan -WSManAuthentication Kerberos

```
This command restarts the Server01 remote computer by using the WSMan protocol, instead of DCOM, which is the default.
It also uses Kerberos authentication to determine whether the current user has permission to restart the remote computer.

These settings are designed for enterprises in which DCOM-based restarts fail because DCOM is blocked, such as by a firewall.



## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/p/?linkid=293905)

[Add-Computer]()

[Checkpoint-Computer]()

[Rename-Computer]()

[Remove-Computer]()

[Restore-Computer]()

[Stop-Computer]()

[Test-Connection]()

