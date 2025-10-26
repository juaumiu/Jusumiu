
local Player = game.Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")

-- Cria o menu
local ScreenGui = Instance.new("ScreenGui", PlayerGui)
local Frame = Instance.new("Frame", ScreenGui)
Frame.Size = UDim2.new(0, 200, 0, 150)
Frame.Position = UDim2.new(0.05, 0, 0.2, 0)
Frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
Frame.BorderSizePixel = 2
Frame.Visible = true

local Title = Instance.new("TextLabel", Frame)
Title.Size = UDim2.new(1, 0, 0, 40)
Title.Text = "🍬 Farm de Doces"
Title.BackgroundTransparency = 1
Title.TextColor3 = Color3.new(1, 1, 1)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 20

local ToggleButton = Instance.new("TextButton", Frame)
ToggleButton.Size = UDim2.new(1, -20, 0, 40)
ToggleButton.Position = UDim2.new(0, 10, 0, 60)
ToggleButton.Text = "Ativar Farm"
ToggleButton.Font = Enum.Font.GothamBold
ToggleButton.TextSize = 18
ToggleButton.BackgroundColor3 = Color3.fromRGB(60, 200, 100)

local farming = false

ToggleButton.MouseButton1Click:Connect(function()
	farming = not farming
	if farming then
		ToggleButton.Text = "Desativar Farm"
		ToggleButton.BackgroundColor3 = Color3.fromRGB(200, 60, 60)
	else
		ToggleButton.Text = "Ativar Farm"
		ToggleButton.BackgroundColor3 = Color3.fromRGB(60, 200, 100)
	end
	game.ReplicatedStorage.FarmEvent:FireServer(farming)
end)
