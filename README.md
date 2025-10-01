-- LocalScript em StarterGui

-- Criar ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "LeaderstatsGui"
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criar Frame (janela arrastável)
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 260, 0, 170)
frame.Position = UDim2.new(0.35, 0, 0.3, 0)
frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true
frame.Parent = screenGui

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 30)
title.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
title.BorderSizePixel = 0
title.Text = "Painel Leaderstats"
title.TextColor3 = Color3.new(1,1,1)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 18
title.Parent = frame

-- Caixa de texto para nome do leaderstat
local statBox = Instance.new("TextBox")
statBox.Size = UDim2.new(0.8, 0, 0.2, 0)
statBox.Position = UDim2.new(0.1, 0, 0.3, 0)
statBox.PlaceholderText = "Nome do Leaderstat (ex: Strength)"
statBox.Text = ""
statBox.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
statBox.TextColor3 = Color3.new(1,1,1)
statBox.Font = Enum.Font.SourceSans
statBox.TextSize = 16
statBox.ClearTextOnFocus = false
statBox.Parent = frame

-- Caixa de texto para valor
local valueBox = Instance.new("TextBox")
valueBox.Size = UDim2.new(0.8, 0, 0.2, 0)
valueBox.Position = UDim2.new(0.1, 0, 0.55, 0)
valueBox.PlaceholderText = "Digite o valor..."
valueBox.Text = ""
valueBox.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
valueBox.TextColor3 = Color3.new(1,1,1)
valueBox.Font = Enum.Font.SourceSans
valueBox.TextSize = 16
valueBox.ClearTextOnFocus = false
valueBox.Parent = frame

-- Botão aplicar
local button = Instance.new("TextButton")
button.Size = UDim2.new(0.8, 0, 0.2, 0)
button.Position = UDim2.new(0.1, 0, 0.8, 0)
button.Text = "Aplicar"
button.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
button.TextColor3 = Color3.new(1,1,1)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 16
button.Parent = frame

-- Clique do botão
button.MouseButton1Click:Connect(function()
	local player = game.Players.LocalPlayer
	local stats = player:FindFirstChild("leaderstats")

	if stats then
		local statName = statBox.Text
		local stat = stats:FindFirstChild(statName)

		if stat then
			local num = tonumber(valueBox.Text)
			if num then
				stat.Value = num
			else
				warn("Digite um número válido!")
			end
		else
			warn("Leaderstat '"..statName.."' não encontrado!")
		end
	else
		warn("leaderstats não encontrado!")
	end
end)
