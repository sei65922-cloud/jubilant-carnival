local ServerStorage = game:GetService("ServerStorage")
local Workspace = game:GetService("Workspace")

-- Crie um Model chamado DragonFruit
-- e coloque-o dentro de ServerStorage.

local function spawnDragon(player)
    local fruit = ServerStorage:FindFirstChild("DragonFruit")

    if not fruit then
        warn("DragonFruit não encontrado no ServerStorage!")
        return false
    end

    local character = player.Character
    if not character then
        return false
    end

    local root = character:FindFirstChild("HumanoidRootPart")
    if not root then
        return false
    end

    local newFruit = fruit:Clone()
    newFruit.Parent = Workspace

    if newFruit:IsA("Model") then
        newFruit:PivotTo(root.CFrame * CFrame.new(0, 0, -6))
    elseif newFruit:IsA("BasePart") then
        newFruit.CFrame = root.CFrame * CFrame.new(0, 0, -6)
    end

    return true
end

-- Exemplo de uso:
-- spawnDragon(player)
