-- WSZ AND GUSTXZ Hub - Volleyball Legends
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")

-- Configuração do Hub
local Hub = {
    Name = "WSZ AND GUSTXZ",
    Version = "1.0",
    Game = "Volleyball Legends"
}

-- Obter o serviço remoto
local function getRemote()
    return game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("_Index"):WaitForChild("sleitnick_knit@1.7.0"):WaitForChild("knit"):WaitForChild("Services"):WaitForChild("SeasonService"):WaitForChild("RF"):WaitForChild("RequestRankedReward")
end

-- Criar a interface do Hub
local hubGui = Instance.new("ScreenGui")
hubGui.Name = "WSZAndGUSTXZHub"
hubGui.ResetOnSpawn = false
hubGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
hubGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- ==================== TELA DE CARREGAMENTO ====================

local loadingGui = Instance.new("Frame")
loadingGui.Name = "LoadingScreen"
loadingGui.Size = UDim2.new(1, 0, 1, 0)
loadingGui.BackgroundColor3 = Color3.fromRGB(15, 15, 25)
loadingGui.BorderSizePixel = 0
loadingGui.ZIndex = 100
loadingGui.Parent = hubGui

local loadingGradient = Instance.new("UIGradient")
loadingGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(15, 15, 35)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(20, 25, 45)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(15, 15, 35))
})
loadingGradient.Rotation = 45
loadingGradient.Parent = loadingGui

-- Container central de loading
local loadingContainer = Instance.new("Frame")
loadingContainer.Name = "LoadingContainer"
loadingContainer.Size = UDim2.new(0, 300, 0, 300)
loadingContainer.Position = UDim2.new(0.5, -150, 0.5, -150)
loadingContainer.BackgroundTransparency = 1
loadingContainer.Parent = loadingGui

-- Círculo de carregamento (spinner)
local spinnerFrame = Instance.new("Frame")
spinnerFrame.Name = "Spinner"
spinnerFrame.Size = UDim2.new(0, 150, 0, 150)
spinnerFrame.Position = UDim2.new(0.5, -75, 0, 0)
spinnerFrame.BackgroundColor3 = Color3.fromRGB(0, 150, 255)
spinnerFrame.BorderSizePixel = 0
spinnerFrame.Parent = loadingContainer

local spinnerCorner = Instance.new("UICorner")
spinnerCorner.CornerRadius = UDim.new(1, 0)
spinnerCorner.Parent = spinnerFrame

local spinnerGradient = Instance.new("UIGradient")
spinnerGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 200, 255)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 150, 200)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 100, 150))
})
spinnerGradient.Rotation = 0
spinnerGradient.Parent = spinnerFrame

-- Spinner interno
local spinnerInner = Instance.new("Frame")
spinnerInner.Name = "SpinnerInner"
spinnerInner.Size = UDim2.new(0, 130, 0, 130)
spinnerInner.Position = UDim2.new(0.5, -65, 0.5, -65)
spinnerInner.BackgroundColor3 = Color3.fromRGB(15, 15, 25)
spinnerInner.BorderSizePixel = 0
spinnerInner.Parent = spinnerFrame

local spinnerInnerCorner = Instance.new("UICorner")
spinnerInnerCorner.CornerRadius = UDim.new(1, 0)
spinnerInnerCorner.Parent = spinnerInner

-- Animação do spinner
local function animateSpinner()
    while loadingGui.Parent and loadingGui.Visible do
        local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Linear, Enum.EasingDirection.In)
        local tween = game:GetService("TweenService"):Create(spinnerFrame, tweenInfo, {
            Rotation = 360
        })
        tween:Play()
        tween.Completed:Wait()
        spinnerFrame.Rotation = 0
    end
end

task.spawn(animateSpinner)

-- Texto de carregamento
local loadingTitle = Instance.new("TextLabel")
loadingTitle.Name = "LoadingTitle"
loadingTitle.Size = UDim2.new(1, 0, 0, 40)
loadingTitle.Position = UDim2.new(0, 0, 0, 160)
loadingTitle.BackgroundTransparency = 1
loadingTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
loadingTitle.TextSize = 24
loadingTitle.Font = Enum.Font.GothamBold
loadingTitle.Text = "⚡ CARREGANDO ⚡"
loadingTitle.TextStrokeTransparency = 0.5
loadingTitle.TextStrokeColor3 = Color3.fromRGB(0, 200, 255)
loadingTitle.Parent = loadingContainer

