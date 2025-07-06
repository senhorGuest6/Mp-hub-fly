# Mp-hub-fly
Fly Gui voar
-- Mp Hub Fly para Celular
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = char:WaitForChild("HumanoidRootPart")

local flying = false
local speed = 50
local bodyGyro
local bodyVelocity

-- Criar botão na tela
local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 100, 0, 50)
button.Position = UDim2.new(0, 20, 1, -70)
button.Text = "Ativar Voo"
button.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
button.TextColor3 = Color3.new(1, 1, 1)
button.TextScaled = true
button.BorderSizePixel = 0
button.Parent = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

-- Função para voar
function startFlying()
    flying = true
    button.Text = "Desativar Voo"

    bodyGyro = Instance.new("BodyGyro")
    bodyGyro.P = 9e4
    bodyGyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
    bodyGyro.CFrame = humanoidRootPart.CFrame
    bodyGyro.Parent = humanoidRootPart

    bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.velocity = Vector3.zero
    bodyVelocity.maxForce = Vector3.new(9e9, 9e9, 9e9)
    bodyVelocity.Parent = humanoidRootPart

    spawn(function()
        while flying do
            task.wait()
            local moveDir = Vector3.zero
            if UserInputService:IsKeyDown(Enum.KeyCode.W) then
                moveDir = workspace.CurrentCamera.CFrame.LookVector
            elseif UserInputService.TouchEnabled then
                moveDir = workspace.CurrentCamera.CFrame.LookVector
            end
            bodyGyro.CFrame = workspace.CurrentCamera.CFrame
            bodyVelocity.Velocity = moveDir * speed
        end
    end)
end

-- Função para parar voo
function stopFlying()
    flying = false
    button.Text = "Ativar Voo"
    if bodyGyro then bodyGyro:Destroy() end
    if bodyVelocity then bodyVelocity:Destroy() end
end

-- Clique do botão
button.MouseButton1Click:Connect(function()
    if flying then
        stopFlying()
    else
        startFlying()
    end
end)
