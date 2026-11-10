--[================================================================[
    Script Name: sara+0v0 hack (Universal Shooter)
    Executor: Delta (Android)
    Description: Advanced Universal ESP, Aimbot, Hitbox Expander, 
                 Instant Reload & Magic Bullet Tracker.
--================================================================]--

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local CoreGui = game:GetService("CoreGui")
local UserInputService = game:GetService("UserInputService")
local Camera = workspace.CurrentCamera
local LocalPlayer = Players.LocalPlayer

-- إزالة أي واجهة قديمة لمنع التكرار
if CoreGui:FindFirstChild("Sara0v0Hack") then
    CoreGui.Sara0v0Hack:Destroy()
end

-- إعدادات الهاك (Config)
getgenv().SaraConfig = {
    ESP_Enabled = false,
    ESP_Line = false,
    ESP_Box3D = false,
    ESP_Skeleton = false,
    ESP_Alert = false,
    ESP_Distance = false,
    ESP_Color = Color3.fromRGB(255, 255, 255),
    
    Aimbot_Enabled = false,
    Aimbot_Smooth = 1, -- قوي كلش
    Aimbot_Part = "Head",
    Aimbot_Mode = "FOV", -- FOV أو 360
    Aimbot_FOV = 150,
    Aimbot_VisibleCheck = false, -- اللاعبين الظاهرين فقط (بدون كفر)
    
    Hitbox_Size = 2,
    SkipReload = false,
    BulletTrack = false
}

-- بناء واجهة المستخدم (GUI)
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "Sara0v0Hack"
ScreenGui.Parent = CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
MainFrame.Position = UDim2.new(0.5, -225, 0.5, -175)
MainFrame.Size = UDim2.new(0, 450, 0, 350)
MainFrame.Active = true
MainFrame.Draggable = true -- قابلة للسحب على الشاشة

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 10)
UICorner.Parent = MainFrame

-- حواف رينبو متحركة للخلفية
local RainbowStroke = Instance.new("UIStroke")
RainbowStroke.Parent = MainFrame
RainbowStroke.Thickness = 3

task.spawn(function()
    while true do
        for i = 0, 1, 0.005 do
            RainbowStroke.Color = Color3.fromHSV(i, 1, 1)
            task.wait(0.03)
        end
    end
end)

-- شريط العنوان العلوي (TitleBar)
local TitleBar = Instance.new("Frame")
TitleBar.Parent = MainFrame
TitleBar.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
TitleBar.Size = UDim2.new(1, 0, 0, 40)

local TitleCorner = Instance.new("UICorner")
TitleCorner.CornerRadius = UDim.new(0, 10)
TitleCorner.Parent = TitleBar

local TitleText = Instance.new("TextLabel")
TitleText.Parent = TitleBar
TitleText.BackgroundTransparency = 1
TitleText.Position = UDim2.new(0, 15, 0, 0)
TitleText.Size = UDim2.new(0, 250, 1, 0)
TitleText.Font = Enum.Font.GothamBold
TitleText.Text = "sara+0v0 hack"
TitleText.TextColor3 = Color3.fromRGB(255, 255, 255)
TitleText.TextSize = 16
TitleText.TextXAlignment = Enum.TextXAlignment.Left

-- تأثير تغيير لون الخط (أبيض، أزرق، أحمر)
task.spawn(function()
    while true do
        TitleText.TextColor3 = Color3.fromRGB(255, 255, 255)
        task.wait(1.5)
        TitleText.TextColor3 = Color3.fromRGB(0, 150, 255)
        task.wait(1.5)
        TitleText.TextColor3 = Color3.fromRGB(255, 50, 50)
        task.wait(1.5)
    end
end)

-- زر الإغلاق (X)
local CloseBtn = Instance.new("TextButton")
CloseBtn.Parent = TitleBar
CloseBtn.BackgroundColor3 = Color3.fromRGB(200, 40, 40)
CloseBtn.Position = UDim2.new(1, -35, 0.5, -12)
CloseBtn.Size = UDim2.new(0, 24, 0, 24)
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseBtn.TextSize = 14

local CloseCorner = Instance.new("UICorner")
CloseCorner.CornerRadius = UDim.new(0, 6)
CloseCorner.Parent = CloseBtn

CloseBtn.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- زر تصغير/إخفاء القائمة (Minimize)
local MinBtn = Instance.new("TextButton")
MinBtn.Parent = TitleBar
MinBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
MinBtn.Position = UDim2.new(1, -70, 0.5, -12)
MinBtn.Size = UDim2.new(0, 24, 0, 24)
MinBtn.Font = Enum.Font.GothamBold
MinBtn.Text = "-"
MinBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
MinBtn.TextSize = 14

