local player = game.Players.LocalPlayer
local userInputService = game:GetService("UserInputService")
local runService = game:GetService("RunService")

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")
screenGui.ResetOnSpawn = false
screenGui.Name = "BetterHack"

local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local gui = playerGui:WaitForChild("ScreenGui")

local frame = Instance.new("Frame")
frame.Name = "Main"
frame.Size = UDim2.new(0, 563,0, 403)
frame.Position = UDim2.new(0.5, -282, 0.5, -180)
frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
frame.BackgroundTransparency = 0.1
frame.BorderSizePixel = 0
frame.Parent = screenGui
frame.Visible = true

local uiStroke = Instance.new("UIStroke")
uiStroke.Parent = frame
uiStroke.Thickness = 1.8

local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(0, 10)
uiCorner.Parent = frame

local closeButton = Instance.new("TextButton")
closeButton.Text = "X"
closeButton.Size = UDim2.new(0, 50, 0, 50)
closeButton.Position = UDim2.new(1, -55, 0, 5)
closeButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
closeButton.Font = Enum.Font.SourceSansBold
closeButton.TextSize = 20
closeButton.Parent = frame

closeButton.MouseButton1Click:Connect(function()
screenGui:Destroy()
end)

local dragging = false
local dragStart
local startPos

frame.InputBegan:Connect(function(input)
if input.UserInputType == Enum.UserInputType.MouseButton1 then
dragging = true
dragStart = input.Position
startPos = frame.Position
end
end)

frame.InputChanged:Connect(function(input)
if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
local delta = input.Position - dragStart
frame.Position = UDim2.new(
startPos.X.Scale,
startPos.X.Offset + delta.X,
startPos.Y.Scale,
startPos.Y.Offset + delta.Y
)
end
end)

frame.InputEnded:Connect(function(input)
if input.UserInputType == Enum.UserInputType.MouseButton1 then
dragging = false
end
end)

local tabs = {"Troll", "Kill Mode", "Visual", "Player","Auto Shoot","Settings"}
local tabButtons = {}
local frames = {}

for i, tabName in ipairs(tabs) do
local button = Instance.new("TextButton")
button.Text = tabName
button.Size = UDim2.new(0, 180, 0, 50)
button.Position = UDim2.new(0.02, 0, 0.03 + (i - 1) * 0.14, 0)
button.BackgroundColor3 = Color3.fromRGB(170, 170, 170)
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 20
button.Parent = frame

local buttonCorner = Instance.new("UICorner")
buttonCorner.CornerRadius = UDim.new(0, 10)
buttonCorner.Parent = button

tabButtons[tabName] = button

local tabFrame = Instance.new("Frame")
tabFrame.Name = tabName
tabFrame.Size = UDim2.new(0, 358, 0, 266)
tabFrame.Position = UDim2.new(0.351, 0,0.172, 0)
tabFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
tabFrame.BorderSizePixel = 0
tabFrame.Visible = i == 1
tabFrame.Parent = frame

local tabFrameCorner = Instance.new("UICorner")
tabFrameCorner.CornerRadius = UDim.new(0, 10)
tabFrameCorner.Parent = tabFrame

local uiStroke = Instance.new("UIStroke")
uiStroke.Parent = tabFrame
uiStroke.Thickness = 1.8

frames[tabName] = tabFrame
end

for tabName, button in pairs(tabButtons) do
button.MouseButton1Click:Connect(function()
for name, tabFrame in pairs(frames) do
tabFrame.Visible = name == tabName
end
end)
end

table.insert(tabs, "Auto Shoot")
local autoShootFrame = Instance.new("Frame")
autoShootFrame.Size = UDim2.new(0, 358, 0, 266)
autoShootFrame.Position = UDim2.new(0.351, 0,0.172, 0)
autoShootFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
autoShootFrame.BorderSizePixel = 0
autoShootFrame.Visible = false
autoShootFrame.Parent = frame
local uiStroke = Instance.new("UIStroke")
uiStroke.Parent = autoShootFrame
uiStroke.Thickness = 1.8

local trollFrame = frames["Troll"]

local function createControl(inputPlaceholder, buttonText, position, callback)
local input = Instance.new("TextBox")
input.Text = ""
input.PlaceholderText = inputPlaceholder
input.Size = UDim2.new(0, 160, 0, 50)
input.Position = UDim2.new(0.05, 0, position, 0)
input.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
input.TextColor3 = Color3.fromRGB(0, 0, 0)
input.Font = Enum.Font.FredokaOne
input.TextSize = 20
input.Parent = trollFrame

