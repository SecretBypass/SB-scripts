-- ui_final_SECRET BYPASS.lua
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer
local gui = Instance.new("ScreenGui")
gui.Parent = player:WaitForChild("PlayerGui")

-- Caixa principal
local box = Instance.new("Frame")
box.Size = UDim2.new(0, 350, 0, 240)
box.AnchorPoint = Vector2.new(0.5, 0.5)
box.Position = UDim2.new(1.5, 0, 0.5, 0) -- começa fora da tela (direita)
box.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
box.BorderSizePixel = 0
box.Parent = gui

-- Cantos arredondados
local boxCorner = Instance.new("UICorner")
boxCorner.CornerRadius = UDim.new(0, 15)
boxCorner.Parent = box

-- Borda rainbow animada
local rainbowStroke = Instance.new("UIStroke")
rainbowStroke.Thickness = 3
rainbowStroke.Parent = box

-- Texto "SECRET BYPASS"
local neonTitle = Instance.new("TextLabel")
neonTitle.Size = UDim2.new(1, 0, 0, 50)
neonTitle.Position = UDim2.new(0, 0, 0, 0)
neonTitle.BackgroundTransparency = 1
neonTitle.Text = "SECRET BYPASS"
neonTitle.TextScaled = true
neonTitle.Font = Enum.Font.Fantasy
neonTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
neonTitle.Parent = box

-- Stroke neon no título
local stroke = Instance.new("UIStroke")
stroke.Parent = neonTitle
stroke.Thickness = 2
stroke.Transparency = 0.3

-- Loop rainbow animado (borda + título)
task.spawn(function()
    local t = 0
    while task.wait(0.05) do
        t = t + 0.01
        local color = Color3.fromHSV(t % 1, 1, 1)
        rainbowStroke.Color = color
        neonTitle.TextColor3 = color
        stroke.Color = color
    end
end)

-- Campo de texto
local inputBox = Instance.new("TextBox")
inputBox.Size = UDim2.new(0.9, 0, 0, 40)
inputBox.Position = UDim2.new(0.05, 0, 0, 60)
inputBox.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
inputBox.Text = ""
inputBox.PlaceholderText = "enter key"
inputBox.TextColor3 = Color3.fromRGB(255,255,255)
inputBox.TextScaled = true
inputBox.Font = Enum.Font.SourceSans
inputBox.Parent = box

local inputCorner = Instance.new("UICorner")
inputCorner.CornerRadius = UDim.new(0, 10)
inputCorner.Parent = inputBox

-- Botão azul
local blueButton = Instance.new("TextButton")
blueButton.Size = UDim2.new(0.9, 0, 0, 40)
blueButton.Position = UDim2.new(0.05, 0, 0, 110)
blueButton.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
blueButton.BorderSizePixel = 0
blueButton.Text = "Acess Script"
blueButton.TextScaled = true
blueButton.Font = Enum.Font.SourceSansBold
blueButton.TextColor3 = Color3.fromRGB(255,255,255)
blueButton.Parent = box

local blueCorner = Instance.new("UICorner")
blueCorner.CornerRadius = UDim.new(0, 10)
blueCorner.Parent = blueButton

-- Botão verde
local greenButton = Instance.new("TextButton")
greenButton.Size = UDim2.new(0.9, 0, 0, 40)
greenButton.Position = UDim2.new(0.05, 0, 0, 160)
greenButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
greenButton.BorderSizePixel = 0
greenButton.Text = "Get key"
greenButton.TextScaled = true
greenButton.Font = Enum.Font.SourceSans
greenButton.TextColor3 = Color3.fromRGB(255,255,255)
greenButton.Parent = box

local greenCorner = Instance.new("UICorner")
greenCorner.CornerRadius = UDim.new(0, 10)
greenCorner.Parent = greenButton

-- Funções dos botões
blueButton.MouseButton1Click:Connect(function()
    print("acess script clicado!")
end)

greenButton.MouseButton1Click:Connect(function()
    local link = "https://rebrand.ly/get-key"
    if setclipboard then
        setclipboard(link)
        print("Link copiado: " .. link)
    else
        warn("Executor não suporta setclipboard!")
    end
end)

-- 🔹 Animação: deslizar da direita -> centro
task.wait(0.3)
TweenService:Create(
    box,
    TweenInfo.new(0.7, Enum.EasingStyle.Quint, Enum.EasingDirection.Out),
    {Position = UDim2.new(0.5, 0, 0.5, 0)}
):Play()