local MinCorner = Instance.new("UICorner")
MinCorner.CornerRadius = UDim.new(0, 6)
MinCorner.Parent = MinBtn

local minimized = false
MinBtn.MouseButton1Click:Connect(function()
    minimized = not minimized
    for _, child in pairs(MainFrame:GetChildren()) do
        if child ~= TitleBar and child ~= UICorner and child ~= RainbowStroke then
            child.Visible = not minimized
        end
    end
    if minimized then
        MainMainSize = MainFrame.Size
        MainFrame.Size = UDim2.new(0, 450, 0, 40)
    else
        MainFrame.Size = UDim2.new(0, 450, 0, 350)
    end
end)

-- حاوية الأقسام (Tab System)
local TabButtons = Instance.new("ScrollingFrame")
TabButtons.Parent = MainFrame
TabButtons.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
TabButtons.Position = UDim2.new(0, 10, 0, 50)
TabButtons.Size = UDim2.new(0, 110, 0, 290)
TabButtons.CanvasSize = UDim2.new(0, 0, 0, 250)
TabButtons.ScrollBarThickness = 3

local UIListLayoutTabs = Instance.new("UIListLayout")
UIListLayoutTabs.Parent = TabButtons
UIListLayoutTabs.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayoutTabs.Padding = UDim.new(0, 5)

local ContainerHolder = Instance.new("Folder")
ContainerHolder.Parent = MainFrame

-- دالة لإنشاء الأقسام
local function CreateTab(name)
    local TabContent = Instance.new("ScrollingFrame")
    TabContent.Name = name .. "Content"
    TabContent.Parent = ContainerHolder
    TabContent.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
    TabContent.BackgroundTransparency = 1
    TabContent.Position = UDim2.new(0, 130, 0, 50)
    TabContent.Size = UDim2.new(0, 310, 0, 290)
    TabContent.CanvasSize = UDim2.new(0, 0, 0, 600)
    TabContent.ScrollBarThickness = 4
    TabContent.Visible = false

    local Layout = Instance.new("UIListLayout")
    Layout.Parent = TabContent
    Layout.SortOrder = Enum.SortOrder.LayoutOrder
    Layout.Padding = UDim.new(0, 8)

    local Btn = Instance.new("TextButton")
    Btn.Parent = TabButtons
    Btn.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
    Btn.Size = UDim2.new(1, 0, 0, 35)
    Btn.Font = Enum.Font.GothamSemibold
    Btn.Text = name
    Btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    Btn.TextSize = 13

    local BtnCorner = Instance.new("UICorner")
    BtnCorner.CornerRadius = UDim.new(0, 6)
    BtnCorner.Parent = Btn

    Btn.MouseButton1Click:Connect(function()
        for _, c in pairs(ContainerHolder:GetChildren()) do
            c.Visible = false
        end
        TabContent.Visible = true
    end)

    return TabContent
end

-- إنشاء الخانات المطلوبة بشكل منفصل تماماً
local ESPTab = CreateTab("ESP")
local AimbotTab = CreateTab("Aimbot")
local HitboxTab = CreateTab("Hitbox")
local ReloadTab = CreateTab("Skip Reload")
local BulletTrackTab = CreateTab("Bullet Track")

-- جعل أول خانة ظاهرة تلقائياً
ESPTab.Visible = true

-- دوال مساعدة لإنشاء الأزرار والخيارات داخل الخانات
local function AddToggle(parent, text, callback)
    local Toggle = Instance.new("TextButton")
    Toggle.Parent = parent
    Toggle.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    Toggle.Size = UDim2.new(1, -10, 0, 35)
    Toggle.Font = Enum.Font.Gotham
    Toggle.Text = text .. ": OFF"
    Toggle.TextColor3 = Color3.fromRGB(200, 200, 200)
    Toggle.TextSize = 12
    Toggle.TextXAlignment = Enum.TextXAlignment.Left

    local Padding = Instance.new("UIPadding")
    Padding.PaddingLeft = UDim.new(0, 10)
    Padding.Parent = Toggle

    local Corner = Instance.new("UICorner")
    Corner.CornerRadius = UDim.new(0, 6)
    Corner.Parent = Toggle

    local state = false
    Toggle.MouseButton1Click:Connect(function()
        state = not state
        if state then
            Toggle.Text = text .. ": ON"
            Toggle.TextColor3 = Color3.fromRGB(0, 255, 100)
            Toggle.BackgroundColor3 = Color3.fromRGB(20, 50, 30)
        else
            Toggle.Text = text .. ": OFF"
            Toggle.TextColor3 = Color3.fromRGB(200, 200, 200)
            Toggle.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
        end
        callback(state)
    end)
end

