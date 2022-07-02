# Inventory

### <mark style="color:blue;">Limits</mark>

Here you can configure the inventors slot limit for every usergroup.

```
InventoryModule.Limits = {
    ["superadmin"] = 100,
    ["admin"] = 50,
    ["user"] = 13
}
```

### <mark style="color:blue;">Blacklist</mark>

Here you can blacklist Entities/Weapons from getting packed into users inventory.

```
InventoryModule.Blacklist = {
    -- Weapons
    ["weapon_fists"] = false,
    ["weapon_physgun"] = false,
    ["msrp_inventorypicker"] = false,
    ["gmod_tool"] = false,
    ["manhack_welder"] = false,
    ["gmod_camera"] = false,
    -- Entities
    ["msrp_bodygroups"] = false,
    ["sent_ball"] = false,
    ["msrp_money"] = false, -- Money
}
```

<mark style="color:blue;"></mark>
