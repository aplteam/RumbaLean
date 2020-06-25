# RumbaLean

## Overview

This is a fork of [Carlisle's original Rumba](https://github.com/the-carlisle-group/Rumba "Link to Carlisle's Rumba project on GitHub") project.

Rumba (and therefore RumbaLean) are an almost full implementation of the HTTP 1.1 protocol with the exception of SSE (Server Side Events).

## Requirements

RumbaLean needs, like Rumba, at least Dyalog APL 17.0 Unicode. It does not run in the Classic version.

## Why this fork

These are the goals of this fork:

* Allow the path to the Conga DLLs being specified as a parameter
* Avoid all dependencies excepts the need of the Conga DLLs required by Rumba
<<<<<<< HEAD
* Allow trapping crashes on the exit functions (`OnStart`, `OnRequest`, ...) with an alternative mechanism: by default the [APLTree](https://github.com/aplteam/apltree/wiki "Link to the APLTree home page on GitHub") class [`HandleError`](https://github.com/aplteam/HandleError "Link to the project page on GitHub") is used for this
* Use the Conga class rather than the namespace `DRC`
=======
>>>>>>> origin/master
* Remove namespaces that are not needed: `Doc`, `DemoApp` and `WebAdmin`
* Remove functions from the `Admin` namespace that are not needed for the core functionality: `BuildPackage`, `BuildRelease`, `CopyFolder`, `CopyProject`, `LoadHelp`, `StartHelp` and `GetDrudgeReport`

Notes:

* Main goal is to keep Rumba's core functionality in line with the original project 
* The test cases are still part of the project
* The help is available in a sub folder - execute `RumbaHelp/ViewHelp.exe`
* In order to build a new version execute the `Make.bat` file in the `Make` folder
* RumbaLean has its own version number

## Syntactical differences

There are two potential differences between the original Rumba project and RumbaLean: the way the Conga DLLs are located. RumbaLean expects these DLLs to be found in the current directory. If that is not the case you have to tell RumbaLean where to look for them:

### Server

Provide the folder that carries the Conga DLLs as the right argument of the function `Core.Start`.

### Client

When you call one the usual functions like `Send` or `SendAndReceive` etc. then they will call a function `Connect` which in turn will attempt to initialize Conga by calling a function `InitConga` under the assumption that the DLLs required are to be found in the current directory.

If that is not the case for you then you must call `InitConga` yourself once with the folder that holds those DLLs as the right argument.

## Build process

Most of the changes are actually performed by the "Make" workspace; only the changes required for finding the Conga DLLs are actually part of the fork. The reason for this is that this makes a comparison between the original Rumba project and RumbaLean much easier.

The drawback of this approach is that the resulting "RumbaLean" workspace looks very different from the resulting project workspace.

## Keeping RumbaLean in sync with Rumba

There is a separate document HowToSyncWithRumba.md available that addresses this issue.