-- Barra de progresso
local progressBarBg = Instance.new("Frame")
progressBarBg.Name = "ProgressBarBg"
progressBarBg.Size = UDim2.new(1, 0, 0, 8)
progressBarBg.Position = UDim2.new(0, 0, 0, 215)
progressBarBg.BackgroundColor3 = Color3.fromRGB(40, 40, 60)
progressBarBg.BorderSizePixel = 0
progressBarBg.Parent = loadingContainer

local progressBarBgCorner = Instance.new("UICorner")
progressBarBgCorner.CornerRadius = UDim.new(0, 5)
progressBarBgCorner.Parent = progressBarBg

-- Barra de progresso preenchida
local progressBar = Instance.new("Frame")
progressBar.Name = "ProgressBar"
progressBar.Size = UDim2.new(0, 0, 1, 0)
progressBar.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
progressBar.BorderSizePixel = 0
progressBar.Parent = progressBarBg

local progressBarCorner = Instance.new("UICorner")
progressBarCorner.CornerRadius = UDim.new(0, 5)
progressBarCorner.Parent = progressBar

local progressGradient = Instance.new("UIGradient")
progressGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 150, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 255, 200))
})
progressGradient.Rotation = 90
progressGradient.Parent = progressBar

-- Percentual de carregamento
local progressText = Instance.new("TextLabel")
progressText.Name = "ProgressText"
progressText.Size = UDim2.new(1, 0, 0, 30)
progressText.Position = UDim2.new(0, 0, 0, 240)
progressText.BackgroundTransparency = 1
progressText.TextColor3 = Color3.fromRGB(100, 200, 255)
progressText.TextSize = 16
progressText.Font = Enum.Font.Gotham
progressText.Text = "0%"
progressText.Parent = loadingContainer

-- Animação da barra de progresso
local loadingTime = 20
local startTime = tick()

local function updateProgress()
    while loadingGui.Parent and loadingGui.Visible do
        local elapsed = tick() - startTime
        local progress = math.min(elapsed / loadingTime, 1)
        
        local tweenInfo = TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
        local tween = game:GetService("TweenService"):Create(progressBar, tweenInfo, {
            Size = UDim2.new(progress, 0, 1, 0)
        })
        tween:Play()
        
        progressText.Text = math.floor(progress * 100) .. "%"
        
        if progress >= 1 then
            break
        end
        
        task.wait(0.1)
    end
end

task.spawn(updateProgress)

-- Sumir a tela de carregamento após 20 segundos
task.wait(loadingTime)
local fadeOutInfo = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
local fadeOutTween = game:GetService("TweenService"):Create(loadingGui, fadeOutInfo, {
    BackgroundTransparency = 1
})
fadeOutTween:Play()
fadeOutTween.Completed:Wait()
loadingGui:Destroy()

-- ==================== INTERFACE PRINCIPAL ====================

-- Frame principal com gradiente
local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 450, 0, 550)
mainFrame.Position = UDim2.new(0.5, -225, 0.5, -275)
mainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 25)
mainFrame.BorderSizePixel = 0
mainFrame.Parent = hubGui
mainFrame.Visible = false

-- Efeito de borda brilhante
local borderGradient = Instance.new("UICorner")
borderGradient.CornerRadius = UDim.new(0, 15)
borderGradient.Parent = mainFrame

-- Borda externa brilhante (neon effect)
local outerBorder = Instance.new("Frame")
outerBorder.Name = "OuterBorder"
outerBorder.Size = UDim2.new(1, 4, 1, 4)
outerBorder.Position = UDim2.new(0, -2, 0, -2)
outerBorder.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
outerBorder.BorderSizePixel = 0
outerBorder.ZIndex = -1
outerBorder.Parent = mainFrame

local outerCorner = Instance.new("UICorner")
outerCorner.CornerRadius = UDim.new(0, 18)
outerCorner.Parent = outerBorder

-- Gradiente de fundo
local bgGradient = Instance.new("UIGradient")
bgGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(15, 15, 35)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(20, 25, 45)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(15, 15, 35))
})
bgGradient.Rotation = 45
bgGradient.Parent = mainFrame

