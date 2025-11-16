local UILib = loadstring(game:HttpGet("https://raw.githubusercontent.com/IEnemyFiles/StellarUI-Remake/refs/heads/main/NewUiStellar.lua"))()

if UILib:LoadAnimation() then
	UILib:StartLoad();
end;
if UILib:LoadAnimation() then
	UILib:Loaded();
end;
local UserInputService = game:GetService("UserInputService")
local Window = UILib:Window({
	SubTitle = "x2zu Project",
	Size = game:GetService("UserInputService").TouchEnabled and UDim2.new(0, 380, 0, 260) or UDim2.new(0, 500, 0, 320),
	TabWidth = 140
})

local Info = Window:Tab("Information", "rbxassetid://128891143813807");
local Main = Window:Tab("Main", "rbxassetid://10723407389");
local Farm = Window:Tab("Farming", "rbxassetid://10723415335");
local Shop = Window:Tab("Shop", "rbxassetid://10709782497");
local TPort = Window:Tab("Teleport", "rbxassetid://98216376967992");
local Player = Window:Tab("Player", "rbxassetid://10747373176");
local Utility = Window:Tab("Utility", "rbxassetid://10734984606");
local Settings = Window:Tab("Settings", "rbxassetid://10734950309");

Info:Seperator("Annoucements")
Info = Info:Label("Important")

Main:Seperator("Main");

Time = Main:Label("Executor Time");
function UILibTime()
    local GameTime = math.floor(workspace.DistributedGameTime + 0.5);
    local Hour = math.floor(GameTime / 60 ^ 2) % 24;
    local Minute = math.floor(GameTime / 60 ^ 1) % 60;
    local Second = math.floor(GameTime / 60 ^ 0) % 60;
	Time:Set("[Game Time] : Hours : " .. Hour .. " Min : " .. Minute .. " Sec : " .. Second);
end;
spawn(function()
	while task.wait() do
    	pcall(function()
    		UILibTime();
    	end);
    end;
end);

Client = Main:Label("Client");
function UILibClient()
	local Fps = workspace:GetRealPhysicsFPS();
	Client:Set("[Fps] : " .. Fps);
end;
spawn(function()
	while true do
		wait(0.1);
		UILibClient();
	end;
end);

Client1 = Main:Label("Client");
function UILibClient1()
	local Ping = (game:GetService("Stats")).Network.ServerStatsItem["Data Ping"]:GetValueString();
	Client1:Set("[Ping] : " .. Ping);
end;
spawn(function()
	while true do
		wait(0.1);
		UILibClient1();
	end;
end);

Main:Button("Copy Discord Link", function()
	setclipboard("https://discord.gg/FmMuvkaWvG");
	UILib:Notify("Copied!", 3);
end);
Main:Label("Status : label");

-- Dropdown
Main:Seperator("Dropdown");
Main:Dropdown("Type", {"Option 1", "Option 2", "Option 3"}, nil, function(selected)
    print("Selected number:", selected)
end)


-- Toggle
Main:Seperator("Toggle");
Main:Toggle("Type", {"Option 1", "Option 2", "Option 3"}, "Toggle with desc", function(selected)
    print("Selected number:", selected)
end)
Main:Toggle("Type", {"Option 1", "Option 2", "Option 3"}, nil, function(selected)
    print("Selected number:", selected)
end)

-- Slider
Main:Seperator("Slider");
Main:Slider("Farm Distance", 0, 50, 25, function(value)
    print("Selected Farm Distance:", value)
end)

Main:Line();
local JobLabel = Main:Label("Server Job ID :")

Main:Button("Copy Server Job ID", function()
	setclipboard("https://discord.gg/FmMuvkaWvG");
	UILib:Notify("Copied!", 3);
end)

Main:Textbox("Enter Server Job ID", true, function(value)
    print("Entered Job ID:", value)
end)

Main:Button("Join Server", function()
    print("Teleporting to Job ID...") -- Ganti dengan teleport logic jika diperlukan
end)
