# Outpost 2 Mission Software Development Kit

A conglomeration of C++ libraries easing the development of new Outpost 2 missions. Designed for static compilation with new mission DLLs. Optimized for use with Microsoft Visual Studio.

The following submodules are included:

 - Outpost2DLL
 - OP2Helper
 - Hacker's Function Library (HFL)
 - odasl: Outpost 2 themed dialog skinning
 
## Change log:
Follows semantic versioning: https://semver.org/

### Version 4.1.0
Version 4.1.0 focuses on focuses on improved library internal implementation and C++ standards compliance. A few minor enhancements are made in OP2Helper including a BuildingBays enum. the constant AllPlayers in Outpost2DLL is now deprecated and should be replaced by PlayerNum::PlayerAll. Targeting a specific version of the Windows SDK was removed from all three major libraries. 

#### Outpost2DLL
 - Bug: Fix documentation of RecordVehReinforceGroup to prevent a hanging bug within Outpost2.exe
 - Add a readme
 - Deprecate AllPlayers constant (Use PlayerNum::PlayerAll instead)
 - Improve C++ standards compliance and readability of source code
 - Clearly forward declare dependence on DirectX IDirectDraw
 - Improve comments on UnitClassifications enum and typedef
 - Improve implementation of internal headers

#### OP2Helper
 - Add a readme
 - Add function CenterViewOn
 - Represent building bays as an enum

#### HFL
 - Improve Readme
 - Improve example level code to prevent save/load bug and use modern features of Outpost2DLL
 - Improve C++ standards compliance and readbility of source code
 - Remove excessive internal casting

### Version 4.0.0
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
 - Ease recording tube and wall lines to building groups
 - Deprecate CreateTubeOrWallLine function
   - Replace with instance functions CreateTubeLine, CreateWallLine, CreateLavaWallLine, and CreateMicrobeWallLine
 - New AddGameMessage function family
   - Simplifies calls to add messages compared to TethysGame::AddMessage
   - Hides const conversion warnings created by TethysGame::AddMessage when using stricter compiler settings
 - Add global operator overloads for LOCATION==, LOCATION!=, LOCATION+=, and LOCATION-=
 - Simplify Visual Studio project settings
 - Remove BaseBuilderV2
 
##### HFL
 - Fix incorrectly formatted include guard in TriggerEx.h
 - Simplify Visual Studio project configuration settings


### Version 3.5.0
Version 3.5.0 is a collection of changes made from 2015 until the SDK was ported to Git. These changes were never officially packaged and released.

##### Outpost2DLL
 - Add Outpost2App headers
 - Remove LibCTiny.lib
 - Add macros to ease mission save region actions (ExportSaveLoadData and ExportSaveLoadDataNone)
   - Allows auto generation of the GetSaveRegions function for a given global variable name
   - Also allows generating a GetSaveRegions function when no data needs to be saved to saved game files
 - Add PlayerColor enum 
 - Add argument names to functions SetAttackType and SetFollowMode
 - Change access to ScStub::stubIndex from private to public
   - While this field would normally be private for object oriented encapsulation, making it public allows for easier hacks that require the contained value
 - Fix typos in code comments
 
##### OP2Helper
 - Add LOCATION global operator overloads for + and -
 - Add Bulldozer.h/.cpp
   - Simplifies bulldozing terrain during mission initialization
 - Update ColonyType to also allow checking which buildings and vehicles belong to which colony type (Eden, Plymouth, or both)
 - Update Lava.h/.cpp
   - Eases setting volcano flow animation on active volcanoes 
   - Eases setting tiles as lava possible
   - This causes function name collisions in some older, existing scenario projects. The functions in lava.h should be drop in replacements for these scenarios.
 - Add CenterViewOnPlayerCC (ZigZagJoe)
   - This function existed since approximately 2009, but was not merged into the master OP2Helper branch
 - Allow specifying player number for function CreateNoCommandCenterFailureCondition
 - Remove reference semantics from functions CreateLastOneStandingVictoryCondition & CreateNoCommandCenterFailureCondition
 - Correct spelling and grammatical mistakes in code comments
 - Refactor functions to use modern C++ coding practices

##### HFL
 - Use safe versions of c-style string functions
 - Add hex values to CommandType enum for easier human reference 
 
### Version 1.0.0 to 3.0.0
 - Maintained in subversion (SVN) repository. Search the forums at https://forum.outpost2.net/ for details.
