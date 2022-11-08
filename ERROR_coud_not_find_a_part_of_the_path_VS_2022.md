When converting XfhUltra over to .NET 6.0 I encountered the error:
"Could not find a part of the path .... (very long file path name)" in 
Visual Studio. I found that the error was due to the long file path.
This is an issue with Windows 10 that has a variable you can set to fix it,
but you have to manually set this variable, as it is not the default.
To fix it, I opened powershell with admin privileges and used the following 
command to enable long file paths:

New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" `
-Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force

See this post for a description of the error:
https://github.com/OmniSharp/omnisharp-roslyn/issues/2261

See this page for instructions on how to set the variable:
https://learn.microsoft.com/en-us/windows/win32/fileio/maximum-file-path-limitation?tabs=powershell