local button = Instance.new("TextButton")
button.Text = buttonText
button.Size = UDim2.new(0, 160, 0, 50)
button.Position = UDim2.new(0.55, 0, position, 0)
button.BackgroundColor3 = Color3.fromRGB(0, 255, 157)
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.Font = Enum.Font.FredokaOne
button.TextSize = 20
button.Parent = trollFrame

local inputCorner = Instance.new("UICorner")
inputCorner.CornerRadius = UDim.new(0, 10)
inputCorner.Parent = input

local buttonCorner = Instance.new("UICorner")
buttonCorner.CornerRadius = UDim.new(0, 10)
buttonCorner.Parent = button

button.MouseButton1Click:Connect(function()
callback(input.Text)
end)
end

createControl("Enter Speed", "Set Speed", 0.05, function(input)
local speed = tonumber(input)
if speed and speed > 0 then
local character = player.Character
if character and character:FindFirstChild("Humanoid") then
character.Humanoid.WalkSpeed = speed
end
end
end)

createControl("Enter JumpPower", "Set JumpPower", 0.35, function(input)
local jumpPower = tonumber(input)
if jumpPower and jumpPower > 0 then
local character = player.Character
if character and character:FindFirstChild("Humanoid") then
character.Humanoid.JumpPower = jumpPower
end
end
end)

createControl("Enter Health", "Set Health", 0.65, function(input)
local health = tonumber(input)
if health and health > 0 then
local character = player.Character
if character and character:FindFirstChild("Humanoid") then
character.Humanoid.MaxHealth = health
character.Humanoid.Health = health
end
end
end)

local playerFrame = frames["Player"]
local noclipEnabled = false
local noclipButton = Instance.new("TextButton")
noclipButton.Text = "Enable Noclip"
noclipButton.Size = UDim2.new(0, 160, 0, 50)
noclipButton.Position = UDim2.new(0.05, 0, 0.05, 0)
noclipButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
noclipButton.TextColor3 = Color3.fromRGB(255, 255, 255)
noclipButton.Font = Enum.Font.SourceSansBold
noclipButton.TextSize = 20
noclipButton.Parent = playerFrame

noclipButton.MouseButton1Click:Connect(function()
noclipEnabled = not noclipEnabled
noclipButton.Text = noclipEnabled and "Disable Noclip" or "Enable Noclip"
runService.Stepped:Connect(function()
if noclipEnabled and player.Character then
for _, part in pairs(player.Character:GetChildren()) do
if part:IsA("BasePart") then
part.CanCollide = false
end
end
end
end)
end)

local infiniteJumpEnabled = false
local infiniteJumpButton = Instance.new("TextButton")
infiniteJumpButton.Text = "Enable Infinite Jump"
infiniteJumpButton.Size = UDim2.new(0, 160, 0, 50)
infiniteJumpButton.Position = UDim2.new(0.05, 0, 0.25, 0)
infiniteJumpButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
infiniteJumpButton.TextColor3 = Color3.fromRGB(255, 255, 255)
infiniteJumpButton.Font = Enum.Font.SourceSansBold
infiniteJumpButton.TextSize = 20
infiniteJumpButton.Parent = playerFrame

infiniteJumpButton.MouseButton1Click:Connect(function()
infiniteJumpEnabled = not infiniteJumpEnabled
infiniteJumpButton.Text = infiniteJumpEnabled and "Disable Infinite Jump" or "Enable Infinite Jump"
end)

userInputService.JumpRequest:Connect(function()
if infiniteJumpEnabled and player.Character and player.Character:FindFirstChild("Humanoid") then
player.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
end
end)

local godModeEnabled = false
local godModeButton = Instance.new("TextButton")
godModeButton.Text = "Enable GodMode"
godModeButton.Size = UDim2.new(0, 160, 0, 50)
godModeButton.Position = UDim2.new(0.05, 0, 0.45, 0)
godModeButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
godModeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
godModeButton.Font = Enum.Font.SourceSansBold
godModeButton.TextSize = 20
godModeButton.Parent = playerFrame

godModeButton.MouseButton1Click:Connect(function()
godModeEnabled = not godModeEnabled
godModeButton.Text = godModeEnabled and "Disable GodMode" or "Enable GodMode"
if godModeEnabled then
runService.Stepped:Connect(function()
local humanoid = player.Character and player.Character:FindFirstChild("Humanoid")
if humanoid then
humanoid.MaxHealth = math.huge
humanoid.Health = math.huge
end
end)
end
end)

local settingsFrame = frames["Settings"]

