Instructions: 
A screenshot or Markdown code block showing the command and its output.
What the absolute path to the working directory was right before the command was run.
A sentence or two explaining why you got that output (e.g. what was in the filesystem, what it meant to have no arguments).
Indicate explicitly whether the output is an error or not, and if it's an error, explain why it's an error in one or two sentences. Note: Make sure to use backticks ` around keywords such as commands, file names, paths, etc. to make them show up as code like cd.


# 1. cd: "Changing Directory"
```
  PS C:\Users\Zoe> cd
```
Absolute path: /home/user/Zoe 

Explaination: Using the above command line means the user did not specify the argument. If used without argument, cd would default the user to the home directory.

This output is not an error. 

```
  PS C:\Users\Zoe> cd Desktop
  PS C:\Users\Zoe\Desktop> 
```
Absolute path: /home/Users/Zoe

Explaination: The result of the above command would change the current directory of the terminal. Specifiying the directory with an argument would reflect a chagne as shown by the directory in the line below.

The output is not an error.

```
PS C:\Users\Zoe> cd \Users\Zoe\Downloads\Filename.txt
```
Absolute path: /home/Users/Zoe

Explaination: Filename.txt is a pdf file in my Downloads. The command recognizes that the argument is not a directory and will not be able to make subsequent directory changes. 

The ouput would result in an error as shown below.


# 2. ls: "List" 

```
PS C:\Users\Zoe> ls
```
Absolute path: /home/Users/Zoe

Explaination: The above command would output the available files and direcotries from the current directory. 

The output is not an error. 

```
PS C:\Users\Zoe> ls Downloads
```
Absolute path: /home/Users/Zoe

Explaination: The output reads the list of files from the directory path that was specified in the argument. This would open a list of files that is in Downloads.

The output is not an error. 

```
PS C:\Users\Zoe\Downloads> ls Filename.txt
```
Absolute path: /home/Users/Zoe/Downloads

Explaination: The argument is a file in my Downloads that is being passed through ls. The argument for a list cannot be a file. 

The outoput is an error. 


# 2. cat: "Concatenate"
```
PS C:\Users\Zoe> cat
```
Absolute path: /home/Users/Zoe

Explaination: When given no argument, the terminal requires the user to enter parameter[0] in order to continue with the command. 

The output is technically not an error, but it would require further specifciations in arguments. Otherwise, the cat command will read from standard input. 

```
PS C:\Users\Zoe\Downloads> cat Filename.txt
```
Absolute path: /home/Users/Zoe/Downloads

Explaination: The command would display the content in Filename.txt. 

The output is not an error. 

```
PS C:\Users\Zoe> cat Downloads
cat : Access to the path 'C:\Users\Zoe\Downloads' is denied.
At line:1 char:1
+ cat Downloads
+ ~~~~~~~~~~~~~
    + CategoryInfo          : PermissionDenied: (C:\Users\Zoe\Downloads:String) [Get-Content], UnauthorizedAccessException
    + FullyQualifiedErrorId : GetContentReaderUnauthorizedAccessError,Microsoft.PowerShell.Commands.GetContentCommand
```
Absolute path: /home/Users/Zoe

Explaination: Since cat would print out the content of a file, the argument cannot be a directory and would show that the access is denied.

The output is an error. 







