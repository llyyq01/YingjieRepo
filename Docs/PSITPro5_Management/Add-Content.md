﻿# Add-Content

## SYNOPSIS
Adds content to the specified items, such as adding words to a file.

## DESCRIPTION
The Add-Content cmdlet appends content to a specified item or file.
You can specify the content by typing the content in the command or by specifying an object that contains the content.

## PARAMETERS

### Credential [PSCredential]

```powershell
[Parameter(ValueFromPipelineByPropertyName = $true)]
```

Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers installed with Windows PowerShell.


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

This parameter is not supported by any providers installed with Windows PowerShell.


### Exclude [String[]]

Omits the specified items.
The value of this parameter qualifies the Path parameter.
Enter a path element or pattern, such as "*.txt".
Wildcards are permitted.


### Filter [String]

Specifies a filter in the provider's format or language.
The value of this parameter qualifies the Path parameter.
The syntax of the filter, including the use of wildcards, depends on the provider.
Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having Windows PowerShell filter the objects after they are retrieved.


### Force [switch]

Overrides the read-only attribute, allowing you to add content to a read-only file.


### Include [String[]]

Adds only the specified items.
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

This parameter is not supported by any providers installed with Windows PowerShell.


### InformationVariable [System.String]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers installed with Windows PowerShell.


### LiteralPath [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  ParameterSetName = 'Set 2')]
```

Specifies the path to the items that receive the additional content.
Unlike Path, the value of LiteralPath is used exactly as it is typed.
No characters are interpreted as wildcards.
If the path includes escape characters, enclose it in single quotation marks.
Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.


### PassThru [switch]

Returns an object representing the added content.
By default, this cmdlet does not generate any output.


### Path [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  Position = 1,
  ValueFromPipelineByPropertyName = $true,
  ParameterSetName = 'Set 1')]
```

Specifies the path to the items that receive the additional content.
Wildcards are permitted.
If you specify multiple paths, use commas to separate the paths.


### Stream [System.String]


Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers installed with Windows PowerShell.


### Value [Object[]]

```powershell
[Parameter(
  Mandatory = $true,
  Position = 2,
  ValueFromPipeline = $true,
  ValueFromPipelineByPropertyName = $true)]
```

Specifies the content to be added.
Type a quoted string, such as "This data is for internal use only", or specify an object that contains content, such as the DateTime object that Get-Date generates.

You cannot specify the contents of a file by typing its path, because the path is just a string, but you can use a Get-Content command to get the content and pass it to the Value parameter.


### Confirm [switch]

Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.


### WhatIf [switch]

Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.


### UseTransaction [switch]

Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see



## INPUTS
### System.Object

You can pipe the objects to be added (the Value) to Add-Content.

## OUTPUTS
### None or System.String

When you use the Passthru parameter, Add-Content generates a System.String object representing the content.
Otherwise, this cmdlet does not generate any output.

## NOTES
When you pipe an object to Add-Content, the object is converted to a string before it is added to the item.
The object type determines the string format, but the format might be different than the default display of the object.
To control the string format, use the formatting parameters of the sending cmdlet.

You can also refer to Add-Content by its built-in alias, "ac".
For more information, see about_Aliases.

The Add-Content cmdlet is designed to work with the data exposed by any provider.
To list the providers available in your session, type "Get-PsProvider".
For more information, see about_Providers.


## EXAMPLES
### -------------------------- EXAMPLE 1 --------------------------

```powershell
PS C:\>add-content -path *.txt -exclude help* -value "END"

```
This command adds "END" to all text files in the current directory, except for those with file names that begin with "help".






### -------------------------- EXAMPLE 2 --------------------------

```powershell
PS C:\>add-content -Path file1.log, file2.log -Value (get-date) -passthru

```
This command adds the date to the end of the File1.log and File2.log files and then displays the date at the command line.
The command uses the Get-Date cmdlet to get the date, and it uses the Value parameter to pass the date to Add-Content.
The PassThru parameter passes an object representing the added content through the pipeline.
Because there is no other cmdlet to receive the passed object, it is displayed at the command line.






### -------------------------- EXAMPLE 3 --------------------------

```powershell
PS C:\>add-content -path monthly.txt -value (get-content c:\rec1\weekly.txt)

```
This command adds the contents of the Weekly.txt file to the end of the Monthly.txt file.
It uses the Get-Content cmdlet to get the contents of the Weekly.txt file, and it uses the Value parameter to pass the content of weekly.txt to Add-Content.
The parentheses ensure that the Get-Content command is complete before the Add-Content command begins.

You can also copy the content of Weekly.txt to a variable, such as $w, and then use the Value parameter to pass the variable to Add-Content.
In that case, the command would be "add-content -path monthly.txt -value $w".






### -------------------------- EXAMPLE 4 --------------------------

```powershell
PS C:\>add-content -value (get-content test.log) -path C:\tests\test134\logs\test134.log

```
This command creates a new directory and file and copies the content of an existing file to the newly created file.

This command uses the Add-Content cmdlet to add the content.
The value of the Value parameter is a Get-Content command that gets content from an existing file, Test.log.

The value of the path parameter is a path that does not exist when the command runs.
In this example, only the C:\Tests directories exist.
The command creates the remaining directories and the Test134.log file.

The Force parameter is not required for this command.
Add-Content creates directories to complete a path even without the Force parameter.




## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/p/?linkid=289796)

[Clear-Content]()

[Get-Content]()

[Get-Item]()

[Set-Content]()

[about_Providers]()