local visualsFrame = frames["Visual"]

local espEnabled = false
local outlinesEnabled = false

local outlineButton = Instance.new("TextButton")
outlineButton.Text = "Enable Outlines"
outlineButton.Size = UDim2.new(0, 160, 0, 50)
outlineButton.Position = UDim2.new(0.05, 0, 0.1, 0)
outlineButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
outlineButton.TextColor3 = Color3.fromRGB(255, 255, 255)
outlineButton.Font = Enum.Font.SourceSansBold
outlineButton.TextSize = 20
outlineButton.Parent = visualsFrame

local function updateOutlines()
for _, obj in pairs(workspace:GetDescendants()) do
if obj:IsA("BasePart") and obj:FindFirstChild("Highlight") then
local highlight = obj.Highlight
highlight.OutlineTransparency = outlinesEnabled and 0 or 1
end
end
end

local function toggleOutlines()
outlinesEnabled = not outlinesEnabled
outlineButton.Text = outlinesEnabled and "Disable Outlines" or "Enable Outlines"
updateOutlines()
end

outlineButton.MouseButton1Click:Connect(toggleOutlines)

local killModeFrame = frames["Kill Mode"]

local killAuraEnabled = false
local killFriends = false

local killauraButton = Instance.new("TextButton")
killauraButton.Text = "Enable Killaura"
killauraButton.Size = UDim2.new(0, 160, 0, 50)
killauraButton.Position = UDim2.new(0.05, 0, 0.05, 0)
killauraButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
killauraButton.TextColor3 = Color3.fromRGB(255, 255, 255)
killauraButton.Font = Enum.Font.SourceSansBold
killauraButton.TextSize = 20
killauraButton.Parent = killModeFrame

killauraButton.MouseButton1Click:Connect(function()
killAuraEnabled = not killAuraEnabled
killauraButton.Text = killAuraEnabled and "Disable Killaura" or "Enable Killaura"
end)

local killFriendsButton = Instance.new("TextButton")
killFriendsButton.Text = "Kill Friends: Off"
killFriendsButton.Size = UDim2.new(0, 160, 0, 50)
killFriendsButton.Position = UDim2.new(0.05, 0, 0.35, 0)
killFriendsButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
killFriendsButton.TextColor3 = Color3.fromRGB(255, 255, 255)
killFriendsButton.Font = Enum.Font.SourceSansBold
killFriendsButton.TextSize = 20
killFriendsButton.Parent = killModeFrame

killFriendsButton.MouseButton1Click:Connect(function()
killFriends = not killFriends
killFriendsButton.Text = killFriends and "Kill Friends: On" or "Kill Friends: Off"
killFriendsButton.BackgroundColor3 = killFriends and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(255, 0, 0)
end)
runService.RenderStepped:Connect(function()
if killAuraEnabled and player.Character then
local knife = player.Backpack:FindFirstChild("Knife") or player.Character:FindFirstChild("Knife")
if knife then
for _, target in pairs(game.Players:GetPlayers()) do
if target ~= player and target.Character and target.Character:FindFirstChild("HumanoidRootPart") then
if not killFriends and player:IsFriendsWith(target.UserId) then
continue
end
target.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame
end
end
end
end
end)

local autoShootCorner = Instance.new("UICorner")
autoShootCorner.CornerRadius = UDim.new(0, 10)
autoShootCorner.Parent = autoShootFrame

frames["Auto Shoot"] = autoShootFrame

local autoShootEnabled = false
local hitboxSize = 1000

local Aimbot = Instance.new("TextButton")
Aimbot.Text = "On Aimbot"
Aimbot.Size = UDim2.new(0, 160, 0, 50)
Aimbot.Position = UDim2.new(0.05, 0, 0.05, 0)
Aimbot.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
Aimbot.TextColor3 = Color3.fromRGB(255, 255, 255)
Aimbot.Font = Enum.Font.SourceSansBold
Aimbot.TextSize = 20
Aimbot.Parent = autoShootFrame

Aimbot.MouseButton1Click:Connect(function()
autoShootEnabled = not autoShootEnabled
Aimbot.Text = autoShootEnabled and "Off Auto Shoot" or "On Auto Shoot"
end)

local sizeCorner = Instance.new("UICorner")
sizeCorner.CornerRadius = UDim.new(0, 10)
sizeCorner.Parent = Aimbot

local visualFrame = frames["Visual"]

