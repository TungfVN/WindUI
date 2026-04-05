--[[
    ╔══════════════════════════════════════════════════════╗
    ║         WindUI — BẢN TEMPLATE TỔNG HỢP ĐẦY ĐỦ       ║
    ║  Bao gồm tất cả element và tính năng của WindUI      ║
    ╚══════════════════════════════════════════════════════╝
]]

-- ══════════════════════════════════════════════
-- 1. LOAD WINDUI
-- ══════════════════════════════════════════════

local WindUI = (loadstring(game:HttpGet("https://raw.githubusercontent.com/Footagesus/WindUI/main/source.lua")))()

-- ══════════════════════════════════════════════
-- 2. LOCALIZATION (tuỳ chọn — đặt trước CreateWindow)
-- ══════════════════════════════════════════════

local Localization = WindUI:Localization({
    Enabled = true,
    Prefix   = "loc:",          -- prefix nhận diện key dịch
    DefaultLanguage = "en",
    Translations = {
        en = {
            greeting = "Hello",
            farewell = "Goodbye",
        },
        vi = {
            greeting = "Xin chào",
            farewell = "Tạm biệt",
        },
    },
})

-- ══════════════════════════════════════════════
-- 3. THÊM THEME TUỲ CHỈNH (tuỳ chọn)
-- ══════════════════════════════════════════════

WindUI:AddTheme({
    Name        = "MyTheme",
    Accent      = "#FF5733",
    Dialog      = "#1a1a2e",
    Outline     = "#FF5733",
    Text        = "#FFFFFF",
    Placeholder = "#ffb3a7",
    Background  = "#16213e",
    Button      = "#FF5733",
    Icon        = "#ffffff",
})

-- ══════════════════════════════════════════════
-- 4. TẠO WINDOW
-- ══════════════════════════════════════════════

