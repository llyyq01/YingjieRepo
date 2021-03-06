﻿# Set-Location

## SYNOPSIS
Sets the current working location to a specified location.

## DESCRIPTION
The Set-Location cmdlet sets the working location to a specified location.
That location could be a directory, a sub-directory, a registry location, or any provider path.

You can also use the StackName parameter of the Set-Location cmdlet to make a named location stack the current location stack.
For more information about location stacks, see the Notes.

## PARAMETERS

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




### InformationVariable [System.String]




### LiteralPath [String]

```powershell
[Parameter(
  Mandatory = $true,
  ParameterSetName = 'Set 2')]
```

Specifies a path to the location.
The value of the LiteralPath parameter is used exactly as it is typed.
No characters are interpreted as wildcards.
If the path includes escape characters, enclose it in single quotation marks.
Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.


### PassThru [switch]

Returns a System.Management.Automation.PathInfo object that represents the location.
By default, this cmdlet does not generate any output.


### Path [String]

```powershell
[Parameter(
  Position = 1,
  ValueFromPipeline = $true,
  ValueFromPipelineByPropertyName = $true,
  ParameterSetName = 'Set 1')]
```

This parameter is used to specify the path to a new working location.


### StackName [String]

```powershell
[Parameter(
  ValueFromPipelineByPropertyName = $true,
  ParameterSetName = 'Set 3')]
```

Makes the specified location stack the current location stack.
Enter a location stack name.
To indicate the unnamed default location stack, type "$null" or an empty string ("").

The Location cmdlets act on the current stack unless you use the StackName parameter to specify a different stack.



## INPUTS
### System.String

You can pipe a string that contains a path (but not a literal path) to Set-Location.

## OUTPUTS
### None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack

When you use the PassThru parameter, Set-Location generates a System.Management.Automation.PathInfo object that represents the location.
Otherwise, this cmdlet does not generate any output.

## NOTES
The Set-Location cmdlet is designed to work with the data exposed by any provider.
To list the providers available in your session, type "Get-PSProvider".
For more information, see about_Providers.

A "stack" is a last-in, first-out list in which only the most recently added item is accessible.
You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.
Windows PowerShell lets you store provider locations in location stacks.
Windows PowerShell creates an unnamed default location stack and you can create multiple named location stacks.
If you do not specify a stack name, Windows PowerShell uses the current location stack.
By default, the unnamed default location is the current location stack, but you can use the Set-Location cmdlet to change the current location stack.

To manage location stacks, use the Windows PowerShell Location cmdlets, as follows.

-- To add a location to a location stack, use the Push-Location cmdlet.

-- To get a location from a location stack, use the Pop-Location cmdlet.

-- To display the locations in the current location stack, use the Stack parameter of the Get-Location cmdlet.
To display the locations in a named location stack, use the StackName parameter of the Get-Location cmdlet.

-- To create a new location stack, use the StackName parameter of the Push-Location cmdlet.
If you specify a stack that does not exist, Push-Location creates the stack.

-- To make a location stack the current location stack, use the StackName parameter of the Set-Location cmdlet.

The unnamed default location stack is fully accessible only when it is the current location stack.
If you make a named location stack the current location stack, you cannot no longer use Push-Location or Pop-Location cmdlets add or get items from the default stack or use Get-Location command to display the locations in the unnamed stack.
To make the unnamed stack the current stack, use the StackName parameter of the Set-Location cmdlet with a value of $null or an empty string ("").


## EXAMPLES
### -------------------------- EXAMPLE 1 --------------------------

```powershell
PS C:\>set-location HKLM:
PS HKLM:\>

```
This command sets the current location to the root of the HKLM: drive.






### -------------------------- EXAMPLE 2 --------------------------

```powershell
PS C:\>set-location env: -passthru

Path
----
Env:\
PS Env:\>

```
This command sets the current location to the root of the Env: drive.
It uses the Passthru parameter to direct Windows PowerShell to return a PathInfo (System.Management.Automation.PathInfo) object that represents the Env: location.






### -------------------------- EXAMPLE 3 --------------------------

```powershell
PS C:\>set-location C:

```
This command sets the current location C: drive in the file system provider.






### -------------------------- EXAMPLE 4 --------------------------

```powershell
PS C:\>set-location -stackName WSManPaths

```
This command makes the WSManPaths location stack the current location stack.

The location cmdlets use the current location stack unless a different location stack is specified in the command.
For information about location stacks, see the Notes.







## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/p/?linkid=293912)

[Get-Location]()

[Pop-Location]()

[Push-Location]()

[about_Providers]()

