''Building the Microsoft  Windows 7 WDK 

_NTTREE

Use the _NTTREE macro to specify the root of the tree where binary files, managed by BinPlace, are put.

The _NTTREE macro works with the TARGET_DESTINATION macro. The value of the TARGET_DESTINATION macro is the path, relative to _NTTREE, where the files are put.
Syntax

_NTTREE = RootDirectory

Parameters

    RootDirectory
    This parameter specifies the root directory of your binaries tree.

Comments

The _NTTREE macro specifies the root of the tree for binary files managed by BinPlace. This macro works together with the TARGET_DESTINATION macro to specify the complete tree for your binary files that are managed by BinPlace. When both macros are declared within your Sources file, the binary tree is defined as:

$(_NTTREE)\$(TARGET_DESTINATION)

You can customize the current _NTTREE path by setting it from your WDK build environment window:

set _NTTREE = BinariesDirectory

The _NTTREE macro is applied only when BinPlace is enabled in a Windows Driver Kit (WDK) build environment. To enable BinPlace, you must specify the separate_object_root parameter of Setenv.bat. For more information about this parameter, see Using the SetEnv.bat Command-Line.

For example, to specify the separate_object_root parameter for the Windows 7 x86 free build environment, follow these steps:

    From the Windows Start menu, click Windows Drivers Kit and then click the Windows 7 WDK entry**.**

    Click the Build Environment menu, and then click Windows 7.

    Right-click x86 Free Build Environment and select Properties.

    Click the Shortcut tab and add the separate_object_root parameter to the end of the Target command for the Build Environment as shown in the following example:

    C:\Windows\System32\cmd.exe /k C:\WinDDK\bin\setenv.bat C:\WinDDK\ fre x86 WIN7 separate_object_root

Example

To configure Binplace to store files under %BASEDIR%.binaries\wdf, follow these steps:

    Type the following command from your WDK build environment window:

set _NTTREE = %BASEDIR%.binaries

Use the following statement within the Sources file:

TARGET_DESTINATION=wdf