local function AddColorPicker(parent, callback)
    local Colors = {
        {"أبيض", Color3.fromRGB(255, 255, 255)},
        {"احمر", Color3.fromRGB(255, 50, 50)},
        {"ازرق", Color3.fromRGB(50, 150, 255)},
        {"اخضر", Color3.fromRGB(50, 255, 50)},
        {"بنفسجي", Color3.fromRGB(150, 50, 255)},
        {"وردي", Color3.fromRGB(255, 100, 200)},
        {"اسود", Color3.fromRGB(20, 20, 20)},
        {"سمائي", Color3.fromRGB(100, 220, 255)}
    }
    
    for _, col in ipairs(Colors) do
        local Btn = Instance.new("TextButton")
        Btn.Parent = parent
        Btn.BackgroundColor3 = col[2]
        Btn.Size = UDim2.new(1, -10, 0, 28)
        Btn.Font = Enum.Font.GothamBold
        Btn.Text = "لون: " .. col[1]
        Btn.TextColor3 = Color3.fromRGB(0, 0, 0)
        Btn.TextSize = 12
        
        local Corner = Instance.new("UICorner")
        Corner.CornerRadius = UDim.new(0, 6)
        Corner.Parent = Btn
        
        Btn.MouseButton1Click:Connect(function()
            callback(col[2])
        end)
    end
end

-- تعبئة خانة الـ ESP
AddToggle(ESPTab, "ENABLE ESP PLAYER", function(v) getgenv().SaraConfig.ESP_Enabled = v end)
AddToggle(ESPTab, "ESP LINE", function(v) getgenv().SaraConfig.ESP_Line = v end)
AddToggle(ESPTab, "ESB BOX 3D", function(v) getgenv().SaraConfig.ESP_Box3D = v end)
AddToggle(ESPTab, "ESB SKELETON", function(v) getgenv().SaraConfig.ESP_Skeleton = v end)
AddToggle(ESPTab, "ESP ALERT", function(v) getgenv().SaraConfig.ESP_Alert = v end)
AddToggle(ESPTab, "ESP DISTANCE", function(v) getgenv().SaraConfig.ESP_Distance = v end)

local ColorLabel = Instance.new("TextLabel")
ColorLabel.Parent = ESPTab
ColorLabel.Size = UDim2.new(1, -10, 0, 20)
ColorLabel.BackgroundTransparency = 1
ColorLabel.Font = Enum.Font.GothamBold
ColorLabel.Text = "--- اختر لون الـ ESP ---"
ColorLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
ColorLabel.TextSize = 12

AddColorPicker(ESPTab, function(c)
    getgenv().SaraConfig.ESP_Color = c
end)

-- تعبئة خانة الأيمبوت
AddToggle(AimbotTab, "Enable aimbot", function(v) getgenv().SaraConfig.Aimbot_Enabled = v end)
AddToggle(AimbotTab, "Visible Check (بدون كفر)", function(v) getgenv().SaraConfig.Aimbot_VisibleCheck = v end)

-- نظام اختيار وضع الأيمبوت (FOV أو 360)
local ModeBtn = Instance.new("TextButton")
ModeBtn.Parent = AimbotTab
ModeBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
ModeBtn.Size = UDim2.new(1, -10, 0, 35)
ModeBtn.Font = Enum.Font.GothamBold
ModeBtn.Text = "وضع الأيمبوت: دائرة FOV"
ModeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ModeBtn.TextSize = 12
local ModeCorner = Instance.new("UICorner")
ModeCorner.CornerRadius = UDim.new(0, 6)
ModeCorner.Parent = ModeBtn

ModeBtn.MouseButton1Click:Connect(function()
    if getgenv().SaraConfig.Aimbot_Mode == "FOV" then
        getgenv().SaraConfig.Aimbot_Mode = "360"
        ModeBtn.Text = "وضع الأيمبوت: 360 درجة"
    else
        getgenv().SaraConfig.Aimbot_Mode = "FOV"
        ModeBtn.Text = "وضع الأيمبوت: دائرة FOV"
    end
end)

-- دائرة الـ FOV المرئية
local FOVCircle = Drawing.new("Circle")
FOVCircle.Visible = false
FOVCircle.Radius = 150
FOVCircle.Color = Color3.fromRGB(255, 255, 255)
FOVCircle.Thickness = 1
FOVCircle.Filled = false
FOVCircle.Transparency = 0.7

RunService.RenderStepped:Connect(function()
    FOVCircle.Position = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)
    if getgenv().SaraConfig.Aimbot_Enabled and getgenv().SaraConfig.Aimbot_Mode == "FOV" then
        FOVCircle.Visible = true
    else
        FOVCircle.Visible = false
    end
end)