local espButton = Instance.new("TextButton")
espButton.Text = "Enable ESP"
espButton.Size = UDim2.new(0, 160, 0, 50)
espButton.Position = UDim2.new(0.05, 0, 0.1, 0)
espButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
espButton.TextColor3 = Color3.fromRGB(255, 255, 255)
espButton.Font = Enum.Font.SourceSansBold
espButton.TextSize = 20
espButton.Parent = visualFrame

local function checkTool(player)
local character = player.Character
local backpack = player:FindFirstChild("Backpack")

if character then
for _, tool in ipairs(character:GetChildren()) do
if tool:IsA("Tool") then
if tool.Name == "Knife" then
return "Knife"
elseif tool.Name == "Gun" then
return "Gun"
end
end
end
end

if backpack then
for _, tool in ipairs(backpack:GetChildren()) do
if tool:IsA("Tool") then
if tool.Name == "Knife" then
return "Knife"
elseif tool.Name == "Gun" then
return "Gun"
end
end
end
end

return nil
end

local function createESP(player)
local character = player.Character or player.CharacterAdded:Wait()
if not character:FindFirstChild("Head") then return end

local highlight = Instance.new("Highlight", character)
highlight.FillTransparency = 1
highlight.OutlineTransparency = 0

local billboard = Instance.new("BillboardGui", character.Head)
billboard.Size = UDim2.new(0, 200, 0, 50)
billboard.AlwaysOnTop = true
billboard.Name = "ESP"

local nameLabel = Instance.new("TextLabel", billboard)
nameLabel.Size = UDim2.new(1, 0, 1, 0)
nameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
nameLabel.BackgroundTransparency = 1
nameLabel.Font = Enum.Font.SourceSansBold
nameLabel.TextSize = 14
nameLabel.TextStrokeTransparency = 0

local function updateESP()
if character:FindFirstChild("Humanoid") then
nameLabel.Text = player.Name .. " | HP: " .. math.floor(character.Humanoid.Health)

  local tool = checkTool(player)
  if tool == "Knife" then
    highlight.OutlineColor = Color3.fromRGB(255, 0, 0)
  elseif tool == "Gun" then
    highlight.OutlineColor = Color3.fromRGB(0, 0, 255)
  else
    highlight.OutlineColor = Color3.fromRGB(0, 255, 0)
  end
end
end

game:GetService("RunService").RenderStepped:Connect(updateESP)
end

local espEnabled = false

local function toggleESP()
espEnabled = not espEnabled
espButton.Text = espEnabled and "Disable ESP" or "Enable ESP"

if espEnabled then
for _, plr in pairs(game.Players:GetPlayers()) do
if plr ~= player then
createESP(plr)
end
end

game.Players.PlayerAdded:Connect(function(newPlayer)
  createESP(newPlayer)
end)
else
for _, plr in pairs(game.Players:GetPlayers()) do
local character = plr.Character
if character and character:FindFirstChild("Highlight") then
character.Highlight:Destroy()
end
if character and character:FindFirstChild("Head"):FindFirstChild("ESP") then
character.Head.ESP:Destroy()
end
end
end
end

espButton.MouseButton1Click:Connect(toggleESP)

local bhopEnabled = false
local strafeEnabled = false
local currentDirection = Vector3.new()

local bhopEnabled = true
local speedIncrement = 90
local maxSpeed = 360
local baseWalkSpeed = 16

local function enableBhop()
local currentSpeed = baseWalkSpeed

if player.Character and player.Character:FindFirstChild("Humanoid") then
player.Character.Humanoid.WalkSpeed = currentSpeed
end

userInputService.InputBegan:Connect(function(input, isProcessed)
if not bhopEnabled or isProcessed then return end
if input.KeyCode == Enum.KeyCode.Space then
local character = player.Character
if character and character:FindFirstChild("Humanoid") then
local humanoid = character.Humanoid
if humanoid.FloorMaterial ~= Enum.Material.Air then
currentSpeed = math.min(currentSpeed + speedIncrement, maxSpeed)
humanoid.WalkSpeed = currentSpeed
end
end
end
end)

userInputService.InputEnded:Connect(function(input, isProcessed)
if not bhopEnabled or isProcessed then return end
if input.KeyCode == Enum.KeyCode.Space then
local character = player.Character
if character and character:FindFirstChild("Humanoid") then
local humanoid = character.Humanoid
humanoid.WalkSpeed = baseWalkSpeed
end
end
end)
end

local function enableStrafe()
userInputService.InputBegan:Connect(function(input)
if strafeEnabled then
if input.KeyCode == Enum.KeyCode.A then
currentDirection = Vector3.new(-1, 0, 0)
elseif input.KeyCode == Enum.KeyCode.D then
currentDirection = Vector3.new(1, 0, 0)
end
end
end)

