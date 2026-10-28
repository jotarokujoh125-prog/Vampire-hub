# Vampire-hub
Interface mobile em Lua 
-- Interface demonstrativa para projeto proprio-- VAMPIRE HUB | RED & BLACK
-- Interface mobile demonstrativa

local VampireHub = {}

function VampireHub.Start()
    local Players = game:GetService("Players")
    local player = Players.LocalPlayer
    local playerGui = player:WaitForChild("PlayerGui")

    local old = playerGui:FindFirstChild("VampireHub")
    if old then
        old:Destroy()
    end

    local RED = Color3.fromRGB(220, 25, 55)
    local DARK = Color3.fromRGB(17, 17, 21)
    local PANEL = Color3.fromRGB(35, 28, 34)
    local WHITE = Color3.fromRGB(255, 245, 248)

    local gui = Instance.new("ScreenGui")
    gui.Name = "VampireHub"
    gui.ResetOnSpawn = false
    gui.DisplayOrder = 10
    gui.Parent = playerGui

    local main = Instance.new("Frame")
    main.Name = "Main"
    main.Size = UDim2.new(0.86, 0, 0, 390)
    main.Position = UDim2.new(0.07, 0, 0.18, 0)
    main.BackgroundColor3 = DARK
    main.BorderSizePixel = 0
    main.Active = true
    main.Parent = gui

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 14)
    corner.Parent = main

    local stroke = Instance.new("UIStroke")
    stroke.Color = RED
    stroke.Thickness = 2
    stroke.Parent = main

    local title = Instance.new("TextLabel")
    title.Name = "Title"
    title.Size = UDim2.new(1, -60, 0, 45)
    title.Position = UDim2.new(0, 12, 0, 0)
    title.BackgroundTransparency = 1
    title.Text = "VAMPIRE HUB"
    title.TextColor3 = RED
    title.Font = Enum.Font.GothamBold
    title.TextSize = 21
    title.TextXAlignment = Enum.TextXAlignment.Left
    title.Parent = main    local minimize = Instance.new("TextButton")
    minimize.Name = "Minimize"
    minimize.Size = UDim2.new(0, 38, 0, 34)
    minimize.Position = UDim2.new(1, -46, 0, 6)
    minimize.BackgroundColor3 = RED
    minimize.Text = "-"
    minimize.TextColor3 = WHITE
    minimize.Font = Enum.Font.GothamBold
    minimize.TextSize = 22
    minimize.Parent = main

    local minCorner = Instance.new("UICorner")
    minCorner.CornerRadius = UDim.new(0, 8)
    minCorner.Parent = minimize

    local content = Instance.new("Frame")
    content.Name = "Content"
    content.Size = UDim2.new(1, -20, 1, -60)
    content.Position = UDim2.new(0, 10, 0, 52)
    content.BackgroundTransparency = 1
    content.Parent = main

    local layout = Instance.new("UIListLayout")
    layout.Padding = UDim.new(0, 9)
    layout.SortOrder = Enum.SortOrder.LayoutOrder
    layout.Parent = content

    local status = Instance.new("TextLabel")
    status.Name = "Status"
    status.Size = UDim2.new(1, 0, 0, 55)
    status.BackgroundColor3 = PANEL
    status.Text = "Bem-vindo ao Vampire Hub!"
    status.TextColor3 = WHITE
    status.Font = Enum.Font.Gotham
    status.TextSize = 14
    status.TextWrapped = true
    status.LayoutOrder = 1
    status.Parent = content

    local statusCorner = Instance.new("UICorner")
    statusCorner.CornerRadius = UDim.new(0, 8)
    statusCorner.Parent = status

    local function makeButton(label, message, order)
        local button = Instance.new("TextButton")
        button.Name = "Button" .. order
        button.Size = UDim2.new(1, 0, 0, 43)
        button.BackgroundColor3 = PANEL
        button.Text = label
        button.TextColor3 = WHITE
        button.Font = Enum.Font.GothamBold
        button.TextSize = 15
        button.LayoutOrder = order
        button.Parent = content

        local c = Instance.new("UICorner")
        c.CornerRadius = UDim.new(0, 8)
        c.Parent = button

        local s = Instance.new("UIStroke")
        s.Color = RED
        s.Thickness = 1
        s.Parent = button

        button.Activated:Connect(function()
            status.Text = message
        end)
    end

    makeButton("XP e niveis", "Painel demonstrativo de XP.", 2)
    makeButton("Dinheiro", "Painel demonstrativo de dinheiro.", 3)
    makeButton("Itens", "Painel demonstrativo de itens.", 4)    makeButton(
        "Original Vampire",
        "Painel demonstrativo de progressao.",
        5
    )

    makeButton(
        "Configuracoes",
        "Vampire Hub v1.0 | Tema vermelho e preto.",
        6
    )

    local minimized = false

    minimize.Activated:Connect(function()
        minimized = not minimized
        content.Visible = not minimized

        if minimized then
            main.Size = UDim2.new(0.86, 0, 0, 48)
            minimize.Text = "+"
        else
            main.Size = UDim2.new(0.86, 0, 0, 390)
            minimize.Text = "-"
        end
    end)
end

return VampireHub