local Window = WindUI:CreateWindow({
    -- ── Thông tin cơ bản ──────────────────────
    Title       = "WindUI Template",
    Author      = "Template Author",
    Icon        = "rbxassetid://90888007617642",   -- Icon toptbar + open button
    IconThemed  = false,                            -- true = icon nhuốm màu theo theme

    -- ── Kích thước & vị trí ───────────────────
    Size        = UDim2.fromOffset(600, 480),       -- giới hạn: 480-700 x 350-520
    SideBarWidth = 160,                             -- chiều rộng thanh tab bên trái

    -- ── Theme & giao diện ─────────────────────
    --  Các theme có sẵn:
    --  "Dark" | "Cosmic Blue" | "Violet" | "Indigo"
    --  "Ethereal Violet" | "Blush Amethyst" | "Lagoon Sapphire"
    --  "Golden Nebula"   | "Coral Twilight" | "Mint Galaxy" | "Royal Abyss"
    Theme       = "Dark",
    Transparent = false,                            -- bật nền trong suốt

    -- ── Background ────────────────────────────
    Background  = "rbxassetid://0",                -- rbxassetid / URL ảnh / URL video (video:https://...)
    BackgroundImageTransparency = 0,

    -- Gradient background (thay cho Background nếu muốn):
    -- Background = WindUI:Gradient({
    --     [0]   = { Color = Color3.fromHex("#002FFF"), Transparency = 0 },
    --     [50]  = { Color = Color3.fromHex("#9D00FF"), Transparency = 0 },
    --     [100] = { Color = Color3.fromHex("#000000"), Transparency = 0 },
    -- }, { Rotation = 45 }),

    -- ── Tuỳ chọn UI ──────────────────────────
    HideSearchBar   = false,         -- true = ẩn thanh tìm kiếm dưới sidebar
    ScrollBarEnabled = false,        -- true = hiện thanh cuộn sidebar
    Resizable       = true,          -- cho phép kéo co giãn cửa sổ
    ToggleKey       = Enum.KeyCode.RightControl,   -- phím tắt ẩn/hiện

    -- ── Open button ──────────────────────────
    EarlyOpened = false,             -- true = mở ngay, không hiện cửa sổ lúc đầu

    -- ── User panel (hiện thông tin người chơi) ─
    User = {
        Enabled   = true,
        Anonymous = false,           -- true = ẩn tên, hiện "Anonymous"
        Callback  = function()
            print("User panel clicked!")
        end,
    },

    -- ── Key System ───────────────────────────
    -- KeySystem = {
    --     Key     = "mySecretKey123",          -- string hoặc table nhiều key
    --     -- Key  = { "key1", "key2", "key3" },
    --     URL     = "https://linktr.ee/yourkey",  -- nút "Get key"
    --     Note    = "Lấy key tại Discord server", -- chú thích
    --     SaveKey = false,                     -- lưu key để khỏi nhập lại
    --     Thumbnail = {
    --         Image = "rbxassetid://0",
    --         Title = "Your Hub",
    --     },
    -- },
})

-- ══════════════════════════════════════════════
-- 5. CALLBACK CỬA SỔ
-- ══════════════════════════════════════════════

Window:OnClose(function()
    print("Cửa sổ đã đóng (minimize)")
end)

Window:OnDestroy(function()
    print("Cửa sổ đã bị huỷ hoàn toàn")
end)

-- ══════════════════════════════════════════════
-- 6. OPEN BUTTON (nút mở lại khi minimize)
-- ══════════════════════════════════════════════

Window:EditOpenButton({
    Icon          = "rbxassetid://90888007617642",
    CornerRadius  = UDim.new(0, 10),
    Position      = UDim2.new(0, 75, 0, 100),
    OnlyMobile    = false,
    Enabled       = true,
    Draggable     = true,
    -- Color      = ColorSequence.new(Color3.fromHex("#40c9ff"), Color3.fromHex("#e81cff")),
    -- StrokeThickness = 2,
})

-- ══════════════════════════════════════════════
-- 7. TOPBAR BUTTONS TUỲ CHỈNH
-- ══════════════════════════════════════════════

Window:CreateTopbarButton(
    "Discord",          -- Title (tooltip)
    "brand-discord",    -- Icon (lucide icon name)
    function()
        setclipboard("https://discord.gg/example")
        WindUI:Notify({ Title = "Copied!", Content = "Discord link copied.", Icon = "check", Duration = 3 })
    end,
    996,                -- LayoutOrder (số nhỏ hơn = gần nút Close hơn; 997=Minimize, 998=Fullscreen, 999=Close)
    false               -- IconThemed
)

-- Ẩn nút mặc định (tuỳ chọn):
-- Window:DisableTopbarButtons({ "Fullscreen", "Minimize", "Close" })

-- ══════════════════════════════════════════════
-- 8. TAG (nhãn trên topbar)
-- ══════════════════════════════════════════════

Window:Tag({
    Title = "v1.0.0",
    Color = Color3.fromHex("#43a047"),
})

Window:Tag({
    Title = "BETA",
    Color = Color3.fromHex("#f57c00"),
})

-- ══════════════════════════════════════════════
-- 9. TẠO CÁC TAB
-- ══════════════════════════════════════════════

local Tabs = {
    MainTab = Window:Tab({
        Title        = "Main",
        Icon         = "home",               -- Lucide icon name hoặc rbxassetid://...
        ShowTabTitle = false,                -- true = hiện tên tab to ở đầu nội dung
        IconThemed   = false,
        -- Locked    = true,                -- khoá tab (mờ, không click được)
        -- Desc      = "Tooltip mô tả tab", -- tooltip khi hover
    }),
    ElementsTab = Window:Tab({
        Title = "Elements",
        Icon  = "layout-panel-top",
        ShowTabTitle = true,
    }),
    AdvancedTab = Window:Tab({
        Title = "Advanced",
        Icon  = "settings-2",
        ShowTabTitle = false,
    }),
    InfoTab = Window:Tab({
        Title = "Info",
        Icon  = "info",
        ShowTabTitle = false,
    }),
}

-- Chọn tab hiển thị mặc định:
Window:SelectTab(1)

-- ══════════════════════════════════════════════
-- 10. MAIN TAB — CÁC ELEMENT CƠ BẢN
-- ══════════════════════════════════════════════

-- ── Section ──────────────────────────────────

Tabs.MainTab:Section({
    Title          = "Auto Farm",
    Icon           = "sprout",               -- lucide icon (tuỳ chọn)
    TextXAlignment = "Left",                 -- "Left" | "Center" | "Right"
    TextSize       = 19,
})

-- ── Toggle ───────────────────────────────────

local AutoFarmToggle = Tabs.MainTab:Toggle({
    Title    = "Auto Farm",
    Desc     = "Tự động farm cho tới khi tắt.",
    Default  = false,
    Icon     = "wheat",                      -- lucide icon (tuỳ chọn)
    -- Type  = "Toggle",                    -- "Toggle" (mặc định) hoặc "Checkbox"
    Callback = function(state)
        print("Auto Farm:", state)
        _G.AutoFarm = state
    end,
})

-- Dùng code để set:
-- AutoFarmToggle:Set(true)
-- AutoFarmToggle:Lock()
-- AutoFarmToggle:Unlock()

local CheckboxToggle = Tabs.MainTab:Toggle({
    Title    = "Checkbox Mode",
    Desc     = "Ví dụ toggle kiểu checkbox.",
    Default  = true,
    Type     = "Checkbox",
    Callback = function(state)
        print("Checkbox:", state)
    end,
})

-- ── Button ────────────────────────────────────

local CollectButton = Tabs.MainTab:Button({
    Title    = "Collect All Fruits",
    Desc     = "Thu thập tất cả trái cây trong vườn.",
    Icon     = "cherry",
    Callback = function()
        print("Collecting fruits...")
    end,
})

-- CollectButton:Lock()   -- khoá nút
-- CollectButton:Unlock()

Tabs.MainTab:Divider()

-- ── Slider ────────────────────────────────────

Tabs.MainTab:Section({ Title = "Teleport & Speed" })

local WalkSpeedSlider = Tabs.MainTab:Slider({
    Title    = "Walk Speed",
    Desc     = "Tốc độ di chuyển của nhân vật.",
    Value    = {
        Min     = 16,
        Max     = 300,
        Default = 16,
    },
    Step     = 1,       -- bước nhảy (dùng số thập phân như 0.1 để có decimal)
    Callback = function(value)
        print("Speed:", value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = tonumber(value)
    end,
})

-- WalkSpeedSlider:Set(50)

local JumpPowerSlider = Tabs.MainTab:Slider({
    Title    = "Jump Power",
    Value    = { Min = 50, Max = 500, Default = 50 },
    Step     = 5,
    Callback = function(value)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = tonumber(value)
    end,
})

Tabs.MainTab:Divider()

-- ── Dropdown — Single ─────────────────────────

Tabs.MainTab:Section({ Title = "Sell & Buy" })

local SeedDropdown = Tabs.MainTab:Dropdown({
    Title    = "Select Seed",
    Desc     = "Chọn loại hạt để mua.",
    Values   = { "Strawberry", "Blueberry", "Tomato", "Carrot", "Pumpkin" },
    Value    = nil,              -- giá trị mặc định (nil = không chọn)
    Multi    = false,
    AllowNone = true,            -- cho phép bỏ chọn hết
    -- MenuWidth = 170,
    Callback = function(option)
        _G.SelectedSeed = option
        print("Selected:", option)
    end,
})

-- SeedDropdown:Select("Carrot")
-- SeedDropdown:Refresh({ "Apple", "Grape" })

-- ── Dropdown — Multi ──────────────────────────

local MutationDropdown = Tabs.MainTab:Dropdown({
    Title     = "Select Mutations",
    Desc      = "Chọn nhiều mutation cùng lúc.",
    Values    = { "Golden", "Rainbow", "Shiny", "Wet", "Moonlit" },
    Value     = {},
    Multi     = true,
    AllowNone = true,
    -- Exclusive = { "Golden" },   -- các option này chỉ được chọn một mình
    Callback  = function(options)
        _G.SelectedMutations = options
        print("Mutations:", options)
    end,
})

-- ══════════════════════════════════════════════
-- 11. ELEMENTS TAB — CÁC ELEMENT NÂNG CAO
-- ══════════════════════════════════════════════

-- ── Input ─────────────────────────────────────

Tabs.ElementsTab:Section({ Title = "Input Fields" })

local NameInput = Tabs.ElementsTab:Input({
    Title       = "Player Name",
    Desc        = "Nhập tên người chơi cần tìm.",
    Placeholder = "Enter player name...",
    Value       = "",                    -- giá trị mặc định
    Type        = "Input",               -- "Input" (1 dòng) | "TextArea" (nhiều dòng)
    AllowedType = "All",                 -- "All" | "Number" | "Text" | "Decimal" | "Time"
    InputIcon   = "user",                -- icon bên trái (tuỳ chọn)
    ClearTextOnFocus = false,
    Callback    = function(value)
        _G.TargetPlayer = value
        print("Player name:", value)
    end,
})

-- NameInput:Set("NewValue")
-- NameInput:SetPlaceholder("Type here...")

local NumberInput = Tabs.ElementsTab:Input({
    Title       = "Quantity",
    Placeholder = "Enter a number...",
    AllowedType = "Number",
    Type        = "Input",
    Callback    = function(value)
        _G.Quantity = tonumber(value) or 1
    end,
})

local TextAreaInput = Tabs.ElementsTab:Input({
    Title       = "Notes",
    Placeholder = "Write your notes here...",
    Type        = "TextArea",            -- ô nhập nhiều dòng
    AllowedType = "All",
    Callback    = function(value)
        print("Notes:", value)
    end,
})

Tabs.ElementsTab:Divider()

-- ── Keybind ───────────────────────────────────

Tabs.ElementsTab:Section({ Title = "Keybinds" })

local TeleportKeybind = Tabs.ElementsTab:Keybind({
    Title     = "Teleport Key",
    Desc      = "Nhấn phím để teleport.",
    Value     = "F",                     -- phím mặc định
    CanChange = true,                    -- cho phép người dùng đổi phím
    Callback  = function(key)
        print("Teleport triggered! Key:", key)
    end,
})

-- TeleportKeybind:Set("T")

Tabs.ElementsTab:Divider()

-- ── Colorpicker ───────────────────────────────

Tabs.ElementsTab:Section({ Title = "Color Pickers" })

local EspColorpicker = Tabs.ElementsTab:Colorpicker({
    Title    = "ESP Color",
    Desc     = "Màu của ESP highlight.",
    Default  = Color3.fromHex("#FF0000"),
    Callback = function(color)
        print("Color changed:", color)
        _G.EspColor = color
    end,
})

-- EspColorpicker.Default → Color3 hiện tại
-- Update bằng code: không có :Set() công khai, nhưng có .Default

local EspColorWithAlpha = Tabs.ElementsTab:Colorpicker({
    Title        = "Fill Color + Transparency",
    Desc         = "Màu + độ trong suốt.",
    Default      = Color3.fromHex("#0055FF"),
    Transparency = 0.5,                  -- thêm alpha slider (0 = đục, 1 = trong)
    Callback     = function(color, transparency)
        print("Color:", color, "Alpha:", transparency)
    end,
})

Tabs.ElementsTab:Divider()

-- ── Code Block ────────────────────────────────

Tabs.ElementsTab:Section({ Title = "Code Display" })

Tabs.ElementsTab:Code({
    Title = "Example Script",
    Code  = [[
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
print("Hello from WindUI!")
]],
    -- Copy callback (chạy khi người dùng nhấn nút copy):
    -- Mặc định sẽ copy vào clipboard và notify nếu WindUI được truyền vào
})

Tabs.ElementsTab:Divider()

-- ── Paragraph ─────────────────────────────────

Tabs.ElementsTab:Section({ Title = "Paragraphs" })

local InfoParagraph = Tabs.ElementsTab:Paragraph({
    Title = "About This Hub",
    Desc  = "Đây là template đầy đủ của WindUI bao gồm tất cả các element và tính năng có sẵn.",
    -- Image       = "rbxassetid://0",    -- ảnh nhỏ bên trái (icon)
    -- ImageSize   = 30,
    -- Thumbnail   = "rbxassetid://0",    -- ảnh lớn phía trên
    -- ThumbnailSize = 80,
    -- Color       = "Blue",             -- "Blue"|"Green"|"Red"|"Orange"|"White"|"Grey"
    -- Buttons = {                        -- nút bên dưới paragraph
    --     { Title = "Join Discord", Icon = "brand-discord", Callback = function() end },
    --     { Title = "Copy Link",    Icon = "link",          Callback = function() end },
    -- },
})

-- InfoParagraph:SetTitle("New Title")
-- InfoParagraph:SetDesc("New description text.")

-- ══════════════════════════════════════════════
-- 12. ADVANCED TAB — COLLAPSIBLE & METHODS
-- ══════════════════════════════════════════════

Tabs.AdvancedTab:Section({ Title = "Collapsible Groups" })

-- ── Collapsible ───────────────────────────────
-- Nhóm các element lại, có thể thu gọn / mở rộng

local FarmGroup = Tabs.AdvancedTab:Collapsible({
    Title = "Farm Settings",
    Icon  = "layers",
})

-- Thêm element vào bên trong Collapsible:
FarmGroup:Toggle({
    Title    = "Auto Harvest",
    Default  = false,
    Callback = function(state)
        _G.AutoHarvest = state
    end,
})

FarmGroup:Slider({
    Title    = "Harvest Delay (s)",
    Value    = { Min = 0, Max = 10, Default = 1 },
    Step     = 0.5,
    Callback = function(v) _G.HarvestDelay = tonumber(v) end,
})

FarmGroup:Dropdown({
    Title    = "Farm Plot",
    Values   = { "Plot 1", "Plot 2", "Plot 3" },
    Value    = "Plot 1",
    Callback = function(opt) _G.FarmPlot = opt end,
})

FarmGroup:Button({
    Title    = "Start Now",
    Icon     = "play",
    Callback = function() print("Farm started!") end,
})

FarmGroup:Divider()

FarmGroup:Input({
    Title       = "Custom Plot Name",
    Placeholder = "Enter name...",
    Callback    = function(v) _G.PlotName = v end,
})

FarmGroup:Paragraph({
    Title = "Note",
    Desc  = "Nhóm này có thể thu gọn bằng cách click vào tiêu đề.",
})

Tabs.AdvancedTab:Divider()

-- ── Các method của Tab element ─────────────────

Tabs.AdvancedTab:Section({ Title = "Lock / Unlock Demo" })

local LockedToggle = Tabs.AdvancedTab:Toggle({
    Title    = "This Toggle is Locked",
    Default  = false,
    Locked   = true,              -- khoá ngay từ đầu
    Callback = function(state) end,
})

local LockedSlider = Tabs.AdvancedTab:Slider({
    Title    = "Locked Slider",
    Value    = { Min = 0, Max = 100, Default = 50 },
    Locked   = true,
    Callback = function(v) end,
})

Tabs.AdvancedTab:Button({
    Title    = "Unlock All Above",
    Icon     = "lock-open",
    Callback = function()
        LockedToggle:Unlock()
        LockedSlider:Unlock()
    end,
})

Tabs.AdvancedTab:Button({
    Title    = "Lock All Again",
    Icon     = "lock",
    Callback = function()
        LockedToggle:Lock()
        LockedSlider:Lock()
    end,
})

Tabs.AdvancedTab:Divider()

-- ── SetTitle / SetDesc runtime ─────────────────

Tabs.AdvancedTab:Section({ Title = "Dynamic Content" })

local DynamicToggle = Tabs.AdvancedTab:Toggle({
    Title    = "Dynamic Toggle",
    Desc     = "Desc sẽ thay đổi khi bật/tắt.",
    Default  = false,
    Callback = function(state)
        if state then
            DynamicToggle:SetTitle("Dynamic Toggle [ON]")
            DynamicToggle:SetDesc("Đang chạy... nhấn để tắt.")
        else
            DynamicToggle:SetTitle("Dynamic Toggle")
            DynamicToggle:SetDesc("Desc sẽ thay đổi khi bật/tắt.")
        end
    end,
})

-- ══════════════════════════════════════════════
-- 13. INFO TAB — NOTIFICATIONS, DIALOG, POPUP
-- ══════════════════════════════════════════════

Tabs.InfoTab:Section({ Title = "Notifications" })

Tabs.InfoTab:Button({
    Title    = "Notify — Basic",
    Desc     = "Hiện thông báo đơn giản.",
    Icon     = "bell",
    Callback = function()
        WindUI:Notify({
            Title    = "Thông báo",
            Content  = "Đây là thông báo cơ bản.",
            Icon     = "info",
            Duration = 5,
        })
    end,
})

Tabs.InfoTab:Button({
    Title    = "Notify — Countdown",
    Icon     = "timer",
    Callback = function()
        WindUI:Notify({
            Title     = "Auto Close",
            Content   = "Thông báo tự đóng sau 8 giây.",
            Icon      = "clock",
            Duration  = 8,
            Countdown = true,             -- hiện đếm ngược trong content
        })
    end,
})

Tabs.InfoTab:Button({
    Title    = "Notify — Custom Background",
    Icon     = "image",
    Callback = function()
        WindUI:Notify({
            Title      = "Custom BG",
            Content    = "Thông báo với background gradient.",
            Icon       = "star",
            Duration   = 5,
            -- Background = "rbxassetid://0",       -- ảnh nền
            -- BackgroundImageTransparency = 0,
        })
    end,
})

Tabs.InfoTab:Divider()

Tabs.InfoTab:Section({ Title = "Dialogs" })

Tabs.InfoTab:Button({
    Title    = "Dialog — Confirm",
    Icon     = "message-square-warning",
    Callback = function()
        Window:Dialog({
            Title   = "Xác nhận thao tác",
            Content = "Bạn có chắc muốn thực hiện thao tác này không?",
            Icon    = "alert-triangle",
            Buttons = {
                {
                    Title    = "Huỷ",
                    Icon     = "x",
                    Variant  = "Secondary",   -- "Primary" | "Secondary" | "Tertiary" | "White"
                    Callback = function()
                        print("Đã huỷ")
                    end,
                },
                {
                    Title    = "Xác nhận",
                    Icon     = "check",
                    Variant  = "Primary",
                    Callback = function()
                        print("Đã xác nhận")
                    end,
                },
            },
        })
    end,
})

Tabs.InfoTab:Button({
    Title    = "Dialog — With Image",
    Icon     = "image",
    Callback = function()
        Window:Dialog({
            Title   = "Item Preview",
            Content = "Mô tả chi tiết về item này.",
            Icon    = "package",
            Thumbnail = {
                Image = "rbxassetid://0",
                Title = "Item Name",
            },
            Buttons = {
                { Title = "OK", Variant = "Primary", Callback = function() end },
            },
        })
    end,
})

Tabs.InfoTab:Divider()

Tabs.InfoTab:Section({ Title = "Popups" })

Tabs.InfoTab:Button({
    Title    = "Popup Window",
    Icon     = "external-link",
    Callback = function()
        WindUI:Popup({
            Title   = "Popup Example",
            Content = "Đây là popup riêng biệt, không phụ thuộc cửa sổ chính.",
            Icon    = "info",
            Thumbnail = {
                Image = "rbxassetid://0",
                Title = "Preview",
            },
            Buttons = {
                { Title = "Close",  Icon = "x",     Variant = "Secondary", Callback = function() end },
                { Title = "Accept", Icon = "check", Variant = "Primary",   Callback = function() end },
            },
        })
    end,
})

-- ══════════════════════════════════════════════
-- 14. WINDOW METHODS ĐA DẠNG
-- ══════════════════════════════════════════════

-- Đổi theme lúc runtime:
-- Window chỉ dùng WindUI:SetTheme(), không gọi qua Window
-- WindUI:SetTheme("Cosmic Blue")

-- Đổi phím toggle:
-- Window:SetToggleKey(Enum.KeyCode.Insert)

-- Đổi UIScale (thu nhỏ/phóng to toàn bộ UI):
-- Window:SetUIScale(0.9)

-- Bật/tắt chế độ fullscreen:
-- Window:ToggleFullscreen()

-- Khoá/mở khoá resize:
-- Window:IsResizable(false)

-- Mở / đóng cửa sổ bằng code:
-- Window:Open()
-- Window:Close()           → trả về object có :Destroy()
-- Window:Close():Destroy() → xoá hoàn toàn

-- Section ngoài Tab (trong sidebar):
-- local SidebarSection = Window:Section({ Title = "Sidebar Section" })

-- Divider trong sidebar:
-- Window:Divider()

-- ══════════════════════════════════════════════
-- 15. WINDUI-LEVEL METHODS
-- ══════════════════════════════════════════════

-- Đặt font chữ:
-- WindUI:SetFont("rbxassetid://12187365364")

-- Đặt ngôn ngữ:
-- WindUI:SetLanguage("vi")

-- Lấy theme hiện tại:
-- print(WindUI:GetCurrentTheme())   --> "Dark"

-- Lấy tất cả theme:
-- local themes = WindUI:GetThemes()

-- Notify từ mức WindUI (không cần Window):
-- WindUI:Notify({ Title = "Hi", Content = "Hello!", Duration = 3 })

-- ══════════════════════════════════════════════
-- 16. SPAWN LOOP VÍ DỤ
-- ══════════════════════════════════════════════

spawn(function()
    while wait(1) do
        pcall(function()
            if _G.AutoFarm then
                -- logic auto farm...
            end
        end)
    end
end)

-- ══════════════════════════════════════════════
-- 17. QUICK REFERENCE — TẤT CẢ ELEMENT
-- ══════════════════════════════════════════════
--[[
    ── Window ──────────────────────────────────────────
    Window:Tab({ Title, Icon, ShowTabTitle, IconThemed, Locked, Desc })
    Window:Section({ Title, Icon, TextXAlignment, TextSize })
    Window:Divider()
    Window:Tag({ Title, Color })
    Window:Dialog({ Title, Content, Icon, IconThemed, Thumbnail, Buttons, Width })
    Window:CreateTopbarButton(title, icon, callback, order, iconThemed)
    Window:DisableTopbarButtons({ "Close", "Minimize", "Fullscreen" })
    Window:SelectTab(index)
    Window:EditOpenButton({ Icon, CornerRadius, Position, OnlyMobile, Enabled, Draggable, Color, StrokeThickness })
    Window:OnClose(callback)
    Window:OnDestroy(callback)
    Window:SetToggleKey(Enum.KeyCode.X)
    Window:SetUIScale(scale)
    Window:ToggleFullscreen()
    Window:IsResizable(bool)
    Window:Open()
    Window:Close()  → { Destroy() }

    ── Tab ─────────────────────────────────────────────
    Tab:Section({ Title, Icon, TextXAlignment, TextSize })
    Tab:Divider()
    Tab:Paragraph({ Title, Desc, Image, ImageSize, Thumbnail, ThumbnailSize, Color, Buttons })
    Tab:Button({ Title, Desc, Icon, Locked, Callback })
    Tab:Toggle({ Title, Desc, Default, Icon, Type, Locked, Callback })  → Set, Lock, Unlock, SetTitle, SetDesc
    Tab:Slider({ Title, Desc, Value{Min,Max,Default}, Step, Locked, Callback })  → Set, Lock, Unlock
    Tab:Dropdown({ Title, Desc, Values, Value, Multi, AllowNone, Exclusive, MenuWidth, Locked, Callback })  → Select, Refresh, Lock, Unlock
    Tab:Input({ Title, Desc, Placeholder, Value, Type, AllowedType, InputIcon, Locked, Callback })  → Set, SetPlaceholder, Lock, Unlock
    Tab:Keybind({ Title, Desc, Value, CanChange, Locked, Callback })  → Set
    Tab:Colorpicker({ Title, Desc, Default, Transparency, Locked, Callback })
    Tab:Code({ Title, Code })
    Tab:Collapsible({ Title, Icon })  → (chứa tất cả element trên trừ Collapsible lồng nhau)

    ── WindUI-level ────────────────────────────────────
    WindUI:CreateWindow({ ... })
    WindUI:Notify({ Title, Content, Icon, IconThemed, Duration, Countdown, Background, BackgroundImageTransparency, Buttons })
    WindUI:Popup({ Title, Content, Icon, IconThemed, Thumbnail, Buttons })
    WindUI:SetTheme(name)
    WindUI:AddTheme({ Name, Accent, Dialog, Outline, Text, Placeholder, Background, Button, Icon })
    WindUI:GetThemes()
    WindUI:GetCurrentTheme()
    WindUI:Gradient({ [0]={Color,Transparency}, [50]={...}, [100]={...} }, extraProps)
    WindUI:Localization({ Enabled, Prefix, DefaultLanguage, Translations })
    WindUI:SetLanguage("vi")
    WindUI:SetFont("rbxassetid://...")

    ── Built-in Themes ─────────────────────────────────
    "Dark" | "Cosmic Blue" | "Violet" | "Indigo"
    "Ethereal Violet" | "Blush Amethyst" | "Lagoon Sapphire"
    "Golden Nebula"   | "Coral Twilight" | "Mint Galaxy" | "Royal Abyss"
]]
