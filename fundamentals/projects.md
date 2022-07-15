---
description: Here you can find all important information about creating a custom module
---

# Creating a module

### <mark style="color:blue;">Autoload</mark>

{% hint style="warning" %}
If an folder does not contain an sh\_index.lua file its possible that the the server returns an error.
{% endhint %}

To improve the simplicitiy of the gamemode we decided to implement an autoloading system for all folders in the module folder.&#x20;

That means that the gamemodes finds all folders containing an **sh\_index.lua** file.&#x20;

### <mark style="color:blue;">Folder structure</mark>

Because we want to make it as esay as possible for you to create custom module we set up a template repository.

You can easily use this template to begin codeing your custom module.

{% embed url="https://github.com/Maax-Studios/ModuleTemplate" %}

### <mark style="color:blue;">sh\_index.lua</mark>

Only the sh\_index.lua file will be loaded automaticly when the gamemodes starts. So all other files like a config file needs to be added to the index file.&#x20;

{% code title="Example #1" %}
```lua
if SERVER then 

    AddCSLuaFile("cl_BodyGroupUI.lua")

    include("sv_BodyGroupNetworking.lua")

else
    
    include("cl_BodyGroupUI.lua")

end

-- Copied from: bodygroups/sh_index.lua
```
{% endcode %}

As you might can see the sh\_config.lua is a shared lua file. So we can run code on client an server-side.

We also can put other stuff in this file like a globle table or some hooks.

{% code title="Example #2" %}
```lua
FactionModule = FactionModule or {}

hook.Add("msrp_MySQLReady", "FactionModuleInit", function() 

    SQL:Query("CREATE TABLE IF NOT EXISTS `FactionModule` ( `FactionId` INT NOT NULL AUTO_INCREMENT , `FactionName` TEXT NOT NULL , `FactionDescription` TEXT NOT NULL , `FactionRankTable` INT NOT NULL , `FactionColor` TEXT NOT NULL DEFAULT '255,255,255' , `FactionIsDefault` BOOLEAN NOT NULL DEFAULT FALSE , `FactionParentId` INT NOT NULL DEFAULT '0' , `FactionShortCut` TEXT NOT NULL , PRIMARY KEY (`FactionId`));")
    SQL:Query("CREATE TABLE IF NOT EXISTS `FactionRanks` ( `RankId` INT NOT NULL AUTO_INCREMENT , `RankName` TEXT NOT NULL , `RankShort` TEXT NOT NULL , `RankModels` JSON NOT NULL , `RankWeapons` JSON NOT NULL , `RankSortId` VARCHAR(11) NOT NULL , `RankFaction` VARCHAR(11) NOT NULL , `RankDefault` BOOLEAN NOT NULL DEFAULT FALSE, PRIMARY KEY (`RankId`))")

end)

if SERVER then 

    AddCSLuaFile("cl_RankManager.lua")
    AddCSLuaFile("cl_FactionManager.lua")
    AddCSLuaFile("cl_FactionCache.lua")
    AddCSLuaFile("cl_FactionHooks.lua")

    include("sv_RankNetworking.lua")
    include("sv_RankFunctions.lua")
    include("sv_FactionsHooks.lua")
    include("sv_FactionsCache.lua")
    include("sv_FactionNetworking.lua")
    include("sv_FactionFuntions.lua")

else 

    include("cl_RankManager.lua")
    include("cl_FactionManager.lua")
    include("cl_FactionCache.lua")
    include("cl_FactionHooks.lua")

end

-- Copied from: factions/sh_index.lua
```
{% endcode %}

Here we added a hook and a table.&#x20;

* The SQLReady hook is called when the gamemode connected to the server.&#x20;
