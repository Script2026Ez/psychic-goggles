-- Pastikan GUI aman dari deteksi/penghapusan otomatis game
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

-- Instances
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local InnerFrame = Instance.new("Frame")
local SpeedTextBox = Instance.new("TextBox")
local DecreaseButton = Instance.new("TextButton")
local IncreaseButton = Instance.new("TextButton")
local FlyButton = Instance.new("TextButton")
local PitchButton = Instance.new("TextButton")
local DestroyButton = Instance.new("TextButton")
local UIGradient = Instance.new("UIGradient")
local UICorner = Instance.new("UICorner")
local UIStroke = Instance.new("UIStroke")

-- ScreenGui properties (Menggunakan gethui/CoreGui agar tidak gampang diblokir game)
ScreenGui.Name = "Vehicle Fly V1"
if syn and syn.protect_gui then
    syn.protect_gui(ScreenGui)
    ScreenGui.Parent = CoreGui
elseif gethui then
    ScreenGui.Parent = gethui()
else
    pcall(function()
        ScreenGui.Parent = CoreGui
    end)
    if ScreenGui.Parent ~= CoreGui then
        ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")
    end
end
ScreenGui.ResetOnSpawn = false

-- MainFrame properties (Diperpanjang sedikit ke bawah agar pas menampung 3 tombol utama)
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
MainFrame.Position = UDim2.new(0.3, 0, 0.5, -115)
MainFrame.Size = UDim2.new(0, 191, 0, 190)
MainFrame.Active = true
MainFrame.Draggable = true

-- UIStroke properties for MainFrame
UIStroke.Parent = MainFrame
UIStroke.Color = Color3.fromRGB(0, 0, 0)
UIStroke.Thickness = 2

-- Title properties
Title.Parent = MainFrame
Title.BackgroundTransparency = 1
Title.Size = UDim2.new(1, 0, 0.17, 0)
Title.Font = Enum.Font.GothamBold
Title.Text = "Vehicle Fly V1"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true

-- InnerFrame properties
InnerFrame.Parent = MainFrame
InnerFrame.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
InnerFrame.Size = UDim2.new(1, 0, 0.83, 0)
InnerFrame.Position = UDim2.new(0, 0, 0.17, 0)

-- SpeedTextBox properties
SpeedTextBox.Parent = InnerFrame
SpeedTextBox.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
SpeedTextBox.Position = UDim2.new(0.5, -25, 0.08, 0)
SpeedTextBox.Size = UDim2.new(0, 50, 0, 26)
SpeedTextBox.Font = Enum.Font.Gotham
SpeedTextBox.Text = "1"
SpeedTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedTextBox.TextScaled = true
SpeedTextBox.PlaceholderText = "Speed"

-- DecreaseButton properties
DecreaseButton.Parent = InnerFrame
DecreaseButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
DecreaseButton.Size = UDim2.new(0, 40, 0, 26)
DecreaseButton.Position = UDim2.new(0.1, 0, 0.08, 0)
DecreaseButton.Font = Enum.Font.Gotham
DecreaseButton.Text = "-"
DecreaseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
DecreaseButton.TextScaled = true

-- IncreaseButton properties
IncreaseButton.Parent = InnerFrame
IncreaseButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
IncreaseButton.Size = UDim2.new(0, 40, 0, 26)
IncreaseButton.Position = UDim2.new(0.9, -40, 0.08, 0)
IncreaseButton.Font = Enum.Font.Gotham
IncreaseButton.Text = "+"
IncreaseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
IncreaseButton.TextScaled = true

-- FlyButton properties
FlyButton.Parent = InnerFrame
FlyButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
FlyButton.Size = UDim2.new(0.8, 0, 0.17, 0)
FlyButton.Position = UDim2.new(0.1, 0, 0.30, 0)
FlyButton.Font = Enum.Font.GothamBold
FlyButton.Text = "Fly"
FlyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FlyButton.TextScaled = true

-- PitchButton properties (Fitur Baru Pitch On/Off)
PitchButton.Parent = InnerFrame
PitchButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
PitchButton.Size = UDim2.new(0.8, 0, 0.17, 0)
PitchButton.Position = UDim2.new(0.1, 0, 0.52, 0)
PitchButton.Font = Enum.Font.GothamBold
PitchButton.Text = "Pitch: Off"
PitchButton.TextColor3 = Color3.fromRGB(255, 255, 255)
PitchButton.TextScaled = true

-- DestroyButton properties
DestroyButton.Parent = InnerFrame
DestroyButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
DestroyButton.Size = UDim2.new(0.8, 0, 0.17, 0)
DestroyButton.Position = UDim2.new(0.1, 0, 0.74, 0)
DestroyButton.Font = Enum.Font.GothamBold
DestroyButton.Text = "Destroy"
DestroyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
DestroyButton.TextScaled = true

-- UICorner properties
UICorner.CornerRadius = UDim.new(0.08, 0)
UICorner.Parent = MainFrame

-- UIGradient properties
UIGradient.Parent = MainFrame
UIGradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(45, 45, 45)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(75, 75, 75))
}

-- Button functionalities
DecreaseButton.MouseButton1Click:Connect(function()
    local speed = tonumber(SpeedTextBox.Text) or 1
    SpeedTextBox.Text = tostring(math.max(speed - 1, 1))
end)

