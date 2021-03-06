﻿# Get-Content

## SYNOPSIS
Gets the content of the item at the specified location.

## DESCRIPTION
The Get-Content cmdlet gets the content of the item at the location specified by the path, such as the text in a file.
It reads the content one line at a time and returns a collection of objects , each of which represents a line of content.

Beginning in Windows PowerShell 3.0, Get-Content can also get a specified number of lines from the beginning or end of an item.

## PARAMETERS

### Credential [PSCredential]

```powershell
[Parameter(ValueFromPipelineByPropertyName = $true)]
```

Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### Delimiter [System.String]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### Encoding [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding]

```powershell
[ValidateSet(
  'Unknown',
  'String',
  'Unicode',
  'Byte',
  'BigEndianUnicode',
  'UTF8',
  'UTF7',
  'UTF32',
  'Ascii',
  'Default',
  'Oem',
  'BigEndianUTF32')]
```


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### Exclude [String[]]

Omits the specified items.
The value of this parameter qualifies the Path parameter.
Enter a path element or pattern, such as "*.txt".
Wildcards are permitted.


### Filter [String]

Specifies a filter in the provider's format or language.
The value of this parameter qualifies the Path parameter.
The syntax of the filter, including the use of wildcards, depends on the provider.
Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having Windows PowerShell filter the objects after they are retrieved.


### Force [switch]

Overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.
For example, Force will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.


### Include [String[]]

Gets only the specified items.
The value of this parameter qualifies the Path parameter.
Enter a path element or pattern, such as "*.txt".
Wildcards are permitted.


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


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### InformationVariable [System.String]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### LiteralPath [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  ParameterSetName = 'Set 2')]
```

Specifies the path to an item.
Unlike Path, the value of LiteralPath is used exactly as it is typed.
No characters are interpreted as wildcards.
If the path includes escape characters, enclose it in single quotation marks.
Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.


### Path [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  Position = 1,
  ValueFromPipelineByPropertyName = $true,
  ParameterSetName = 'Set 1')]
```

Specifies the path to an item.
Get-Content gets the content of the item.
Wildcards are permitted.
The parameter name ("Path" or "FilePath") is optional.


### Raw [switch]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### ReadCount [Int64]

```powershell
[Parameter(ValueFromPipelineByPropertyName = $true)]
```

Specifies how many lines of content are sent through the pipeline at a time.
The default value is 1.
A value of 0 (zero) sends all of the content at one time.

This parameter does not change the content displayed, but it does affect the time it takes to display the content.
As the value of ReadCount increases, the time it takes to return the first line increases, but the total time for the operation decreases.
This can make a perceptible difference in very large items.


### Stream [System.String]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### TotalCount [Int64]

```powershell
[Parameter(ValueFromPipelineByPropertyName = $true)]
```

Gets the specified number of lines from the beginning of a file or other item.
The default is -1 (all lines).

You can use the "TotalCount" parameter name or its aliases, "First" or "Head".


### Tail [Int32]

```powershell
[Parameter(ValueFromPipelineByPropertyName = $true)]
```

Gets the specified number of lines from the end of a file or other item.

This parameter is introduced in Windows PowerShell 3.0.

You can use the "Tail" parameter name or its alias, "Last".


### Wait [switch]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers that are installed with Windows PowerShell.


### UseTransaction [switch]

Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see



## INPUTS
### None

You cannot pipe input to Get-Content.

## OUTPUTS
### System.Byte, System.String

Get-Content returns strings or bytes.
The output type depends upon the content that it gets.

## NOTES
The Get-Content cmdlet is designed to work with the data exposed by any provider.
To get the providers in your session, use the Get-PsProvider cmdlet.
For more information, see about_Providers (http://go.microsoft.com/fwlink/?LinkID=113250).


## EXAMPLES
### -------------------------- EXAMPLE 1 --------------------------

```powershell
PS C:\>Get-Content -Path C:\Chapters\Chapter1.txt

```
This command gets the content of the Chapter1.txt file.
It uses the Path parameter to specify the name of the item.
Get-Content actually passes the content down the pipeline, but because there are no other pipeline elements, the content is formatted by default and displayed at the command line.


### -------------------------- EXAMPLE 2 --------------------------

```powershell
PS C:\>Get-Content c:\Logs\Log060912.txt -TotalCount 50 | Set-Content Sample.txt

```
This command gets the first 50 lines of the Log060912.txt file and stores them in the Sample.txt file.
The command uses the Get-Content cmdlet to get the text in the file. (The name of Path parameter, which is optional, is omitted.) The TotalCount parameter limits the content retrieved to the first 50 lines.
The pipeline operator (|) sends the result to the Set-Content cmdlet, which places it in the Sample.txt file.


### -------------------------- EXAMPLE 3 --------------------------

```powershell
PS C:\>(Get-Content Cmdlets.txt -TotalCount 5)[-1]

```
This command gets the fifth line of the Cmdlets.txt text file.
It uses the TotalCount parameter to get the first five lines and then uses array notation to get the last line (indicated by "-1") of the resulting set.


### -------------------------- EXAMPLE 4 --------------------------

```powershell
PS C:\>dir .\*.txt | ForEach {Get-Content $_ -Head 1; Get-Content $_ -Tail 1}

```
This command gets the first and last lines of each text file in the current directory.
The command uses the Tail parameter and the Head alias of the TotalCount parameter



## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/p/?linkid=290491)

[Add-Content]()

[Clear-Content]()

[Set-Content]()

[about_Providers]()

