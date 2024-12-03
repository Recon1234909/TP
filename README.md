local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("COA HUB", "DarkTheme")
local Tab = Window:NewTab("Menu")
local Section = Tab:NewSection("Section Name")

local Plr = {}
for i, v in pairs(game:GetService("Players"):GetChildren()) do
    table.insert(Plr, v.Name) 
end

Section:NewDropdown("Select Player!", "Click To Select", Plr, function(t)
    PlayerTP = t
end)


Section:NewButton("Click To TP", "", function()
    if PlayerTP then
        local targetPlayer = game.Players[PlayerTP]
        if targetPlayer and targetPlayer.Character then
            local targetHumanoidRootPart = targetPlayer.Character:FindFirstChild("HumanoidRootPart")
            if targetHumanoidRootPart then

                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = targetHumanoidRootPart.CFrame
            end
        end
    end
end)
