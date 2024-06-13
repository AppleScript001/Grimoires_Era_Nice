local Library = loadstring(game:HttpGet("https://pastebin.com/raw/KNBp0LRy"), "Coastified UI")()
repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)
local Window = Library:NewWindow("Grimoires Era")

local Section = Window:NewSection("AutoFarm")
Section:CreateLabel("Mobs|Boss")

local PlayerTP1
local TweenService = game:GetService("TweenService")

local Dropdown = Section:CreateDropdown("Select Mobs!", {"Bandit", "Bandit Commoner", "Bandit Nobleman", "Corrupt Blacksmith", "Corrupt Commoner", "Corrupt Dark Wizard", "Corrupt Magic Knight", "Corrupt Senior Magic Knight", "Corrupt Wizard", "Desert Wizard", "Evil Nobleman", "Low Mana Bandit", "Low Mana Knight", "Marauder", "Marauder Wizard", "Palm Bandit", "Strong Bandit", "Strong Marauder Wizard", "Strong Palm Bandit"}, 0, function(t)
    PlayerTP1 = t
end)
local Dropdown = Section:CreateDropdown("Select Bosses!", {"Bandit Royal", "Corrupt Nobleman", "Corrupt Wizard Boss", "Elemental Boss", "Evil Old Man", "Exiled Magic Knight Captain", "Fire Wizard", "Malicious Farmer", "Low Mana King", "Marauder Wizard Boss"}, 0, function(t)
    PlayerTP1 = t
end)

local Toggle = Section:CreateToggle("Auto [Farm]", function(Value)
_G.Hit = Value
while _G.Hit do
wait(1)  -- Wait for 1 second before checking for enemies
pcall(function()
for i,v in pairs(workspace.NPCS:GetDescendants()) do
if v.Name == PlayerTP1 then
if v.Humanoid.Health > 0 then
repeat
    local toolName = "Combat" -- Replace "YourToolNameHere" with the name of your tool
    
    local LocalPlayer = game:GetService("Players").LocalPlayer
for i, v in pairs(LocalPlayer.Backpack:GetChildren()) do
    if v:IsA('Tool') and v.Name == toolName then
        v.Parent = LocalPlayer.Character
        break -- Stop the loop after picking up the tool
    end
end
local args = {
    [1] = "Combat"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("M1"):FireServer(unpack(args))
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,5)
wait()  -- Wait a short time before checking again
until not _G.Hit or v.Humanoid.Health <= 0
end
end
end
end)
local Player = game.Players.LocalPlayer
local function onCharacterAdded(character)
    character.Archivable = false
    character:WaitForChild("HumanoidRootPart").Anchored = false
    if Player.Character then
            onCharacterAdded(Player.Character)
    end
end
    
Player.CharacterAdded:Connect(onCharacterAdded)
end
end)
Section:CreateLabel("Quest")
Eggs = {}
for i,v in pairs(workspace.NPCS.QuestGivers:GetChildren()) do
    table.insert(Eggs,v.Name) 
end

local Dropdown = Section:CreateDropdown("Select ! Quest", Eggs, 0, function(Value)
  PlayerTP = Value
end)

local Toggle = Section:CreateToggle("Auto Quest", function(Value)
  _G.quest = Value
while _G.quest do 
wait(2)
local args = {
    [1] = PlayerTP,
    [2] = PlayerTP1
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("Dialog"):FireServer(unpack(args))
end
end)
local Section = Window:NewSection("Stats")
local Toggle = Section:CreateToggle("Auto [Strength]", function(Value)
_G.Strength = Value
while _G.Strength do
wait(0.1)
local args = {
    [1] = "Strength",
    [2] = "1"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("Stats"):FireServer(unpack(args))
    end
end)
local Toggle = Section:CreateToggle("Auto [Sword]", function(Value)
_G.Sword = Value
while _G.Sword do
wait(0.1)
local args = {
    [1] = "Sword",
    [2] = "1"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("Stats"):FireServer(unpack(args))
    end
end)
local Toggle = Section:CreateToggle("Auto [Magic]", function(Value)
_G.Magic = Value
while _G.Magic do
wait(0.1)
local args = {
    [1] = "Magic",
    [2] = "1"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("Stats"):FireServer(unpack(args))
    end
end)
local Toggle = Section:CreateToggle("Auto [Mana]", function(Value)
_G.Mana = Value
while _G.Mana do
wait(0.1)
local args = {
    [1] = "Mana",
    [2] = "1"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("Stats"):FireServer(unpack(args))
    end
end)
local Toggle = Section:CreateToggle("Auto [Defense]", function(Value)
_G.Defense = Value
while _G.Defense do
wait(0.1)
local args = {
    [1] = "Defense",
    [2] = "1"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("Stats"):FireServer(unpack(args))
    end
end)
local Section = Window:NewSection("NPCs")
local Button = Section:CreateButton("Grimoire Spins", function(Value)
for i,v in pairs(workspace.NPCS.Sellers.Jack:GetDescendants()) do
if v.Name == "Head" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)
local Button = Section:CreateButton("Reset Stats", function(Value)
for i,v in pairs(workspace.NPCS.Sellers.Lofi:GetDescendants()) do
if v.Name == "Head" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)
local Button = Section:CreateButton("Popo", function(Value)
for i,v in pairs(workspace.NPCS.Sellers.Popo:GetDescendants()) do
if v.Name == "Head" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)
local Button = Section:CreateButton("Mana Light", function(Value)
for i,v in pairs(workspace.NPCS.Sellers.Rick:GetDescendants()) do
if v.Name == "Head" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)
local Button = Section:CreateButton("Roger", function(Value)
for i,v in pairs(workspace.NPCS.Sellers.Roger:GetDescendants()) do
if v.Name == "Head" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)
