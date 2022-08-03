getgenv().esp = false
getgenv().Farm = false
getgenv().enabled = false --Toggle on/off
getgenv().uselocalplayer = false --Choose whether the ESP highlights LocalPlayer or not
getgenv().filluseteamcolor = false --Toggle fill color using player team color on/off
getgenv().outlineuseteamcolor = false --Toggle outline color using player team color on/off
getgenv().fillcolor = Color3.fromRGB(55, 55, 55) --Change fill color, no need to edit if using team color
getgenv().outlinecolor = Color3.fromRGB(255, 255, 255) --Change outline color, no need to edit if using team color
getgenv().filltrans = 0 --Change fill transparency
getgenv().outlinetrans = 0 --Change outline transparency
getgenv().AimPart = "HumanoidRootPart" -- For R15 Games: {UpperTorso, LowerTorso, HumanoidRootPart, Head} | For R6 Games: {Head, Torso, HumanoidRootPart}
getgenv().AimlockToggleKey = "Y" -- Toggles Aimbot On/Off 
getgenv().AimRadius = 50 -- How far away from someones character you want to lock on at
getgenv().ThirdPerson = false -- Locking onto someone in your Third Person POV
getgenv().FirstPerson = true -- Locking onto someone in your First Person POV
getgenv().TeamCheck = false -- Check if Target is on your Team (True means it wont lock onto your teamates, false is vice versa) (Set it to false if there are no teams)
getgenv().PredictMovement = true -- Predicts if they are moving in fast velocity (like jumping) so the aimbot will go a bit faster to match their speed 
getgenv().PredictionVelocity = 10 -- The speed of the PredictMovement feature 

local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()

local playertable = {}
for i,v in pairs(game:GetService("Players"):GetDescendants()) do
   if v:IsA("Player") and v.Name ~= game:GetService("Players").LocalPlayer.Name then
       playertable[#playertable+1] = v.Name
   end
end
local plr = game.Players.LocalPlayer.Character.HumanoidRootPart

local UI = Material.Load({
     Title = "By Stormzzy#0880 : item asylum",
     Style = 1,
     SizeX = 400,
     SizeY = 350,
     Theme = "Dark"
})

local Page = UI.New({
    Title = "Farm"
})

local Page2 = UI.New({
    Title = "Esp"
})

local Page3 = UI.New({
    Title = "AimBot"
})

local Page4 = UI.New({
    Title = "Local Player"
})

Page.Dropdown({
    Text = "Farm Player",
    Callback = function(value)
        _G.player = value
    end,
    Options = {unpack(playertable)}
})

Page.Toggle({
    Text = "Auto Farm Player",
    Callback = function(value)
        getgenv().Farm = value
            spawn(function()
            while Farm == true do
                wait()
        plr.CFrame = game.Players[_G.player].Character.HumanoidRootPart.CFrame
            end
            end)
    end,
    Enabled = false
})

Page.Button({
    Text = "Click Me If You Die With While Farming",
    Callback = function()
        loadstring(game:HttpGet(('https://raw.githubusercontent.com/iiprixe/235325125-GENATOR/main/item-asylum'),true))()    
    end
})

Page2.Toggle({
    Text = "Auto Update",
    Callback = function(value)
    getgenv().esp = value
    spawn(function()
        while esp == true do
     loadstring(game:HttpGet("https://raw.githubusercontent.com/zntly/highlight-esp/main/esp.lua"))()       
    end
    end)
    end,
    Enabled = false
})

Page2.Toggle({
    Text = "Esp",
    Callback = function(value)
    getgenv().enabled = value
    end,
    Enabled = false
})

Page2.Toggle({
    Text = "Fill With Teamcolor",
    Callback = function(value)
    getgenv().filluseteamcolor = value
    end,
    Enabled = false
})

Page2.Toggle({
    Text = "Outline With Teamcolor",
    Callback = function(value)
    getgenv().outlineuseteamcolor = value
    end,
    Enabled = false
})

Page2.ColorPicker({
    Text = "Fill Color",
    Default = Color3.fromRGB(255, 255, 255),
    Callback = function(value)
        getgenv().fillcolor = value
    end
})

Page2.ColorPicker({
    Text = "Outline Color",
    Default = Color3.fromRGB(0, 0, 0),
    Callback = function(value)
        getgenv().outlinecolor = value
    end
})

Page3.Button({
    Text = "Aim Bot (Credit To Ciazware)",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/zxciaz/Universal-Scripts/main/Aimbot", true))()   
    end
})

Page3.Dropdown({
    Text = "Choose an option",
    Callback = function(value)
        getgenv().AimPart = value
    end,
    Options = {"Head", "Torso", "HumanoidRootPart"}
})

Page3.TextField({
    Text = "Aim Lock Toggle Key",
    Callback = function(value)
        getgenv().AimlockToggleKey = value
    end
})

Page3.Slider({
    Text = "Aim Radius",
    Callback = function(value)
        getgenv().AimRadius = value
    end,
    Min = 80,
    Max = 200,
    Def = 80
})

Page3.Toggle({
    Text = "Third Person",
    Callback = function(value)
        getgenv().ThirdPerson = value
    end,
    Enabled = false
})

Page3.Toggle({
    Text = "First Person",
    Callback = function(value)
        getgenv().FirstPerson = value
    end,
    Enabled = false
})

Page3.Toggle({
    Text = "Predict Movement",
    Callback = function(value)
        getgenv().PredictMovement = value
    end,
    Enabled = false
})

Page3.Slider({
    Text = "Prediction Velocity",
    Callback = function(value)
        getgenv().PredictionVelocity = value
    end,
    Min = 10,
    Max = 100,
    Def = 10
})

Page4.Slider({
    Text = "WS/Walk Speed",
    Callback = function(value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
    end,
    Min = 16,
    Max = 100,
    Def = 16
})

Page4.Slider({
    Text = "JP/Jump Power",
    Callback = function(value)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = value
    end,
    Min = 50,
    Max = 100,
    Def = 50
})
