local A1 = loadstring(game:HttpGet(string.char(104, 116, 116, 112, 115, 58, 47, 47, 114, 97, 119, 46, 103, 105, 116, 104, 117, 98, 117, 115, 101, 114, 99, 111, 110, 116, 101, 110, 116, 46, 99, 111, 109, 47, 115, 104, 108, 101, 120, 119, 97, 114, 101, 47, 79, 114, 105, 111, 110, 47, 109, 97, 105, 110, 47, 115, 111, 117, 114, 99, 101)))()
local A2 = A1:MakeWindow({Name = string.char(72, 120), HidePremium = true, SaveConfig = true, ConfigFolder = string.char(67, 102, 103)})
local A3 = A2:MakeTab({Name = string.char(73, 110, 102), Icon = "rbxassetid://4483345998", PremiumOnly = false})

local function A4(...)
    local V1, V2 = ...
    local V3 = 0
    while V3 == 0 do
        if V3 == 0 then
            A3:AddToggle({
                Name = V1,
                Default = false,
                Callback = function(C1)
                    local S1 = game:GetService("ReplicatedStorage").Remotes.Server.Combat.Skill
                    local S2 = {V2}
                    S1:FireServer(table.unpack(S2))
                    print(V1 .. tostring(C1):reverse():reverse())
                end
            })
            V3 = 1
        end
    end
end

local A5 = {
    {string.char(68), "Domain Expansion: Unlimited Void"},
    {string.sub("Hollow Purple", 1, 2), "Infinity: Hollow Purple"},
    {"IR", "Infinity: Reversal Red"},
    {"IB", "Infinity: Lapse Blue"},
    {"SE", "Maximum: Six Eyes"},
    {"IP", "Infinity: Spatial Pummel"},
    {"RT", "Infinity: Red Transmission"},
    {"IM", "Infinity: Mugen"},
    {"CIM", "Domain Expansion: Coffin Of The Iron Mountain"},
    {"VF", "Volcano: Fissure"},
    {"MM", "Maximum: Meteor"},
    {"VMC", "Volcano: Molten Chamber"},
    {"VE", "Volcano: Eruption"},
    {"VI", "Volcano: Ember Insects"},
    {"VP", "Volcano: Molten Palm"}
}

for i = 1, #A5 do
    local K = A5[i]
    A4(K[1], K[2])
end

local A6, A7 = false, _G.CD or 2000

A3:AddToggle({
    Name = string.char(75, 65),
    Default = false,
    Callback = function(C2)
        A6 = C2
        local A8 = A6 and spawn
        local A9 = function()
            while A6 do
                wait()
                pcall(function()
                    for _, J in next, game:GetService("Workspace").Objects.Mobs:GetChildren() do
                        if J:FindFirstChild("HumanoidRootPart") then
                            local P = (J.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
                            if P <= A7 then
                                J.Humanoid.Health = 0
                            end
                        end
                    end
                end)
            end
        end
        if A8 then
            A8(A9)
        else
            print(string.char(75, 65) .. " disabled.")
        end
    end
})

local A10 = A2:MakeTab({Name = string.char(76, 118, 108), Icon = "rbxassetid://4483345998", PremiumOnly = true})

local function A11(...)
    local V4, V5 = ...
    A10:AddButton({
        Name = V4,
        Callback = function()
            local S3 = game:GetService("ReplicatedStorage").Remotes.Server.Data.TakeQuest
            local S4 = {V5}
            S3:InvokeServer(table.unpack(S4))
        end
    })
end

local A12 = {
    {string.char(78, 84, 81), {type = string.char(69), set = "NTSet", rewards = {essence = 10, chestMeter = 75, exp = 8301880, cash = 40090}}},
    {"UVQ", {type = "K", set = "UVSet", rewards = {essence = 10, chestMeter = 75, exp = 7125485, cash = 40936}}},
    {"STQ", {type = "E", set = "STSet", rewards = {essence = 10, chestMeter = 75, exp = 6257802, cash = 40813}}},
    {"KCQ", {type = "E", set = "KCSet", rewards = {essence = 10, chestMeter = 75, exp = 8301880, cash = 40900}}},
    {"YFQ", {type = "K", set = "YFSet", rewards = {essence = 10, chestMeter = 75, exp = 7015600, cash = 50000}}}
}

for i = 1, #A12 do
    local L = A12[i]
    A11(L[1], L[2])
end

A1:Init()
