# Outpost 2 Mission Software Development Kit

A conglomeration of C++ libraries easing the development of new Outpost 2 missions. Designed for static compilation with new mission DLLs. Optimized for use with Microsoft Visual Studio.

The following submodules are included:

 - Outpost2DLL
 - OP2Helper
 - Hacker's Function Library (HFL)
 - odasl: Outpost 2 themed dialog skinning
 
## Change log:
Follows semantic versioning: https://semver.org/

### Version 2.0.0
This release is a rollup of minor changes to the 3 subprojects. Contains breaking changes by removing deprecated functionality. If deprecated features are not in use, should be a drop-in upgrade. The macro `ExportLevelDetailsEx` in Outpost2DLL is now considered deprecated and should be replaced in new projects.

##### Outpost2DLL
 - Add comments to TethysGame::AddMessage explaining location agnostic messages work
   - Recommend using OP2Helper AddGameMessage family instead of TethysGame::AddMessage
 - Improve comments and argument names when using function SetEMPMissile
 - Add AiModDescEx struct
   - Required when using an AI controlled player in multiplayer scenarios
 - Replace macro ExportLevelDetailsEx with ExportLevelDetailsFull
   - Deprecate macro ExportLevelDetailsEx
   - ExportLevelDetailsFull is a more appropriate name for macro based on what it exports.
 - Add ExportLevelDetailsFullEx macro
   - Incorporates new AiModDescEx struct and can be used to add AI players in multiplayer scenarios without manually exporting the AiModDescEx struct.
 - Remove previously deprecated portions of RequiredExports.h
   - If previously using the macro SCRIPT_API, the macro Export is a drop-in replacement
 - Mark exported data in RequiredExports.h as const
 - Add dummy file Outpost2DLL.cpp to allow compiling Outpost2DLL standalone (running compiler checks)
 
##### OP2Helper
 - New AddGameMessage function family
   - Simplifies calls to add messages compared to TethysGame::AddMessage
   - Hides const conversion warnings created by TethysGame::AddMessage when using stricter compiler settings
 - Add global operator overloads for LOCATION== and LOCATION!=
 - Simplify Visual Studio project settings
 
##### HFL
 - Fix incorrectly formatted include guard in TriggerEx.h
 - Simplify Visual Studio project configuration settings

 
### Version 1.0.0
 - Initial Release