-- Header com efeito cyberpunk
local headerFrame = Instance.new("Frame")
headerFrame.Name = "Header"
headerFrame.Size = UDim2.new(1, 0, 0, 80)
headerFrame.BackgroundColor3 = Color3.fromRGB(0, 150, 255)
headerFrame.BorderSizePixel = 0
headerFrame.Parent = mainFrame

local headerGradient = Instance.new("UIGradient")
headerGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 100, 200)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 200, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 100, 200))
})
headerGradient.Rotation = 90
headerGradient.Parent = headerFrame

local headerCorner = Instance.new("UICorner")
headerCorner.CornerRadius = UDim.new(0, 15)
headerCorner.Parent = headerFrame

-- Efeito de brilho no header
local glowEffect = Instance.new("Frame")
glowEffect.Name = "Glow"
glowEffect.Size = UDim2.new(1, 0, 0, 3)
glowEffect.Position = UDim2.new(0, 0, 0, 80)
glowEffect.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
glowEffect.BorderSizePixel = 0
glowEffect.Parent = mainFrame

-- Título do Hub com efeito
local titleLabel = Instance.new("TextLabel")
titleLabel.Name = "Title"
titleLabel.Size = UDim2.new(1, 0, 0, 45)
titleLabel.Position = UDim2.new(0, 0, 0, 5)
titleLabel.BackgroundTransparency = 1
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.TextSize = 28
titleLabel.Font = Enum.Font.GothamBold
titleLabel.Text = "⚡ WSZ AND GUSTXZ ⚡"
titleLabel.TextStrokeTransparency = 0.5
titleLabel.TextStrokeColor3 = Color3.fromRGB(0, 200, 255)
titleLabel.Parent = headerFrame

-- Versão
local versionLabel = Instance.new("TextLabel")
versionLabel.Name = "Version"
versionLabel.Size = UDim2.new(1, 0, 0, 20)
versionLabel.Position = UDim2.new(0, 0, 0, 50)
versionLabel.BackgroundTransparency = 1
versionLabel.TextColor3 = Color3.fromRGB(100, 200, 255)
versionLabel.TextSize = 12
versionLabel.Font = Enum.Font.Gotham
versionLabel.Text = "v1.0 | Volleyball Legends"
versionLabel.Parent = headerFrame

-- ScrollingFrame para os botões
local scrollFrame = Instance.new("ScrollingFrame")
scrollFrame.Name = "ButtonScroll"
scrollFrame.Size = UDim2.new(1, -20, 1, -110)
scrollFrame.Position = UDim2.new(0, 10, 0, 90)
scrollFrame.BackgroundTransparency = 1
scrollFrame.BorderSizePixel = 0
scrollFrame.ScrollBarThickness = 8
scrollFrame.ScrollBarImageColor3 = Color3.fromRGB(0, 200, 255)
scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
scrollFrame.Parent = mainFrame

