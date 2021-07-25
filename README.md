# RumbaLean

## Overview

This is a fork of [Carlisle's original Rumba](https://github.com/the-carlisle-group/Rumba "Link to Carlisle's Rumba project on GitHub") project.

Rumba (and therefore RumbaLean) are an almost full implementation of the HTTP 1.1 protocol: only SSE (Server Side Events) are missing.

## Requirements

RumbaLean needs at least Dyalog APL 18.0 Unicode.

## Why this fork

These are the goals of this fork:

* Allow the path to the Conga DLLs being specified as a parameter
* Allow the specification of "rootname" (Conga)
* Added function `Shutdown` that needs to be called in order to restart Conga
* RumbaLean requires upfront initialisation befor Rumba can be used.
* All calls to `InitConga` are removed from the Rumba functions.
* Avoid all dependencies excepts the need of the Conga DLLs required by Rumba
* Allow trapping crashes on the exit functions (`OnStart`, `OnRequest`, ...) with an alternative mechanism: by default the [APLTree](https://github.com/aplteam/apltree/wiki "Link to the APLTree home page on GitHub") class [`HandleError`](https://github.com/aplteam/HandleError "Link to the project page on GitHub") is used for this
* Use the Conga class rather than the namespace `DRC`
* Remove namespaces that are not required: `Doc`, `DemoApp` and `WebAdmin` for the core functionality
* Remove functions from the `Admin` namespace that are not needed for the core functionality: `BuildPackage`, `BuildRelease`, `CopyFolder`, `CopyProject`, `LoadHelp`, `StartHelp` and `GetDrudgeReport`

Notes:

* Main goal is to keep Rumba's core functionality in line with the original project 
* The test cases are still part of the project
* The help is available in a sub folder - execute `RumbaHelp/ViewHelp.exe`
* In order to build a new version load `Make\Make.dws`
* RumbaLean has its own version number

## Syntactical differences

There are two main differences between the original Rumba project and RumbaLean: 

* The way the Conga DLLs are located. RumbaLean expects these DLLs to be found in the current directory. If that is not the case you have to tell RumbaLean where to look for them as the first optional right argument to `InitConga`.

* You may specify an optional "rootname" (Conga). This is important if you wish to use Rumba in the samke workspace for two different applications. Each application needs "see" only its own Conga objects, and for that you must specify "rootname" for one of them so that they use different ones. Default is "DEFAULT".

### Server

Provide the folder that carries the Conga DLLs as the right argument of the function `Core.Start`.

### Client

When you call one the usual functions like `Send` or `SendAndReceive` etc. then they will call a function `Connect` which in turn will attempt to initialize Conga by calling a function `InitConga` under the assumption that the DLLs required are to be found in the current directory.

If that is not the case you have two options:
* Call `InitConga` yourself once with the folder holding those DLLs as the right argument in order to make sure that all is fine before Rumba is doing anywork.
* Set the global `Rumba.Core.∆CONGA_DLL_PATH` to the path where the Conga DLLs live. This variable is by default empty.

## Build process

Most of the changes are actually performed by the "Make" workspace. Any changes made to the code are marked up with comments like `⍝ Kai`. The reason for this is that this makes a comparison between the original Rumba project and RumbaLean easier.

The drawback of this approach is that the resulting "RumbaLean" workspace looks very different from the project workspace.

## Keeping RumbaLean in sync with Rumba

There is a separate document HowToSyncWithRumba.md available that addresses this issue.
