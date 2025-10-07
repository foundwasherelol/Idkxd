local library = {count = 0};

local FindLibrary = game:GetService("CoreGui"):FindFirstChild("UI Library")
if game:GetService("CoreGui"):FindFirstChild("UI Library") then
	game:GetService("CoreGui"):FindFirstChild("UI Library"):Destroy()
end

local UILibrary = Instance.new("ScreenGui")
UILibrary.Name = "UI Library"
UILibrary.Parent = game:GetService("CoreGui")

game:GetService("UserInputService").InputBegan:Connect(function(Input)
	if Input.KeyCode == Enum.KeyCode.RightShift then
		UILibrary.Enabled= not UILibrary.Enabled
	end
end)


function library:CreateWindow(WName)
	library.count = library.count + 1
	local ui = {};
	local Holder = Instance.new("ImageLabel")
	local WindowText = Instance.new("TextLabel")
	local Container = Instance.new("ImageLabel")
	local ToggleGUI = Instance.new("TextButton")
	local UIListLayout = Instance.new("UIListLayout")
	local UIPadding = Instance.new("UIPadding")

	Holder.Name = WName
	Holder.Parent = UILibrary
	Holder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Holder.BackgroundTransparency = 1.000
	Holder.BorderSizePixel = 0
	Holder.Position = UDim2.new(0, (15 + (202 * library.count) - 200), 0.002, 0)
	Holder.Size = UDim2.new(0, 200, 0, 39)
	Holder.ZIndex = 5
	Holder.Image = "rbxassetid://3570695787"
	Holder.ImageColor3 = Color3.fromRGB(26, 26, 26)
	Holder.ScaleType = Enum.ScaleType.Slice
	Holder.SliceCenter = Rect.new(100, 100, 100, 100)
	Holder.SliceScale = 0.040

	ToggleGUI.Name = "ToggleGUI"
	ToggleGUI.Parent = Holder
	ToggleGUI.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ToggleGUI.BackgroundTransparency = 1.000
	ToggleGUI.BorderSizePixel = 0
	ToggleGUI.Position = UDim2.new(0.852380931, 0, 0, 0)
	ToggleGUI.Size = UDim2.new(0, 31, 0, 38)
	ToggleGUI.ZIndex = 6
	ToggleGUI.Font = Enum.Font.GothamBold
	ToggleGUI.Text = "▼"
	ToggleGUI.TextColor3 = Color3.fromRGB(255, 255, 255)
	ToggleGUI.TextSize = 17.000

	Container.Name = "Container"
	Container.Parent = Holder
	Container.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Container.BackgroundTransparency = 1.000
	Container.ClipsDescendants = true
	Container.Size = UDim2.new(0, 200, 0, 37)
	Container.ZIndex = 2
	Container.Image = "rbxassetid://3570695787"
	Container.ImageColor3 = Color3.fromRGB(35, 35, 35)
	Container.ScaleType = Enum.ScaleType.Slice
	Container.SliceCenter = Rect.new(100, 100, 100, 100)
	Container.SliceScale = 0.040

	WindowText.Name = WName
	WindowText.Parent = Holder
	WindowText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	WindowText.BackgroundTransparency = 1.000
	WindowText.BorderSizePixel = 0
	WindowText.Position = UDim2.new(0.0399999991, 0, 0.15384616, 0)
	WindowText.Size = UDim2.new(0, 186, 0, 27)
	WindowText.ZIndex = 5
	WindowText.Font = Enum.Font.SourceSans
	WindowText.Text = WName
	WindowText.TextColor3 = Color3.fromRGB(255, 255, 255)
	WindowText.TextSize = 22.000
	WindowText.TextXAlignment = Enum.TextXAlignment.Left

	UIListLayout.Parent = Container
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIListLayout.Padding = UDim.new(0, 1)

	UIPadding.Parent = Container
	UIPadding.PaddingTop = UDim.new(0, 40)

	local NewWindow = Holder;

	--//DRAGGABLE FUNCTION ADDED\\--
	local players = game:service('Players');
    local player = players.LocalPlayer;
    local mouse = player:GetMouse();
    local run = game:service('RunService');
    local stepped = run.Stepped;
	draggable = function(obj)
        spawn(function()
            obj.Active = true;
            local minitial;
            local initial;
            local isdragging;
            obj.InputBegan:Connect(function(input)
                if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                    isdragging = true;
                    minitial = input.Position;
                    initial = obj.Position;
                    local con;
                    con = stepped:Connect(function()
                        if isdragging then
                            local delta = Vector3.new(mouse.X, mouse.Y, 0) - minitial;
                            obj.Position = UDim2.new(initial.X.Scale, initial.X.Offset + delta.X, initial.Y.Scale, initial.Y.Offset + delta.Y);
                        else
                            con:Disconnect();
                        end;
                    end);
                    input.Changed:Connect(function()
                        if input.UserInputState == Enum.UserInputState.End then
                            isdragging = false;
                        end;
                    end);
                end;
            end);
        end)
	end;

	draggable(Holder)
	--//END DRAGGABLE FUNCTION\\--

	local TweenService = game:GetService("TweenService");
	local function Rotation(Object,RotateAMT,Delay)
	local ToTween = Object
	local tweenInfo = TweenInfo.new(Delay,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut,0,false,0)
	local Tweener = TweenService:Create(ToTween,tweenInfo,{Rotation = RotateAMT})
		Tweener:Play()
	end

	local Enabled = false;

	NewWindow:FindFirstChild("ToggleGUI").MouseButton1Click:Connect(function()
		Enabled = not Enabled
		if Enabled then
        	Rotation(NewWindow:FindFirstChild("ToggleGUI"),90,.2)
        else
        	Rotation(NewWindow:FindFirstChild("ToggleGUI"),0,.2)
        end
        wait()
		local y = 37
        for i, v in pairs(Container:GetChildren()) do
            if (not v:IsA("UIPadding") and not v:IsA("UIListLayout")) then
                y = y + (v.AbsoluteSize.Y) + 2
            end
        end

        local targetSize = Enabled and UDim2.new(0, 200, 0, 37) or UDim2.new(0, 200, 0, y+2);
        local targetDirection = Enabled and "Out" or "In"

        Container:TweenSize(targetSize, targetDirection, "Linear", 0.15, true)
	end)

	-- REST OF YOUR BUTTON, SLIDER, BOX, TOGGLE FUNCTIONS HERE...
	-- (unchanged from your original code)

	pcall(function()
		game:GetService("StarterGui"):SetCore("SendNotification", {
        	Title = "YoungStars Lib V1",
        	Text = "Made by YoungStar#0001",
        	Duration = 5
   	 	})
	end)
	return ui
end

return library
