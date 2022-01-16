# qb-lsd
https://github.com/Predator7158

Join My Server
https://discord.gg/nbMazBXaVa

#More Scripts Coming Soon#

**IMPORTANT**

**In Order To get Acid bottle you need to bring Empty bottles and you need to add them manually to a Store**

Step 1
Make sure you add the images that i gave to the inventory and open the shared.lua and add the text given to
qb-core/shared.lua

['lsd'] 				 	 = {['name'] = 'lsd', 			   			['label'] = 'LSD', 					['weight'] = 1000, 		['type'] = 'item', 		['image'] = 'lsd.png', 	    			['unique'] = false, 	['useable'] = false, 	['shouldClose'] = true,	  ['combinable'] = nil,   ['description'] = 'Goo Crazy'},

['empty_bottle'] 				 = {['name'] = 'empty_bottle', 			  	  	['label'] = 'Empty Bottle', 				['weight'] = 900, 		['type'] = 'item', 		['image'] = 'empty_bottle.png', 	   	['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	  ['combinable'] = nil,   ['description'] = 'All we can say is It is empty'},

['acid_bottle'] 				 = {['name'] = 'acid_bottle', 			  	  	['label'] = 'Acid Bottle', 				['weight'] = 1000, 		['type'] = 'item', 		['image'] = 'acid_bottle.png', 	   		['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	  ['combinable'] = nil,   ['description'] = 'Be Careful It might Explode!!'

Step 2
Make sure to add these in qb-core/client/functions.lua
(And this after Drawtext3d) 

```lua
QBCore.Functions.Draw2DText = function(x, y, text, scale)
    SetTextFont(4)
    SetTextProportional(7)
    SetTextScale(scale, scale)
    SetTextColour(255, 255, 255, 255)
    SetTextDropShadow(0, 0, 0, 0,255)
    SetTextDropShadow()
    SetTextEdge(4, 0, 0, 0, 255)
    SetTextOutline()
    SetTextCentre(true)
    SetTextEntry("STRING")
    AddTextComponentString(text)
    DrawText(x, y)
end
```

(This at the Bottom)

```lua
QBCore.Functions.SpawnObject = function(model, coords, cb)
    local model = (type(model) == 'number' and model or GetHashKey(model))

    Citizen.CreateThread(function()
        RequestModel(model)
        local obj = CreateObject(model, coords.x, coords.y, coords.z, true, false, true)
        SetModelAsNoLongerNeeded(model)

        if cb then
            cb(obj)
        end
    end)
end
```
```lua
QBCore.Functions.SpawnLocalObject = function(model, coords, cb)
    local model = (type(model) == 'number' and model or GetHashKey(model))

    Citizen.CreateThread(function()
        RequestModel(model)
        local obj = CreateObject(model, coords.x, coords.y, coords.z, false, false, true)
        SetModelAsNoLongerNeeded(model)

        if cb then
            cb(obj)
        end
    end)
end
```
```lua
QBCore.Functions.DeleteObject = function(object)
    SetEntityAsMissionEntity(object, false, true)
    DeleteObject(object)
end
```