IncreaseButton.MouseButton1Click:Connect(function()
    local speed = tonumber(SpeedTextBox.Text) or 1
    SpeedTextBox.Text = tostring(speed + 1)
end)

-- Enable Fly Function with safer handling
local velocityHandlerName = "Velocity Fly V1"
local gyroHandlerName = "VFlyGyro"
local mfly1, mfly2
local bv, bg
local pitchEnabled = false

-- Pitch Toggle Functionality
PitchButton.MouseButton1Click:Connect(function()
    pitchEnabled = not pitchEnabled
    if pitchEnabled then
        PitchButton.Text = "Pitch: On"
        PitchButton.BackgroundColor3 = Color3.fromRGB(50, 130, 50) -- Berubah warna hijau pas aktif
    else
        PitchButton.Text = "Pitch: Off"
        PitchButton.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
    end
end)

local function EnableFly()
    local char = LocalPlayer.Character
    if not char or not char:FindFirstChild("HumanoidRootPart") then return end
    
    local rootPart = char.HumanoidRootPart
    local camera = workspace.CurrentCamera
    local v3zero = Vector3.new(0, 0, 0)
    local v3inf = Vector3.new(9e9, 9e9, 9e9)
    
    -- Safe ControlModule loader
    local success, controlModule = pcall(function()
        return require(LocalPlayer.PlayerScripts:WaitForChild("PlayerModule"):WaitForChild("ControlModule"))
    end)

    bv = Instance.new("BodyVelocity")
    bv.Name = velocityHandlerName
    bv.Parent = rootPart
    bv.MaxForce = v3zero
    bv.Velocity = v3zero

    bg = Instance.new("BodyGyro")
    bg.Name = gyroHandlerName
    bg.Parent = rootPart
    bg.MaxTorque = v3inf
    bg.P = 1000
    bg.D = 50

    mfly1 = LocalPlayer.CharacterAdded:Connect(function(newChar)
        task.wait(1)
        local newRoot = newChar:WaitForChild("HumanoidRootPart", 5)
        if newRoot then
            local newBv = Instance.new("BodyVelocity")
            newBv.Name = velocityHandlerName
            newBv.Parent = newRoot
            newBv.MaxForce = v3zero
            newBv.Velocity = v3zero

            local newBg = Instance.new("BodyGyro")
            newBg.Name = gyroHandlerName
            newBg.Parent = newRoot
            newBg.MaxTorque = v3inf
            newBg.P = 1000
            newBg.D = 50
        end
    end)

    mfly2 = RunService.RenderStepped:Connect(function()
        cam = workspace.CurrentCamera
        local speed = tonumber(SpeedTextBox.Text) or 1

        local currentLegChar = LocalPlayer.Character
        if currentLegChar and currentLegChar:FindFirstChild("HumanoidRootPart") then
            local rPart = currentLegChar.HumanoidRootPart
            local velHandler = rPart:FindFirstChild(velocityHandlerName)
            local gyrHandler = rPart:FindFirstChild(gyroHandlerName)

            if velHandler and gyrHandler then
                velHandler.MaxForce = v3inf
                gyrHandler.MaxTorque = v3inf
                
                -- Mengatur rotasi berdasarkan status Pitch On/Off
                if pitchEnabled then
                    gyrHandler.CFrame = cam.CFrame
                else
                    -- Jika pitch off, arah rotasi tetap mendatar (mengabaikan kemiringan atas/bawah kamera)
                    local lookVector = cam.CFrame.LookVector
                    local flatLook = Vector3.new(lookVector.X, 0, lookVector.Z).Unit
                    if flatLook.Magnitude > 0 then
                        gyrHandler.CFrame = CFrame.new(rPart.Position, rPart.Position + flatLook)
                    else
                        gyrHandler.CFrame = cam.CFrame
                    end
                end

                local direction = Vector3.new()
                if success and controlModule then
                    pcall(function()
                        direction = controlModule:GetMoveVector()
                    end)
                end

                local calculatedVelocity = (cam.CFrame.RightVector * direction.X * speed * 50) - (cam.CFrame.LookVector * direction.Z * speed * 50)
                velHandler.Velocity = calculatedVelocity
            end
        end
    end)
end

local function DisableFly()
    local char = LocalPlayer.Character
    if char and char:FindFirstChild("HumanoidRootPart") then
        local rPart = char.HumanoidRootPart
        if rPart:FindFirstChild(velocityHandlerName) then
            rPart:FindFirstChild(velocityHandlerName):Destroy()
        end
        if rPart:FindFirstChild(gyroHandlerName) then
            rPart:FindFirstChild(gyroHandlerName):Destroy()
        end
        local humanoid = char:FindFirstChildWhichIsA("Humanoid")
        if humanoid then
            humanoid.PlatformStand = false
        end
    end
    if mfly1 then mfly1:Disconnect() end
    if mfly2 then mfly2:Disconnect() end
end

FlyButton.MouseButton1Click:Connect(function()
    if FlyButton.Text == "Fly" then
        FlyButton.Text = "UnFly"
        EnableFly()
    else
        FlyButton.Text = "Fly"
        DisableFly()
    end
end)

DestroyButton.MouseButton1Click:Connect(function()
    DisableFly()
    ScreenGui:Destroy()
end)
