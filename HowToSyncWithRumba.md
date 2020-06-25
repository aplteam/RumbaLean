# How to sync with Rumba

RumbaLean's _main_ purpose was to allow specifying the location of the Conga DLLs.

Once the decision was made to fork from the original Rumba project, a couple of other changes were made as well. See the ReadMe.md for details.

However, for the time being the goal is to keep RumbaLean in line with the original project.

The easiest way to do this is to open RumbaLean with acre and save the workspace. Then do the same for the original project:

1. Download from <https://github.com/the-carlisle-group/Rumba>

2. Open the project with acre

3. `)save` the workspace

Now compare the two workspaces with an appropriate tool in order to figure out what was actually changed, and either accept or reject those changes.

Note that most of the changes are actually done by the "Make" workspace, so those will not show as differences at all. 

On the other hand that means that changes or additions to the `WebAdmin` or the `HTML` and other sub namespaces (again, ReadMe.md provides the details) can be savely ignored because they won't be part of the final RumbaLean workspace anyway.