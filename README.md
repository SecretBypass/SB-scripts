-- LocalScript (coloque em StarterGui)
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local Lighting = game:GetService("Lighting")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Criar blur no fundo
local blur = Instance.new("BlurEffect")
blur.Size = 0
blur.Parent = Lighting

-- Ativar blur com tween suave
local blurTween = TweenService:Create(blur, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Size = 12})
blurTween:Play()

-- Criar GUI principal
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "SecretBypassGui"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

local main = Instance.new("Frame")
main.Name = "MainFrame"
main.AnchorPoint = Vector2.new(0.5, 0.5)
main.Position = UDim2.new(0.5, 0, 0.5, 0)
main.Size = UDim2.new(0, 250, 0, 200) -- já aparece pronto
main.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
main.BackgroundTransparency = 0.3
main.BorderSizePixel = 0
main.Parent = screenGui

local mainCorner = Instance.new("UICorner", main)
mainCorner.CornerRadius = UDim.new(0, 12)
local mainStroke = Instance.new("UIStroke", main)
mainStroke.Thickness = 2
mainStroke.Color = Color3.fromRGB(0,0,0)

-- título
local title = Instance.new("TextLabel", main)
title.Size = UDim2.new(1, 0, 0, 40)
title.Position = UDim2.new(0, 0, 0, 8)
title.BackgroundTransparency = 1
title.Text = "SECRET BYPASS"
title.TextColor3 = Color3.fromRGB(0,0,0)
title.Font = Enum.Font.GothamBold
title.TextSize = 20
title.TextXAlignment = Enum.TextXAlignment.Center
title.TextYAlignment = Enum.TextYAlignment.Center

-- caixa "Enter Key"
local keyBox = Instance.new("TextBox", main)
keyBox.Size = UDim2.new(0.8, 0, 0, 35)
keyBox.Position = UDim2.new(0.1, 0, 0.3, 0)
keyBox.PlaceholderText = "Enter Key"
keyBox.Text = ""
keyBox.ClearTextOnFocus = false
keyBox.TextColor3 = Color3.fromRGB(0,0,0)
keyBox.Font = Enum.Font.Gotham
keyBox.TextSize = 16
local keyCorner = Instance.new("UICorner", keyBox)
keyCorner.CornerRadius = UDim.new(0, 8)

-- botão "Acess Script"
local accessBtn = Instance.new("TextButton", main)
accessBtn.Size = UDim2.new(0.8, 0, 0, 35)
accessBtn.Position = UDim2.new(0.1, 0, 0.55, 0)
accessBtn.Text = "Acess Script"
accessBtn.TextColor3 = Color3.fromRGB(0,0,0)
accessBtn.Font = Enum.Font.GothamBold
accessBtn.TextSize = 16
accessBtn.BackgroundColor3 = Color3.fromRGB(255,255,255)
accessBtn.BorderSizePixel = 0
local accessCorner = Instance.new("UICorner", accessBtn)
accessCorner.CornerRadius = UDim.new(0, 8)

-- botão "Get Key"
local getBtn = Instance.new("TextButton", main)
getBtn.Size = UDim2.new(0.8, 0, 0, 35)
getBtn.Position = UDim2.new(0.1, 0, 0.75, 0)
getBtn.Text = "Get Key"
getBtn.TextColor3 = Color3.fromRGB(255,255,255)
getBtn.Font = Enum.Font.GothamBold
getBtn.TextSize = 16
getBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
getBtn.BorderSizePixel = 0
local getCorner = Instance.new("UICorner", getBtn)
getCorner.CornerRadius = UDim.new(0, 8)

-- hover efeito para botões
local function addHover(button, defaultColor, hoverColor)
    button.MouseEnter:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.2), {BackgroundColor3 = hoverColor}):Play()
    end)
    button.MouseLeave:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.2), {BackgroundColor3 = defaultColor}):Play()
    end)
end
addHover(accessBtn, Color3.fromRGB(255,255,255), Color3.fromRGB(220,220,220))
addHover(getBtn, Color3.fromRGB(0,0,0), Color3.fromRGB(40,40,40))

-- copiar link
local URL = "https://rebrand.ly/get-key"
getBtn.MouseButton1Click:Connect(function()
    if setclipboard then
        setclipboard(URL)
    end
end)

-- ação de teste no botão "Acess Script"
accessBtn.MouseButton1Click:Connect(function()
    print("Acess Script clicado!")
end)