-- Função para criar botão estilo gamer
local function createButton(name, text, position, icon, callback, hasGlow)
    local buttonContainer = Instance.new("Frame")
    buttonContainer.Name = name .. "Container"
    buttonContainer.Size = UDim2.new(1, 0, 0, 60)
    buttonContainer.Position = UDim2.new(0, 0, 0, position)
    buttonContainer.BackgroundTransparency = 1
    buttonContainer.Parent = scrollFrame
    
    local button = Instance.new("TextButton")
    button.Name = name
    button.Size = UDim2.new(1, -5, 1, 0)
    button.Position = UDim2.new(0, 0, 0, 0)
    button.BackgroundColor3 = Color3.fromRGB(25, 35, 55)
    button.TextColor3 = Color3.fromRGB(0, 255, 200)
    button.TextSize = 16
    button.Font = Enum.Font.GothamBold
    button.Text = text
    button.BorderSizePixel = 0
    button.AutoButtonColor = false
    button.Parent = buttonContainer
    
    -- Gradiente do botão
    local buttonGradient = Instance.new("UIGradient")
    buttonGradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(30, 40, 60)),
        ColorSequenceKeypoint.new(1, Color3.fromRGB(20, 30, 50))
    })
    buttonGradient.Rotation = 90
    buttonGradient.Parent = button
    
    -- Canto arredondado
    local buttonCorner = Instance.new("UICorner")
    buttonCorner.CornerRadius = UDim.new(0, 10)
    buttonCorner.Parent = button
    
    -- Borda do botão
    local buttonStroke = Instance.new("UIStroke")
    buttonStroke.Color = Color3.fromRGB(0, 150, 200)
    buttonStroke.Thickness = 2
    buttonStroke.Parent = button
    
    -- Padding do texto
    local padding = Instance.new("UIPadding")
    padding.PaddingLeft = UDim.new(0, 15)
    padding.PaddingRight = UDim.new(0, 15)
    padding.Parent = button
    
    -- GLOW BRANCO NAS LETRAS (se hasGlow for true)
    if hasGlow then
        button.TextStrokeTransparency = 0.3
        button.TextStrokeColor3 = Color3.fromRGB(255, 255, 255)
    end
    
    -- Efeito hover
    local isHovered = false
    button.MouseEnter:Connect(function()
        isHovered = true
        local tweenInfo = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
        local tween = game:GetService("TweenService"):Create(button, tweenInfo, {
            BackgroundColor3 = Color3.fromRGB(35, 50, 75)
        })
        tween:Play()
        
        buttonStroke.Color = Color3.fromRGB(0, 255, 200)
        button.TextColor3 = Color3.fromRGB(0, 255, 150)
    end)
    
    button.MouseLeave:Connect(function()
        isHovered = false
        local tweenInfo = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
        local tween = game:GetService("TweenService"):Create(button, tweenInfo, {
            BackgroundColor3 = Color3.fromRGB(25, 35, 55)
        })
        tween:Play()
        
        buttonStroke.Color = Color3.fromRGB(0, 150, 200)
        button.TextColor3 = Color3.fromRGB(0, 255, 200)
    end)
    
    -- Efeito de clique
    button.MouseButton1Click:Connect(function()
        local tweenInfo = TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.In)
        local tween = game:GetService("TweenService"):Create(button, tweenInfo, {
            BackgroundColor3 = Color3.fromRGB(0, 200, 255)
        })
        tween:Play()
        
        callback()
        
        task.wait(0.1)
        local tweenInfo2 = TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
        local tween2 = game:GetService("TweenService"):Create(button, tweenInfo2, {
            BackgroundColor3 = isHovered and Color3.fromRGB(35, 50, 75) or Color3.fromRGB(25, 35, 55)
        })
        tween2:Play()
    end)
    
    return button
end

-- Criar botões
local buttons = {
    {name = "LuckyStyle", text = "🎰 LUCKY STYLE", icon = "🎰", position = 0, glow = false},
    {name = "LuckyAbility", text = "⚡ LUCKY ABILITY", icon = "⚡", position = 75, glow = true},
    {name = "AutoYen", text = "💰 AUTO YEN", icon = "💰", position = 150, glow = true}
}

local remote = nil

-- Obter remote com segurança
pcall(function()
    remote = getRemote()
end)

-- Estados dos toggles
local states = {
    LuckyStyle = false,
    LuckyAbility = false,
    AutoYen = false
}

-- Criar botões com callbacks
createButton(buttons[1].name, buttons[1].text, buttons[1].position, buttons[1].icon, function()
    if not remote then
        pcall(function() remote = getRemote() end)
    end
    
    states.LuckyStyle = not states.LuckyStyle
    pcall(function()
        if remote then
            remote:InvokeServer(1)
        end
    end)
end, buttons[1].glow)

createButton(buttons[2].name, buttons[2].text, buttons[2].position, buttons[2].icon, function()
    if not remote then
        pcall(function() remote = getRemote() end)
    end
    
    states.LuckyAbility = not states.LuckyAbility
    pcall(function()
        if remote then
            remote:InvokeServer(4)
        end
    end)
end, buttons[2].glow)

createButton(buttons[3].name, buttons[3].text, buttons[3].position, buttons[3].icon, function()
    if not remote then
        pcall(function() remote = getRemote() end)
    end
    
    states.AutoYen = not states.AutoYen
    pcall(function()
        if remote then
            remote:InvokeServer(2)
        end
    end)
end, buttons[3].glow)

-- Atualizar tamanho do canvas
scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 250)

-- Rodapé
local footerFrame = Instance.new("Frame")
footerFrame.Name = "Footer"
footerFrame.Size = UDim2.new(1, 0, 0, 40)
footerFrame.Position = UDim2.new(0, 0, 1, -40)
footerFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 20)
footerFrame.BorderSizePixel = 0
footerFrame.Parent = mainFrame

