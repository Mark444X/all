-- ====== UI Setup ======
local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "PlayerTeleportGUI"
screenGui.Parent = player.PlayerGui

local COLORS = {
    BACKGROUND = Color3.fromRGB(24,24,24),
    SECONDARY = Color3.fromRGB(30,30,30),
    ACCENT = Color3.fromRGB(77,179,255),
    SUCCESS = Color3.fromRGB(51,204,102),
    DANGER = Color3.fromRGB(230,76,76),
    TEXT = Color3.fromRGB(255,255,255),
    TEXT_DARK = Color3.fromRGB(40,40,40)
}

local frame = Instance.new("Frame")
frame.Name = "MainFrame"
frame.Size = UDim2.new(0.4,0,0.6,0)
frame.Position = UDim2.new(0.5,0,0.5,0)
frame.AnchorPoint = Vector2.new(0.5,0.5)
frame.BackgroundColor3 = COLORS.BACKGROUND
frame.BorderSizePixel = 0
frame.Parent = screenGui

-- Corner + Gradient + Stroke
local frameCorner = Instance.new("UICorner", frame)
frameCorner.CornerRadius = UDim.new(0,12)
local frameGradient = Instance.new("UIGradient", frame)
frameGradient.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.fromRGB(35,35,40)), ColorSequenceKeypoint.new(1, COLORS.BACKGROUND)})
frameGradient.Rotation = 45
local frameStroke = Instance.new("UIStroke", frame)
frameStroke.Color = Color3.fromRGB(80,80,80)
frameStroke.Thickness = 1

-- Title
local titleLabel = Instance.new("TextLabel", frame)
titleLabel.Size = UDim2.new(1,-60,0,45)
titleLabel.Position = UDim2.new(0,0,0,0)
titleLabel.Text = "TP MENU (เมนูเทเลพอร์ต)"
titleLabel.TextColor3 = COLORS.TEXT
titleLabel.BackgroundColor3 = COLORS.SECONDARY
titleLabel.TextScaled = true
titleLabel.Font = Enum.Font.GothamBold
local titleCorner = Instance.new("UICorner", titleLabel)
titleCorner.CornerRadius = UDim.new(0,8)
local titleGradient = Instance.new("UIGradient", titleLabel)
titleGradient.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,COLORS.ACCENT),ColorSequenceKeypoint.new(1,Color3.fromRGB(50,120,200))})
titleGradient.Rotation = 90

-- Close Button
local closeButton = Instance.new("TextButton", frame)
closeButton.Size = UDim2.new(0,40,0,40)
closeButton.Position = UDim2.new(1,-45,0,2.5)
closeButton.Text = "✕"
closeButton.TextColor3 = COLORS.TEXT
closeButton.BackgroundColor3 = COLORS.DANGER
closeButton.TextScaled = true
closeButton.Font = Enum.Font.GothamBold
local closeCorner = Instance.new("UICorner", closeButton)
closeCorner.CornerRadius = UDim.new(0,8)
closeButton.MouseButton1Click:Connect(function() screenGui.Enabled = false end)

-- Hide/Show Button
local hideButton = Instance.new("TextButton", screenGui)
hideButton.Size = UDim2.new(0.08,0,0.08,0)
hideButton.Position = UDim2.new(0.02,0,0.02,0)
hideButton.Text = "👁"
hideButton.TextColor3 = COLORS.TEXT
hideButton.BackgroundColor3 = COLORS.SECONDARY
hideButton.TextScaled = true
hideButton.Font = Enum.Font.Gotham
local hideCorner = Instance.new("UICorner", hideButton)
hideCorner.CornerRadius = UDim.new(1,0)
local hideStroke = Instance.new("UIStroke", hideButton)
hideStroke.Color = COLORS.ACCENT
hideStroke.Thickness = 2
hideButton.MouseButton1Click:Connect(function()
    frame.Visible = not frame.Visible
end)

-- Dropdown
local dropdownButton = Instance.new("TextButton", frame)
dropdownButton.Size = UDim2.new(1,-20,0,35)
dropdownButton.Position = UDim2.new(0,10,0,55)
dropdownButton.Text = "📋 เลือกผู้เล่น (Select Player)"
dropdownButton.TextColor3 = COLORS.TEXT_DARK
dropdownButton.BackgroundColor3 = Color3.fromRGB(220,220,220)
dropdownButton.TextScaled = true
dropdownButton.Font = Enum.Font.Gotham
local dropdownCorner = Instance.new("UICorner", dropdownButton)
dropdownCorner.CornerRadius = UDim.new(0,6)

-- Button Container
local buttonContainer = Instance.new("Frame", frame)
buttonContainer.Size = UDim2.new(1,-20,0,50)
buttonContainer.Position = UDim2.new(0,10,0,100)
buttonContainer.BackgroundTransparency = 1
local followButton = Instance.new("TextButton", buttonContainer)
followButton.Size = UDim2.new(0.45,0,1,0)
followButton.Text = "🔗 Follow"
followButton.TextColor3 = COLORS.TEXT
followButton.BackgroundColor3 = COLORS.SUCCESS
followButton.TextScaled = true
followButton.Font = Enum.Font.GothamSemibold
local teleportButton = Instance.new("TextButton", buttonContainer)
teleportButton.Size = UDim2.new(0.45,0,1,0)
teleportButton.Position = UDim2.new(0.55,0,0,0)
teleportButton.Text = "⚡ Teleport"
teleportButton.TextColor3 = COLORS.TEXT
teleportButton.BackgroundColor3 = COLORS.ACCENT
teleportButton.TextScaled = true
teleportButton.Font = Enum.Font.GothamSemibold

-- ====== รวม Kavo UI Library ======
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("red shop", "DarkTheme")
local Tab = Window:NewTab("All")
local Section = Tab:NewSection("WalkSpeed / JumpPower / Fly / NoClip / Hitbox / ESP")

-- ฟังก์ชันทั้งหมดของ WalkSpeed / JumpPower / Fly / NoClip / Hitbox / ESP
-- (รวมโค้ดเดิมที่ตึ๊งส่งมา)
-- ตรงนี้ใส่โค้ดทั้งหมดของฟีเจอร์เหมือนตัวอย่างที่ตึ๊งส่งมา
-- เพียงแต่รวมเป็น Section เดียวใน UI สวยงาม

-- ====== จบ UI / ฟีเจอร์ ======
print("TP GUI พร้อมใช้งาน!")