userInputService.InputEnded:Connect(function(input)
if input.KeyCode == Enum.KeyCode.A or input.KeyCode == Enum.KeyCode.D then
currentDirection = Vector3.new()
end
end)

runService.RenderStepped:Connect(function()
if strafeEnabled and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
local rootPart = player.Character.HumanoidRootPart
local direction = rootPart.CFrame.RightVector * currentDirection.X
rootPart.Velocity = Vector3.new(direction.X * 50, rootPart.Velocity.Y, direction.Z * 50)
end
end)
end

local playerFrame = frames["Player"]

local bhopButton = Instance.new("TextButton")
bhopButton.Text = "Enable Bhop"
bhopButton.Size = UDim2.new(0, 160, 0, 50)
bhopButton.Position = UDim2.new(0.05, 0, 0.65, 0)
bhopButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
bhopButton.TextColor3 = Color3.fromRGB(255, 255, 255)
bhopButton.Font = Enum.Font.SourceSansBold
bhopButton.TextSize = 20
bhopButton.Parent = playerFrame

bhopButton.MouseButton1Click:Connect(function()
bhopEnabled = not bhopEnabled
bhopButton.Text = bhopEnabled and "Disable Bhop" or "Enable Bhop"
if bhopEnabled then
enableBhop()
end
end)

--[[local strafeButton = Instance.new("TextButton")
strafeButton.Text = "Enable Strafe"
strafeButton.Size = UDim2.new(0, 160, 0, 50)
strafeButton.Position = UDim2.new(0.05, 0, 0.85, 0)
strafeButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
strafeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
strafeButton.Font = Enum.Font.SourceSansBold
strafeButton.TextSize = 20
strafeButton.Parent = playerFrame

strafeButton.MouseButton1Click:Connect(function()
strafeEnabled = not strafeEnabled
strafeButton.Text = strafeEnabled and "Disable Strafe" or "Enable Strafe"
if strafeEnabled then
enableStrafe()
end
end)]]

local settingsFrame = frames["Settings"]

local strokeMode = "Classic"
local strokeConnections = {}

local function applyStrokeMode()
for _, uiElement in pairs(screenGui:GetDescendants()) do
if uiElement:IsA("UIStroke") then
if strokeMode == "Classic" then
uiElement.Color = Color3.fromRGB(0, 0, 0)
elseif strokeMode == "Rainbow" then
if strokeConnections[uiElement] then
strokeConnections[uiElement]:Disconnect()
end

    local connection
    connection = runService.RenderStepped:Connect(function()
      uiElement.Color = Color3.fromHSV(tick() % 5 / 5, 1, 1)
    end)
    strokeConnections[uiElement] = connection
  end
end
end

if strokeMode == "Classic" then
for _, connection in pairs(strokeConnections) do
connection:Disconnect()
end
strokeConnections = {}
end
end

local strokeModeButton = Instance.new("TextButton")
strokeModeButton.Text = "Stroke Mode: Classic"
strokeModeButton.Size = UDim2.new(0, 160, 0, 50)
strokeModeButton.Position = UDim2.new(0.05, 0, 0.1, 0)
strokeModeButton.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
strokeModeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
strokeModeButton.Font = Enum.Font.SourceSansBold
strokeModeButton.TextSize = 20
strokeModeButton.Parent = settingsFrame

strokeModeButton.MouseButton1Click:Connect(function()
strokeMode = (strokeMode == "Classic") and "Rainbow" or "Classic"
strokeModeButton.Text = "Stroke Mode: " .. strokeMode
applyStrokeMode()
end)

applyStrokeMode()

local Wremia = Instance.new("TextButton")
Wremia.Text = "Time: Day"
Wremia.Size = UDim2.new(0, 160, 0, 50)
Wremia.Position = UDim2.new(0.05, 0, 0.40, 0)
Wremia.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
Wremia.TextColor3 = Color3.fromRGB(255, 255, 255)
Wremia.Font = Enum.Font.SourceSansBold
Wremia.TextSize = 20
Wremia.Parent = settingsFrame
local currentTime = "Day"

local function changeTime()
local lighting = game:GetService("Lighting")

if currentTime == "Day" then
currentTime = "Night"
lighting.ClockTime = 18
else
currentTime = "Day"
lighting.ClockTime = 12
end
end

Wremia.MouseButton1Click:Connect(function()
if currentTime == "Day" then
Wremia.Text = "Time: Night"
else
Wremia.Text = "Time: Day"
end
changeTime()
end)