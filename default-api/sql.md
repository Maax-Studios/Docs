# SQL

## <mark style="color:blue;">SQL:Query()</mark>

{% code title="Function" %}
```lua
SQL:Query( string, callback, wait)
```
{% endcode %}

{% tabs %}
{% tab title="Arguments" %}
*   <mark style="color:blue;">**string**</mark>

    Query-String
*   <mark style="color:blue;">**boolean**</mark>

    Should wait or not
{% endtab %}

{% tab title="Returns" %}
*   <mark style="color:blue;">**table**</mark>

    Returns the selected data
{% endtab %}
{% endtabs %}

## <mark style="color:blue;">Hooks</mark>

#### msrp\_MySQLReady

```lua
hook.Add(„msrp_MySQLReady“, function()
        print(„MySQL Ready“)
 end)
```

#### Example/Usage

```lua
hook.Add("msrp_MySQLReady", "CharacterModuleInit", function() 

    SQL:Query("CREATE TABLE IF NOT EXISTS `FactionModule` ( `FactionId` INT NOT NULL AUTO_INCREMENT , `FactionName` TEXT NOT NULL , `FactionDescription` TEXT NOT NULL , `FactionRankTable` INT NOT NULL , `FactionColor` TEXT NOT NULL DEFAULT '255,255,255' , `FactionIsDefault` BOOLEAN NOT NULL DEFAULT FALSE , `FactionParentId` INT NOT NULL DEFAULT '0' , `FactionShortCut` TEXT NOT NULL , PRIMARY KEY (`FactionId`));")
    SQL:Query("CREATE TABLE IF NOT EXISTS `FactionRanks` ( `RankId` INT NOT NULL AUTO_INCREMENT , `RankName` TEXT NOT NULL , `RankShort` TEXT NOT NULL , `RankModels` JSON NOT NULL , `RankWeapons` JSON NOT NULL , `RankSortId` VARCHAR(11) NOT NULL , `RankFaction` VARCHAR(11) NOT NULL , `RankDefault` BOOLEAN NOT NULL DEFAULT FALSE, PRIMARY KEY (`RankId`))")

end)

-- Copied from: factions/sh_index.lua
```