local footerCorner = Instance.new("UICorner")
footerCorner.CornerRadius = UDim.new(0, 15)
footerCorner.Parent = footerFrame

local footerLabel = Instance.new("TextLabel")
footerLabel.Size = UDim2.new(1, -20, 1, 0)
footerLabel.Position = UDim2.new(0, 10, 0, 0)
footerLabel.BackgroundTransparency = 1
footerLabel.TextColor3 = Color3.fromRGB(100, 150, 200)
footerLabel.TextSize = 12
footerLabel.Font = Enum.Font.Gotham
footerLabel.Text = "Made by WSZ & GUSTXZ | Delta Executor"
footerLabel.TextXAlignment = Enum.TextXAlignment.Center
footerLabel.Parent = footerFrame

-- Tornar a UI arrastável
local dragStart = nil
local dragStartPos = nil

mainFrame.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragStart = input
        dragStartPos = mainFrame.Position
    end
end)

mainFrame.InputEnded:Connect(function(input, gameProcessed)
    if input == dragStart then
        dragStart = nil
    end
end)

UserInputService.InputChanged:Connect(function(input, gameProcessed)
    if dragStart then
        local delta = input.Position - dragStart.Position
        mainFrame.Position = dragStartPos + UDim2.new(0, delta.X, 0, delta.Y)
    end
end)

-- ==================== BOTÃO TOGGLE 🤺 (CANTO SUPERIOR DIREITO) ====================

-- Container para o botão toggle
local toggleContainer = Instance.new("Frame")
toggleContainer.Name = "ToggleContainer"
toggleContainer.Size = UDim2.new(0, 120, 0, 120)
toggleContainer.Position = UDim2.new(1, -130, 0, 10)
toggleContainer.BackgroundTransparency = 1
toggleContainer.ZIndex = 50
toggleContainer.Parent = hubGui

-- Borda externa decorativa 1
local borderDecor1 = Instance.new("Frame")
borderDecor1.Name = "BorderDecor1"
borderDecor1.Size = UDim2.new(1, 0, 1, 0)
borderDecor1.Position = UDim2.new(0, 0, 0, 0)
borderDecor1.BackgroundTransparency = 1
borderDecor1.BorderSizePixel = 3
borderDecor1.BorderColor3 = Color3.fromRGB(0, 200, 255)
borderDecor1.Parent = toggleContainer

-- Borda externa decorativa 2 (rotated)
local borderDecor2 = Instance.new("Frame")
borderDecor2.Name = "BorderDecor2"
borderDecor2.Size = UDim2.new(0.7, 0, 0.7, 0)
borderDecor2.Position = UDim2.new(0.15, 0, 0.15, 0)
borderDecor2.BackgroundTransparency = 1
borderDecor2.BorderSizePixel = 2
borderDecor2.BorderColor3 = Color3.fromRGB(0, 150, 200)
borderDecor2.Rotation = 45
borderDecor2.Parent = toggleContainer

-- Botão toggle principal
local toggleButton = Instance.new("TextButton")
toggleButton.Name = "ToggleButton"
toggleButton.Size = UDim2.new(0, 90, 0, 90)
toggleButton.Position = UDim2.new(0.5, -45, 0.5, -45)
toggleButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButton.TextSize = 44
toggleButton.Font = Enum.Font.GothamBold
toggleButton.Text = "🤺"
toggleButton.BorderSizePixel = 0
toggleButton.AutoButtonColor = false
toggleButton.ZIndex = 51
toggleButton.Parent = toggleContainer

-- Gradiente do botão toggle
local toggleGradient = Instance.new("UIGradient")
toggleGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 150, 255)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 200, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 100, 200))
})
toggleGradient.Rotation = 45
toggleGradient.Parent = toggleButton

-- Canto arredondado do toggle
local toggleCorner = Instance.new("UICorner")
toggleCorner.CornerRadius = UDim.new(0, 20)
toggleCorner.Parent = toggleButton

-- Borda principal do botão toggle com stroke duplo
local toggleStroke = Instance.new("UIStroke")
toggleStroke.Color = Color3.fromRGB(0, 255, 200)
tog