-- تعبئة خانة الـ Hitbox / Magic Bullet
local HitboxText = Instance.new("TextLabel")
HitboxText.Parent = HitboxTab
HitboxText.Size = UDim2.new(1, -10, 0, 30)
HitboxText.BackgroundTransparency = 1
HitboxText.Font = Enum.Font.GothamBold
HitboxText.Text = "تكبير هيدبكس اللاعبين (Magic Bullet / Hitbox)"
HitboxText.TextColor3 = Color3.fromRGB(255, 255, 255)
HitboxText.TextSize = 11

AddToggle(HitboxTab, "تفعيل تكبير الـ Hitbox", function(v)
    task.spawn(function()
        while task.wait(1) do
            if v then
                for _, p in pairs(Players:GetPlayers()) do
                    if p ~= LocalPlayer and p.Character and p.Character:FindFirstChild("Head") then
                        p.Character.Head.Size = Vector3.new(getgenv().SaraConfig.Hitbox_Size, getgenv().SaraConfig.Hitbox_Size, getgenv().SaraConfig.Hitbox_Size)
                        p.Character.Head.Transparency = 0.5
                        p.Character.Head.CanCollide = false
                    end
                end
            end
        end
    end)
end)

-- خانة تخطي الريلود
AddToggle(ReloadTab, "Enable skip reload", function(v)
    getgenv().SaraConfig.SkipReload = v
    task.spawn(function()
        while task.wait(0.1) do
            if getgenv().SaraConfig.SkipReload then
                pcall(function()
                    local char = LocalPlayer.Character
                    if char and char:FindFirstChildOfClass("Tool") then
                        local tool = char:FindFirstChildOfClass("Tool")
                        if tool:FindFirstChild("Reload") then
                            -- تخطي وقت الريلود البرمجي حسب الماب
                            tool.Reload:FireServer()
                        end
                    end
                end)
            end
        end
    end)
end)

-- خانة الـ Bullet Track الأسطورية (إرسال الطلقة للسماء لتنزل على رأس العدو)
AddToggle(BulletTrackTab, "Enable Bullet Track (سماء للرأس)", function(v)
    getgenv().SaraConfig.BulletTrack = v
end)

-- كود تتبع الرصاص الأسطوري
RunService.Stepped:Connect(function()
    if getgenv().SaraConfig.BulletTrack then
        pcall(function()
            for _, v in pairs(workspace:GetChildren()) do
                if v:IsA("Part") and (v.Name == "Bullet" or v.Name == "Projectile" or v.Name == "Ammo") then
                    -- إعادة توجيه موضع الطلقة تلقائياً لأقرب عدو
                    local target = nil
                    local shortestDist = math.huge
                    for _, player in pairs(Players:GetPlayers()) do
                        if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("Head") then
                            local dist = (player.Character.Head.Position - v.Position).Magnitude
                            if dist < shortestDist then
                                shortestDist = dist
                                target = player.Character.Head
                            end
                        end
                    end
                    if target then
                        v.Position = target.Position + Vector3.new(0, 0.5, 0)
                    end
                end
            end
        end)
    end
end)

-- نظام تشغيل الـ Aimbot الفتاك (رأس العدو تلقائياً)
RunService.RenderStepped:Connect(function()
    if getgenv().SaraConfig.Aimbot_Enabled then
        pcall(function()
            local closestTarget = nil
            local shortestDist = getgenv().SaraConfig.Aimbot_Mode == "FOV" and getgenv().SaraConfig.Aimbot_FOV or math.huge
            
            for _, player in pairs(Players:GetPlayers()) do
                if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("Head") then
                    local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
                    if humanoid and humanoid.Health > 0 then
                        local head = player.Character.Head
                        
                        -- فحص الكفر (Visible Check) إذا كان مفعلاً
                        local isVisible = true
                        if getgenv().SaraConfig.Aimbot_VisibleCheck then
                            local origin = Camera.CFrame.Position
                            local rayParams = RaycastParams.new()
                            rayParams.FilterDescendantsInstances = {LocalPlayer.Character, player.Character}
                            rayParams.FilterType = RaycastType.Exclude
                            local result = workspace:Raycast(origin, head.Position - origin, rayParams)
                            if result then
                                isVisible = false -- يوجد كفر بينك وبينه
                            end
                        end
                        
                        if isVisible then
                            local screenPoint, onScreen = Camera:WorldToScreenPoint(head.Position)
                            if onScreen then
                                local mouseDist = (Vector2.new(screenPoint.X, screenPoint.Y) - Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)).Magnitude
                                if mouseDist < shortestDist then
                                    shortestDist = mouseDist
                                    closestTarget = head
                                end
                            end
                        end
                    end
                end
            end
            
            if closestTarget then
                Camera.CFrame = CFrame.new(Camera.CFrame.Position, closestTarget.Position)
            end
        end)
    end
end)

print("sara+0v0 hack loaded successfully!")
