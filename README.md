if game.PlaceId == 155615604 then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Prison Life", "Midnight")
 
    -- MAIN
    local Main = Window:NewTab("Main")
    local MainSection = Main:NewSection("Main")
 
    MainSection:NewDropdown("Give Gun", "Gives the localplayer a gun", {"M9", "Remington 870", "AK-47"}, function(v)
        local A_1 = game:GetService("Workspace")["Prison_ITEMS"].giver[v].ITEMPICKUP
        local Event = game:GetService("Workspace").Remote.ItemHandler
        Event:InvokeServer(A_1)
    end)
 
    MainSection:NewDropdown("Gun Mod", "Makes the gun op", {"M9", "Remington 870", "AK-47"}, function(v)
        local module = nil
        if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(v) then
            module = require(game:GetService("Players").LocalPlayer.Backpack[v].GunStates)
        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(v) then
            module = require(game:GetService("Players").LocalPlayer.Character[v].GunStates)
        end
        if module ~= nil then
            module["FireRate"] = 0.00000001
            module["Spread"] = 0
            module["AutoFire"] = true
        end
    end)
    
         MainSection:NewButton("Silent Aim", "Locks onto polices head", function()
    local Players = game.Players
local LocalPlayer = Players.LocalPlayer
local GetPlayers = Players.GetPlayers
local Camera = workspace.CurrentCamera
local WTSP = Camera.WorldToScreenPoint
local FindFirstChild = game.FindFirstChild
local Vector2_new = Vector2.new
local Mouse = LocalPlayer.GetMouse(LocalPlayer)
function ClosestChar()
    local Max, Close = math.huge
    for I,V in pairs(GetPlayers(Players)) do
        if V ~= LocalPlayer and V.Team ~= LocalPlayer.Team and V.Character then
            local Head = FindFirstChild(V.Character, "Head")
            if Head then
                local Pos, OnScreen = WTSP(Camera, Head.Position)
                if OnScreen then
                    local Dist = (Vector2_new(Pos.X, Pos.Y) - Vector2_new(Mouse.X, Mouse.Y)).Magnitude
                    if Dist < Max then
                        Max = Dist
                        Close = V.Character
                    end
                end
            end
        end
    end
    return Close
end
 
local MT = getrawmetatable(game)
local __namecall = MT.__namecall
setreadonly(MT, false)
MT.__namecall = newcclosure(function(self, ...)
    local Method = getnamecallmethod()
    if Method == "FindPartOnRay" and not checkcaller() and tostring(getfenv(0).script) == "GunInterface" then
        local Character = ClosestChar()
        if Character then
            return Character.Head, Character.Head.Position
        end
    end
 
    return __namecall(self, ...)
end)
setreadonly(MT, true)
     end)
 
    -- PLAYER
    local Player = Window:NewTab("Player")
    local PlayerSection = Player:NewSection("Player")
 
    PlayerSection:NewSlider("Walkspeed", "Changes the walkspeed", 250, 16, function(v)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = v
    end)
 
    PlayerSection:NewSlider("Jumppower", "Changes the jumppower", 250, 50, function(v)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = v
    end)
    
     --Teleports
    local Teleports = Window:NewTab("Teleports")
    local Teleports = Teleports:NewSection("Teleports")
    
    
    Teleports:NewButton("Armoury", "Makes you teleport to armoury", function()
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(836.77002, 99.9899979, 2284.42993, 1, 0, 0, 0, 1, 0, 0, 0, 1)
        end)
     
    Teleports:NewButton("Base", "Makes you teleport to Base", function()
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-975.134033, 109.323792, 2053.67236, 0.00843861606, 6.74631124e-08, -0.999964416, 1.52641615e-08, 1, 6.75943284e-08, 0.999964416, -1.58340203e-08, 0.00843861606)
        end)
       
    Teleports:NewButton("Sewers", "Makes you teleport to Sewers", function()
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(916.408386, 78.700798, 2368.22632, 0.999951601, 8.68191847e-08, -0.0098446589, -8.66753851e-08, 1, 1.50331587e-08, 0.0098446589, -1.41791414e-08, 0.999951601)
        end)
        
    Teleports:NewButton("Entrance", "Makes you teleport to Entrance", function()
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(652.77002, 99.9900055, 2289.34009, 1, 0, 0, 0, 1, 0, 0, 0, 1)
        end)
        
    Teleports:NewButton("Escape", "Makes you teleport to Escape", function()
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-896.799988, 94.1287842, 2049.05005, 1, 0, 0, 0, 1, 0, 0, 0, 1)
        end)
        
    Teleports:NewButton("Roof", "Makes you teleport to Roof", function()
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(885.549988, 135.204163, 2455.61011, 1, 0, 0, 0, 1, 0, 0, 0, 1)
    end)
    
        --Misc
     local Misc = Window:NewTab("Misc")
     local MiscSection = Misc:NewSection("Misc")
    
    
    MiscSection:NewButton("Rejoin", "Makes you rejoin", function()
       local tpservice= game:GetService("TeleportService")
       local plr = game.Players.LocalPlayer
       
       tpservice:Teleport(game.PlaceId, plr)
       
end)
       
       

       
elseif game.PlaceId == 3956818381 then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Ninja Legends", "Midnight")
 
    -- MAIN
    local Main = Window:NewTab("Main")
    local MainSection = Main:NewSection("Main")
 
    MainSection:NewToggle("Auto Swing", "Make your player autoswing", function(v)
        getgenv().autoswing = v
        while true do
            if not getgenv().autoswing then return end
            for _,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if v:FindFirstChild("ninjitsuGain") then
                    game.Players.LocalPlayer.Character.Humanoid:EquipTool(v)
                    break
                end
            end
            local A_1 = "swingKatana"
            local Event = game:GetService("Players").LocalPlayer.ninjaEvent
            Event:FireServer(A_1)
            wait(0.1)
        end
    end)
 
    MainSection:NewToggle("Auto Sell", "Makes your player autosell", function(v)
        getgenv().autosell = v
        while true do
            if getgenv().autoswing == false then return end
            game:GetService("Workspace").sellAreaCircles["sellAreaCircle16"].circleInner.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
            wait(0.1)
            game:GetService("Workspace").sellAreaCircles["sellAreaCircle16"].circleInner.CFrame = CFrame.new(0,0,0)
            wait(0.1)
        end
    end)
 
    MainSection:NewButton("Unlock all islands", "Unlocks all islands", function()
        local oldcframe = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
        for _,v in pairs(game:GetService("Workspace").islandUnlockParts:GetChildren()) do
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
            wait(0.1)
        end
        wait(0.1)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = oldcframe
    end)
    
    MainSection:NewToggle("Auto buy all swords", "Auto buys all swords", function(v)
        getgenv().buyswords = v
        while true do
            if not getgenv().buyswords then return end
            local A_1 = "buyAllSwords"
            local A_2 = "Inner Peace Island"
            local Event = game:GetService("Players").LocalPlayer.ninjaEvent
            Event:FireServer(A_1, A_2)
            wait(0.5)
        end
    end)
 
    MainSection:NewToggle("Auto buy all belts", "Auto buys all belts", function(v)
        getgenv().buybelts = v
        while true do
            if not getgenv().buybelts then return end
            local A_1 = "buyAllBelts"
            local A_2 = "Inner Peace Island"
            local Event = game:GetService("Players").LocalPlayer.ninjaEvent
            Event:FireServer(A_1, A_2)
            wait(0.5)
        end
    end)
end
