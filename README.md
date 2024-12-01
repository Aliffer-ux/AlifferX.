-- Script completo para Blox Fruits

-- Função de auto-farm
function autoFarm()
    while true do
        local enemies = game.Workspace.Enemies:GetChildren()
        for _, enemy in pairs(enemies) do
            if enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
                wait(0.5)
                game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool"):Activate()
            end
        end
        wait(1)
    end
end

-- Função de auto-quest
function autoQuest()
    while true do
        local questGivers = game.Workspace.QuestGivers:GetChildren()
        for _, questGiver in pairs(questGivers) do
            if questGiver:FindFirstChild("Quest") then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = questGiver.HumanoidRootPart.CFrame
                wait(0.5)
                fireclickdetector(questGiver.Quest.ClickDetector)
            end
        end
        wait(5)
    end
end

-- Função de auto-kill
function autoKill()
    while true do
        local enemies = game.Workspace.Enemies:GetChildren()
        for _, enemy in pairs(enemies) do
            if enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
                wait(0.5)
                game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool"):Activate()
            end
        end
        wait(1)
    end
end

-- Função de auto-collect de frutas
function autoCollectFruits()
    while true do
        local fruits = game.Workspace.Fruits:GetChildren()
        for _, fruit in pairs(fruits) do
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = fruit.CFrame
            wait(0.5)
            fireclickdetector(fruit.ClickDetector)
        end
        wait(10)
    end
end

-- Função de auto-upgrade de habilidades
function autoUpgradeSkills()
    while true do
        local player = game.Players.LocalPlayer
        local stats = player:FindFirstChild("Stats")
        if stats then
            stats.Strength.Value = stats.Strength.Value + 1
            stats.Defense.Value = stats.Defense.Value + 1
            stats.Sword.Value = stats.Sword.Value + 1
            stats.Gun.Value = stats.Gun.Value + 1
            stats.Fruit.Value = stats.Fruit.Value + 1
        end
        wait(60)
    end
end

-- Função de auto-buy
function autoBuy(itemName)
    local shop = game.Workspace.Shops:FindFirstChild(itemName)
    if shop then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = shop.HumanoidRootPart.CFrame
        wait(0.5)
        fireclickdetector(shop.ClickDetector)
    end
end

-- Função de auto-equip
function autoEquip(itemName)
    local backpack = game.Players.LocalPlayer.Backpack
    local item = backpack:FindFirstChild(itemName)
    if item then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = item.HumanoidRootPart.CFrame
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = item.CFrame
    end
end

-- Função de teletransporte para diferentes ilhas
function teleportToIsland(islandName)
    local islands = {
        ["Starter Island"] = Vector3.new(100, 50, 100),
        ["Jungle Island"] = Vector3.new(200, 50, 200),
        ["Desert Island"] = Vector3.new(300, 50, 300),
        ["Sky Island"] = Vector3.new(400, 50, 400)
    }
    local location = islands[islandName]
    if location then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(location)
    end
end

-- Exemplo de uso
spawn(autoFarm)
spawn(autoQuest)
spawn(autoKill)
spawn(autoCollectFruits)
spawn(autoUpgradeSkills)
autoBuy("Sword")
autoEquip("Sword")
teleportToIsland("Jungle Island")
