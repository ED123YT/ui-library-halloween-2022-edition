ts = game:GetService("TweenService")
uis = game:GetService("UserInputService")
rs = game:GetService("RunService")
plrs = game:GetService("Players")
plr = plrs.LocalPlayer
mouse = plr:GetMouse()
tween = TweenInfo.new

if game:FindFirstChild("CoregGui"):FindFirstChild("HALLOWEEN2022") then
	game:FindFirstChild("CoregGui"):FindFirstChild("HALLOWEEN2022"):Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game:FindFirstChild("CoreGui")
ScreenGui.Name = "HALLOWEEN2022"

--[[
	
	Slider Default/Set: Used by Zypher/Blood lib huge thanks for they to not obf it.
	Adding of features methode inspired by Zypher which was made from xTheAlex14#7266.
	Update headers and etc huge thanks from blood by the method.
	Who helper me? no one i scripted all these at my own.
	It's waste of time! ok idc it's fun i love make library so let me do it then!!!
	Steal/skidd/etc this script idc, i might used some at my own but at least i gave credit.
	Dragify script is not made by me, I cannot figure the actual name of the dev, but at least i was honest...
	
]]

hl = {}

function dragify(Frame)
	dragToggle = nil
	dragSpeed = .25 -- You can edit this.
	dragInput = nil
	dragStart = nil
	dragPos = nil

	function updateInput(input)
		Delta = input.Position - dragStart
		Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + Delta.X, startPos.Y.Scale, startPos.Y.Offset + Delta.Y)
		game:GetService("TweenService"):Create(Frame, TweenInfo.new(.25), {Position = Position}):Play()
	end

	Frame.InputBegan:Connect(function(input)
		if (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) then
			dragToggle = true
			dragStart = input.Position
			startPos = Frame.Position
			input.Changed:Connect(function()
				if (input.UserInputState == Enum.UserInputState.End) then
					dragToggle = false
				end
			end)
		end
	end)

	Frame.InputChanged:Connect(function(input)
		if (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
			dragInput = input
		end
	end)

	game:GetService("UserInputService").InputChanged:Connect(function(input)
		if (input == dragInput and dragToggle) then
			updateInput(input)
		end
	end)
end

function hl:MakeUI()
	local Main = Instance.new("ImageLabel")
	local MainC = Instance.new("UICorner")
	local Menu = Instance.new("Frame")
	local UCOG = Instance.new("Frame")
	local MenuC = Instance.new("UICorner")
	local UIName = Instance.new("TextLabel")
	local Tabs = Instance.new("ScrollingFrame")
	local TabsListL = Instance.new("UIListLayout")
	local Container = Instance.new("Folder")
	
	dragify(Main)

	Main.Name = "Main"
	Main.Parent = ScreenGui
	Main.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Main.BorderSizePixel = 0
	Main.Position = UDim2.new(0.219438881, 0, 0.102505691, 0)
	Main.Size = UDim2.new(0, 560, 0, 349)
	Main.Image = "http://www.roblox.com/asset/?id=5634829223"

	MainC.CornerRadius = UDim.new(0, 6)
	MainC.Name = "MainC"
	MainC.Parent = Main

	Menu.Name = "Menu"
	Menu.Parent = Main
	Menu.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
	Menu.BackgroundTransparency = 0.650
	Menu.Size = UDim2.new(0, 158, 0, 349)

	UCOG.Name = "UCOG"
	UCOG.Parent = Menu
	UCOG.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
	UCOG.BackgroundTransparency = 0.650
	UCOG.BorderSizePixel = 0
	UCOG.Position = UDim2.new(0.5, 0, 0, 0)
	UCOG.Size = UDim2.new(0.5, 0, 1, 0)

	MenuC.CornerRadius = UDim.new(0.0599999987, 0)
	MenuC.Name = "MenuC"
	MenuC.Parent = Menu

	UIName.Name = "UIName"
	UIName.Parent = Menu
	UIName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	UIName.BackgroundTransparency = 1.000
	UIName.BorderSizePixel = 0
	UIName.Position = UDim2.new(0.0379746817, 0, 0.0171919763, 0)
	UIName.Size = UDim2.new(0, 145, 0, 32)
	UIName.Font = Enum.Font.Creepster
	UIName.Text = "HALLOWEEN - 2022"
	UIName.TextColor3 = Color3.fromRGB(209, 139, 0)
	UIName.TextSize = 24.000
	UIName.TextWrapped = true

	Tabs.Name = "Tabs"
	Tabs.Parent = Menu
	Tabs.Active = true
	Tabs.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Tabs.BackgroundTransparency = 1.000
	Tabs.BorderSizePixel = 0
	Tabs.Position = UDim2.new(0, 0, 0.14040114, 0)
	Tabs.Size = UDim2.new(0, 158, 0, 291)
	Tabs.CanvasSize = UDim2.new(0, 0, 0, 0)
	Tabs.ScrollBarThickness = 6

	TabsListL.Name = "TabsListL"
	TabsListL.Parent = Tabs
	TabsListL.HorizontalAlignment = Enum.HorizontalAlignment.Center
	TabsListL.SortOrder = Enum.SortOrder.LayoutOrder
	TabsListL.Padding = UDim.new(0, 8)
	
	local firstCat = true
	local tbss = {}
	function tbss:AddPage(pgname)
		local TabButton = Instance.new("TextButton")
		local TabButtonC = Instance.new("UICorner")
		local Page = Instance.new("ScrollingFrame")
		local PageListL = Instance.new("UIListLayout")

		TabButton.Name = ""
		TabButton.Parent = Tabs
		TabButton.BackgroundColor3 = Color3.fromRGB(170, 108, 32)
		TabButton.BackgroundTransparency = 1
		TabButton.Position = UDim2.new(0.0443037972, 0, 0, 0)
		TabButton.Size = UDim2.new(0, 144, 0, 28)
		TabButton.Font = Enum.Font.Creepster
		TabButton.Text = pgname
		TabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
		TabButton.TextSize = 24.000

		TabButtonC.CornerRadius = UDim.new(0, 6)
		TabButtonC.Name = "TabButtonC"
		TabButtonC.Parent = TabButton

		Container.Name = "Container"
		Container.Parent = Main

		Page.Name = pgname
		Page.Parent = Container
		Page.Active = true
		Page.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Page.BackgroundTransparency = 1.000
		Page.BorderSizePixel = 0
		Page.Position = UDim2.new(0.296428561, 0, 0.0257879645, 0)
		Page.Size = UDim2.new(0, 394, 0, 330)
		Page.CanvasSize = UDim2.new(0, 0, 0, 0)
		Page.ScrollBarThickness = 6

		PageListL.Name = "PageListL"
		PageListL.Parent = Page
		PageListL.HorizontalAlignment = Enum.HorizontalAlignment.Center
		PageListL.SortOrder = Enum.SortOrder.LayoutOrder
		
		if firstCat then
			firstCat = false
			Page.Visible = true
			TabButton.BackgroundTransparency = 0
		else
			Page.Visible = false
			TabButton.BackgroundTransparency = 1
		end
		
		TabButton.MouseButton1Click:Connect(function()
			for i,v in next, Tabs:GetChildren() do
				if v:IsA("GuiButton") then
					if v.Text == Page.Name then
						ts:Create(v,tween(.16),{
							BackgroundTransparency = 0
						}):Play()
						ts:Create(TabButton,tween(.16),{
							TextSize=18
						}):Play()
						wait(.17)
						ts:Create(TabButton,tween(.16),{
							TextSize=24
						}):Play()
					else
						ts:Create(v,tween(.16),{
							BackgroundTransparency = 1
						}):Play()
					end
				end
			end
			
			for i,v in next,Container:GetChildren() do
				v.Visible = false
			end
			Page.Visible = true
		end)
		
		local secc = {}
		function secc:AddSection(secname)
			local Section = Instance.new("ImageLabel")
			local SectionName = Instance.new("TextLabel")
			local SectionListL = Instance.new("UIListLayout")

			Section.Name = "Section"
			Section.Parent = Page
			Section.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Section.BackgroundTransparency = 1.000
			Section.Position = UDim2.new(0.373096436, 0, 0, 0)
			Section.Size = UDim2.new(0, 379, 0, 26)
			Section.Image = "rbxassetid://3570695787"
			Section.ImageColor3 = Color3.fromRGB(42, 42, 42)
			Section.ImageTransparency = 0.200
			Section.ScaleType = Enum.ScaleType.Slice
			Section.SliceCenter = Rect.new(100, 100, 100, 100)
			Section.SliceScale = 0.060

			SectionName.Name = "SectionName"
			SectionName.Parent = Section
			SectionName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			SectionName.BackgroundTransparency = 1.000
			SectionName.Position = UDim2.new(0.0211081803, 0, 0, 0)
			SectionName.Size = UDim2.new(0, 364, 0, 26)
			SectionName.Font = Enum.Font.Creepster
			SectionName.Text = secname or "Section";
			SectionName.TextColor3 = Color3.fromRGB(198, 132, 0)
			SectionName.TextSize = 24.000
			SectionName.TextXAlignment = Enum.TextXAlignment.Left

			SectionListL.Name = "SectionListL"
			SectionListL.Parent = Section
			SectionListL.HorizontalAlignment = Enum.HorizontalAlignment.Center
			SectionListL.SortOrder = Enum.SortOrder.LayoutOrder
			SectionListL.Padding = UDim.new(0, 7)
			
			Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y)
			
			local pgss = {}
			function pgss:Add(Type,Name,callback,Options)
				if Type:lower() == "button" then
					
					local BtnFunc={}
					local Button = Instance.new("TextButton")
					local ButtonC = Instance.new("UICorner")

					Button.Name = ""
					Button.Parent = Section
					Button.BackgroundColor3 = Color3.fromRGB(170, 108, 32)
					Button.BorderSizePixel = 0
					Button.Position = UDim2.new(0.0211081803, 0, 0.440677971, 0)
					Button.Size = UDim2.new(0, 363, 0, 34)
					Button.Font = Enum.Font.Creepster
					Button.Text = Name
					Button.TextColor3 = Color3.fromRGB(255, 255, 255)
					Button.TextSize = 24.000

					ButtonC.CornerRadius = UDim.new(0, 6)
					ButtonC.Name = "ButtonC"
					ButtonC.Parent = Button
					
					local SecPadding_Y = UDim2.new(0,0,0,8)
					Section.Size = UDim2.new(0, 379,0, SectionListL.AbsoluteContentSize.Y) + SecPadding_Y
					Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y) + UDim2.new(0,0,0,1)
					
					Button.MouseButton1Click:Connect(function()
						callback()
						if Options.txtanimated then
							ts:Create(Button,tween(.06),{
								TextSize=18
							}):Play()
							wait(.07)
							ts:Create(Button,tween(.06),{
								TextSize=24
							}):Play()
						end
					end)
					
					function BtnFunc:UpdateHeader(txt)
						Button.Text = txt
					end
					return BtnFunc
					
				elseif Type:lower() == "toggle" then
					
					local togFunc = {}
					local enabled = false
					
					local Toggle = Instance.new("TextButton")
					local ToggleC = Instance.new("UICorner")
					local ToggleName = Instance.new("TextLabel")
					local Tog = Instance.new("TextButton")
					local TogC = Instance.new("UICorner")
					local Togg = Instance.new("TextButton")
					local ToggC = Instance.new("UICorner")

					Toggle.Name = "Toggle"
					Toggle.Parent = Section
					Toggle.BackgroundColor3 = Color3.fromRGB(170, 108, 32)
					Toggle.BorderSizePixel = 0
					Toggle.Position = UDim2.new(0.0211081803, 0, 0.440677971, 0)
					Toggle.Size = UDim2.new(0, 363, 0, 34)
					Toggle.Font = Enum.Font.Creepster
					Toggle.Text = ""
					Toggle.TextColor3 = Color3.fromRGB(255, 255, 255)
					Toggle.TextSize = 24.000

					ToggleC.CornerRadius = UDim.new(0, 6)
					ToggleC.Name = "ToggleC"
					ToggleC.Parent = Toggle

					ToggleName.Name = "ToggleName"
					ToggleName.Parent = Toggle
					ToggleName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					ToggleName.BackgroundTransparency = 1.000
					ToggleName.Position = UDim2.new(0.0220385678, 0, 0.117647059, 0)
					ToggleName.Size = UDim2.new(0, 200, 0, 26)
					ToggleName.Font = Enum.Font.Creepster
					ToggleName.Text = Name or "Toggle";
					ToggleName.TextColor3 = Color3.fromRGB(255, 255, 255)
					ToggleName.TextSize = 24.000
					ToggleName.TextXAlignment = Enum.TextXAlignment.Left

					Tog.Name = "Tog"
					Tog.Parent = Toggle
					Tog.BackgroundColor3 = Color3.fromRGB(126, 84, 0)
					Tog.BorderSizePixel = 0
					Tog.Position = UDim2.new(0.847000003, 0, 0.118000001, 0)
					Tog.Size = UDim2.new(0, 52, 0, 26)
					Tog.Font = Enum.Font.SourceSans
					Tog.Text = ""
					Tog.TextColor3 = Color3.fromRGB(0, 0, 0)
					Tog.TextSize = 14.000

					TogC.CornerRadius = UDim.new(0, 6)
					TogC.Name = "TogC"
					TogC.Parent = Tog

					Togg.Name = "Togg"
					Togg.Parent = Tog
					Togg.BackgroundColor3 = Color3.fromRGB(225, 150, 0)
					Togg.BorderSizePixel = 0
					Togg.Position = UDim2.new(0.1, 0, 0.154, 0)
					Togg.Size = UDim2.new(0, 18, 0, 18)
					Togg.Font = Enum.Font.SourceSans
					Togg.Text = ""
					Togg.TextColor3 = Color3.fromRGB(0, 0, 0)
					Togg.TextSize = 14.000

					ToggC.CornerRadius = UDim.new(0, 6)
					ToggC.Name = "ToggC"
					ToggC.Parent = Togg

					local SecPadding_Y = UDim2.new(0,0,0,8)
					Section.Size = UDim2.new(0, 379,0, SectionListL.AbsoluteContentSize.Y) + SecPadding_Y
					Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y) + UDim2.new(0,0,0,1)

					if Options then
						if Options.enabled then
							enabled = true
							ts:Create(Togg,tween(.2),{
								Position = UDim2.new(0.55, 0,0.154, 0)
							}):Play()
							callback(enabled)
						end
					end
					
					local function Fire()
						enabled = not enabled
						if enabled then
							ts:Create(Togg,tween(.2),{
								Position = UDim2.new(0.55, 0,0.154, 0)
							}):Play()
						else
							ts:Create(Togg,tween(.2),{
								Position = UDim2.new(0.1, 0, 0.154, 0)
							}):Play()
						end
						callback(enabled)
					end
					Toggle.MouseButton1Click:Connect(Fire)
					Togg.MouseButton1Click:Connect(Fire)
					Tog.MouseButton1Click:Connect(Fire)
					
					function togFunc(setstate)
						enabled = setstate
						if setstate then
							ts:Create(Togg,tween(.2),{
								Position = UDim2.new(0.55, 0,0.154, 0)
							}):Play()
						else
							ts:Create(Togg,tween(.2),{
								Position = UDim2.new(0.1, 0, 0.154, 0)
							}):Play()
						end
						callback(setstate)
					end
					return togFunc
					
				elseif Type:lower() == "slider" then
					
					local sliderFunc = {}
					local min = Options.min
					local max = Options.max
					local default = Options.default
					local Value;
					
					local Slider = Instance.new("ImageLabel")
					local SliderName = Instance.new("TextLabel")
					local SliderCount = Instance.new("TextLabel")
					local SliderInner = Instance.new("TextButton")
					local SliderIC = Instance.new("UICorner")
					local SliderFrame = Instance.new("ImageLabel")

					Slider.Name = "Slider"
					Slider.Parent = Section
					Slider.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					Slider.BackgroundTransparency = 1.000
					Slider.Position = UDim2.new(0.0211081803, 0, 0.657142878, 0)
					Slider.Size = UDim2.new(0, 363, 0, 60)
					Slider.Image = "rbxassetid://3570695787"
					Slider.ImageColor3 = Color3.fromRGB(170, 108, 32)
					Slider.ScaleType = Enum.ScaleType.Slice
					Slider.SliceCenter = Rect.new(100, 100, 100, 100)
					Slider.SliceScale = 0.060

					SliderName.Name = "SliderName"
					SliderName.Parent = Slider
					SliderName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					SliderName.BackgroundTransparency = 1.000
					SliderName.BorderSizePixel = 0
					SliderName.Position = UDim2.new(0.0220385678, 0, 0, 0)
					SliderName.Size = UDim2.new(0, 154, 0, 33)
					SliderName.Font = Enum.Font.Creepster
					SliderName.Text = Name or "Slider";
					SliderName.TextColor3 = Color3.fromRGB(255, 255, 255)
					SliderName.TextSize = 24.000
					SliderName.TextXAlignment = Enum.TextXAlignment.Left

					SliderCount.Name = "SliderCount"
					SliderCount.Parent = Slider
					SliderCount.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					SliderCount.BackgroundTransparency = 1.000
					SliderCount.BorderSizePixel = 0
					SliderCount.Position = UDim2.new(0.564738333, 0, 0, 0)
					SliderCount.Size = UDim2.new(0, 154, 0, 33)
					SliderCount.Font = Enum.Font.Creepster
					SliderCount.Text = min or "1";
					SliderCount.TextColor3 = Color3.fromRGB(255, 255, 255)
					SliderCount.TextSize = 24.000
					SliderCount.TextXAlignment = Enum.TextXAlignment.Right

					SliderInner.Name = "SliderInner"
					SliderInner.Parent = Slider
					SliderInner.BackgroundColor3 = Color3.fromRGB(34, 34, 34)
					SliderInner.BackgroundTransparency = 0.500
					SliderInner.BorderSizePixel = 0
					SliderInner.Position = UDim2.new(0.0137741044, 0, 0.73333329, 0)
					SliderInner.Size = UDim2.new(0, 353, 0, 12)
					SliderInner.Font = Enum.Font.SourceSans
					SliderInner.Text = ""
					SliderInner.TextColor3 = Color3.fromRGB(0, 0, 0)
					SliderInner.TextSize = 14.000

					SliderIC.CornerRadius = UDim.new(0, 6)
					SliderIC.Name = "SliderIC"
					SliderIC.Parent = SliderInner

					SliderFrame.Name = "SliderFrame"
					SliderFrame.Parent = SliderInner
					SliderFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					SliderFrame.BackgroundTransparency = 1.000
					SliderFrame.Size = UDim2.new(0, 100, 0, 12)
					SliderFrame.Image = "rbxassetid://3570695787"
					SliderFrame.ImageColor3 = Color3.fromRGB(170, 0, 0)
					SliderFrame.ScaleType = Enum.ScaleType.Slice
					SliderFrame.SliceCenter = Rect.new(100, 100, 100, 100)
					SliderFrame.SliceScale = 0.060

					local SecPadding_Y = UDim2.new(0,0,0,8)
					Section.Size = UDim2.new(0, 379,0, SectionListL.AbsoluteContentSize.Y) + SecPadding_Y
					Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y) + UDim2.new(0,0,0,1)

					if default then
						SliderCount.Text = default
						callback(default)
						local def = (default - min) / (max - min)
						ts:Create(SliderFrame,tween(.05),{
							Size=UDim2.new(def,0,0,12)
						}):Play()
					end
					
					if Options.percent then
						SliderCount.Text = default.."%"
					else
						SliderCount.Text = default
					end
					
					SliderInner.MouseButton1Down:Connect(function()
						Value = math.floor((((tonumber(max) - tonumber(min)) / 353) * SliderFrame.AbsoluteSize.X) + tonumber(min)) or 0
						pcall(function()
							if Options.percent then
								SliderCount.Text = Value.."%"
							else
								SliderCount.Text = Value
							end
							callback(Value)
						end)
						SliderFrame.Size = UDim2.new(0, math.clamp(mouse.X - SliderFrame.AbsolutePosition.X, 0, 353), 0, 12)
						moveconnection = mouse.Move:Connect(function()
							if Options.percent then
								SliderCount.Text = Value.."%"
							else
								SliderCount.Text = Value
							end
							Value = math.floor((((tonumber(max) - tonumber(min)) / 353) * SliderFrame.AbsoluteSize.X) + tonumber(min))
							pcall(function()
								if Options.percent then
									SliderCount.Text = Value.."%"
								else
									SliderCount.Text = Value
								end
								callback(Value)
							end)
							SliderFrame.Size = UDim2.new(0, math.clamp(mouse.X - SliderFrame.AbsolutePosition.X, 0, 353), 0, 12)
						end)
						releaseconnection = uis.InputEnded:Connect(function(Mouse)
							if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
								if Options.percent then
									SliderCount.Text = Value.."%"
								else
									SliderCount.Text = Value
								end
								Value = math.floor((((tonumber(max) - tonumber(min)) / 353) * SliderFrame.AbsoluteSize.X) + tonumber(min))
								pcall(function()
									if Options.percent then
										SliderCount.Text = Value.."%"
									else
										SliderCount.Text = Value
									end
									callback(Value)
								end)
								SliderFrame.Size = UDim2.new(0, math.clamp(mouse.X - SliderFrame.AbsolutePosition.X, 0, 353), 0, 12)
								moveconnection:Disconnect()
								releaseconnection:Disconnect()
							end
						end)
					end)
					
					function sliderFunc:Set(tochange)
						ts:Create(SliderFrame,tween(.2),{Size=UDim2.new((tochange or 0) / max, 0, 0, 12)})
						--SliderFrame.Size = UDim2.new((tochange or 0) / max, 0, 0, 12)
						SliderCount.Text = tostring(tochange and math.floor((tochange / max) * (max - min) + min) or 0)
						pcall(callback, tochange)
					end
					return sliderFunc
					
				elseif Type:lower() == "dropdown" then
					
					local dropFunc = {}
					local isDropped = false
					
					local DropDown = Instance.new("ImageLabel")
					local DropName = Instance.new("TextLabel")
					local DDOpenShadow = Instance.new("TextButton")
					local DDopeSDCorner = Instance.new("UICorner")
					local DDOpen = Instance.new("TextButton")
					local DDopeCorner = Instance.new("UICorner")
					local DropDownListL = Instance.new("UIListLayout")
					local DropContainer = Instance.new("ScrollingFrame")
					local DropConListL = Instance.new("UIListLayout")

					DropDown.Name = "DropDown"
					DropDown.Parent = Section
					DropDown.ClipsDescendants = true
					DropDown.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					DropDown.BackgroundTransparency = 1.000
					DropDown.Position = UDim2.new(0.0211081803, 0, 0.657142878, 0)
					DropDown.Size = UDim2.new(0, 363, 0, 34)
					DropDown.Image = "rbxassetid://3570695787"
					DropDown.ImageColor3 = Color3.fromRGB(170, 108, 32)
					DropDown.ScaleType = Enum.ScaleType.Slice
					DropDown.SliceCenter = Rect.new(100, 100, 100, 100)
					DropDown.SliceScale = 0.060

					DropName.Name = "DropName"
					DropName.Parent = DropDown
					DropName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					DropName.BackgroundTransparency = 1.000
					DropName.BorderSizePixel = 0
					DropName.Position = UDim2.new(0.287878782, 0, 0, 0)
					DropName.Size = UDim2.new(0, 348, 0, 33)
					DropName.Font = Enum.Font.Creepster
					DropName.Text = Name or "Button"
					DropName.TextColor3 = Color3.fromRGB(255, 255, 255)
					DropName.TextSize = 24.000
					DropName.TextXAlignment = Enum.TextXAlignment.Left

					DDOpenShadow.Name = "DDOpenShadow"
					DDOpenShadow.Parent = DropName
					DDOpenShadow.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
					DDOpenShadow.BorderSizePixel = 0
					DDOpenShadow.Position = UDim2.new(0.935000002, 0, 0.120999999, 0)
					DDOpenShadow.Size = UDim2.new(0, 26, 0, 26)
					DDOpenShadow.Font = Enum.Font.SourceSans
					DDOpenShadow.Text = ""
					DDOpenShadow.TextColor3 = Color3.fromRGB(0, 0, 0)
					DDOpenShadow.TextSize = 14.000

					DDopeSDCorner.CornerRadius = UDim.new(0, 6)
					DDopeSDCorner.Name = "DDopeSDCorner"
					DDopeSDCorner.Parent = DDOpenShadow

					DDOpen.Name = "DDOpen"
					DDOpen.Parent = DDOpenShadow
					DDOpen.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
					DDOpen.BackgroundTransparency = 1.000
					DDOpen.BorderSizePixel = 0
					DDOpen.Size = UDim2.new(0, 26, 0, 26)
					DDOpen.Font = Enum.Font.Creepster
					DDOpen.Text = "<"
					DDOpen.TextColor3 = Color3.fromRGB(255, 255, 255)
					DDOpen.TextSize = 40.000

					DDopeCorner.CornerRadius = UDim.new(0.0599999987, 0)
					DDopeCorner.Name = "DDopeCorner"
					DDopeCorner.Parent = DDOpen

					DropDownListL.Name = "DropDownListL"
					DropDownListL.Parent = DropDown
					DropDownListL.HorizontalAlignment = Enum.HorizontalAlignment.Center
					DropDownListL.SortOrder = Enum.SortOrder.LayoutOrder
					DropDownListL.Padding = UDim.new(0, 7)

					DropContainer.Name = "DropContainer"
					DropContainer.Parent = DropDown
					DropContainer.Active = true
					DropContainer.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					DropContainer.BackgroundTransparency = 1.000
					DropContainer.BorderSizePixel = 0
					DropContainer.Position = UDim2.new(0.362258941, 0, 0.248120308, 0)
					DropContainer.Size = UDim2.new(0, 363, 0, 100)
					DropContainer.CanvasSize = UDim2.new(0,0,0,0)
					DropContainer.ScrollBarThickness = 6

					DropConListL.Name = "DropConListL"
					DropConListL.Parent = DropContainer
					DropConListL.HorizontalAlignment = Enum.HorizontalAlignment.Center
					DropConListL.SortOrder = Enum.SortOrder.LayoutOrder
					DropConListL.Padding = UDim.new(0, 7)

					local SecPadding_Y = UDim2.new(0,0,0,8)
					Section.Size = UDim2.new(0, 379,0, SectionListL.AbsoluteContentSize.Y) + SecPadding_Y
					Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y) + UDim2.new(0,0,0,1)

					local function Drop()
						isDropped = not isDropped
						if isDropped then
							ts:Create(DDOpen,tween(.3),{
								Rotation = -90
							}):Play()
							ts:Create(DropDown,tween(.3),{
								Size=UDim2.new(0, 363, 0, 146)
							}):Play()
							ts:Create(Section,tween(.3),{
								Size=Section.Size+UDim2.new(0,0,0,113)
							}):Play()
							ts:Create(Page,tween(.3),{
								CanvasSize=Page.CanvasSize+UDim2.new(0,0,0,113)
							}):Play()
							ts:Create(DropContainer,tween(.3),{
								CanvasSize=UDim2.new(0,0,0,DropConListL.AbsoluteContentSize.Y)
							}):Play()
							DropName.Text = Name
						else
							ts:Create(DDOpen,tween(.3),{
								Rotation = 0
							}):Play()
							ts:Create(DropDown,tween(.3),{
								Size=UDim2.new(0, 363, 0, 34)
							}):Play()
							ts:Create(Section,tween(.3),{
								Size=Section.Size-UDim2.new(0,0,0,113)
							}):Play()
							ts:Create(Page,tween(.3),{
								CanvasSize=Page.CanvasSize-UDim2.new(0,0,0,113)
							}):Play()	
							ts:Create(DropContainer,tween(.3),{
								CanvasSize=UDim2.new(0,0,0,0)
							}):Play()
						end
					end
					DDOpen.MouseButton1Click:Connect(Drop)
					DDOpenShadow.MouseButton1Click:Connect(Drop)
					
					for i,v in next,Options.option or Options.list do

						local Button = Instance.new("TextButton")
						local ButtonC = Instance.new("UICorner")

						Button.Name = ""
						Button.Parent = DropContainer
						Button.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
						Button.BackgroundTransparency = 1.000
						Button.BorderSizePixel = 0
						Button.Position = UDim2.new(0.0137741044, 0, 0, 0)
						Button.Size = UDim2.new(0, 350, 0, 34)
						Button.Font = Enum.Font.Creepster
						Button.Text = v
						Button.TextColor3 = Color3.fromRGB(170, 0, 0)
						Button.TextSize = 24.000

						ButtonC.CornerRadius = UDim.new(0, 6)
						ButtonC.Name = "ButtonC"
						ButtonC.Parent = Button
						
						Button.MouseButton1Click:Connect(function()
							isDropped = false
							callback(v)
							DropName.Text = Button.Text
							if Options.autoclose then
								ts:Create(DDOpen,tween(.3),{
									Rotation = 0
								}):Play()
								ts:Create(DropDown,tween(.3),{
									Size=UDim2.new(0, 363, 0, 34)
								}):Play()
								ts:Create(Section,tween(.3),{
									Size=Section.Size-UDim2.new(0,0,0,113)
								}):Play()
								ts:Create(Page,tween(.3),{
									CanvasSize=Page.CanvasSize-UDim2.new(0,0,0,113)
								}):Play()	
							end
						end)
						
						
						
					end
					
				elseif Type:lower() == "textbox" then
					
					local boxFunc={}
					
					local TextBox = Instance.new("TextButton")
					local TextboxC = Instance.new("UICorner")
					local TextboxName = Instance.new("TextLabel")
					local TypeBox = Instance.new("TextBox")
					local TypeboxC = Instance.new("UICorner")

					TextBox.Name = "TextBox"
					TextBox.Parent = Section
					TextBox.BackgroundColor3 = Color3.fromRGB(170, 108, 32)
					TextBox.BorderSizePixel = 0
					TextBox.Position = UDim2.new(0.0211081803, 0, 0.440677971, 0)
					TextBox.Size = UDim2.new(0, 363, 0, 34)
					TextBox.Font = Enum.Font.Creepster
					TextBox.Text = ""
					TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
					TextBox.TextSize = 24.000

					TextboxC.CornerRadius = UDim.new(0, 6)
					TextboxC.Name = "TextboxC"
					TextboxC.Parent = TextBox

					TextboxName.Name = "TextboxName"
					TextboxName.Parent = TextBox
					TextboxName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					TextboxName.BackgroundTransparency = 1.000
					TextboxName.Position = UDim2.new(0.0220385678, 0, 0.117647059, 0)
					TextboxName.Size = UDim2.new(0, 200, 0, 26)
					TextboxName.Font = Enum.Font.Creepster
					TextboxName.Text = Name or "TextBox"
					TextboxName.TextColor3 = Color3.fromRGB(255, 255, 255)
					TextboxName.TextSize = 24.000
					TextboxName.TextXAlignment = Enum.TextXAlignment.Left

					TypeBox.Name = "TypeBox"
					TypeBox.Parent = TextBox
					TypeBox.BackgroundColor3 = Color3.fromRGB(126, 84, 0)
					TypeBox.Position = UDim2.new(0.6418733, 0, 0.117647059, 0)
					TypeBox.Size = UDim2.new(0, 126, 0, 26)
					TypeBox.Font = Enum.Font.Creepster
					TypeBox.PlaceholderText = Options.txt
					TypeBox.Text = ""
					TypeBox.TextColor3 = Color3.fromRGB(255,255,255)
					TypeBox.TextSize = 24.000
					TypeBox.TextXAlignment = Enum.TextXAlignment.Right

					TypeboxC.CornerRadius = UDim.new(0, 6)
					TypeboxC.Name = "TextboxC"
					TypeboxC.Parent = TypeBox

					local SecPadding_Y = UDim2.new(0,0,0,8)
					Section.Size = UDim2.new(0, 379,0, SectionListL.AbsoluteContentSize.Y) + SecPadding_Y
					Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y) + UDim2.new(0,0,0,1)

					TypeBox.FocusLost:Connect(function(ePressed)
						if not ePressed then
							return
						else
							callback(TypeBox.Text)
							wait(.018)
							TypeBox.Text = ""
						end
					end)
					
					function boxFunc:UpdateText(txt)
						TypeBox.PlaceholderText = txt
					end
					return boxFunc
					
				elseif Type:lower() == "keybind" then
					
					local default = nil
					
					local Keybind = Instance.new("TextButton")
					local KBC = Instance.new("UICorner")
					local KBName = Instance.new("TextLabel")
					local Bind = Instance.new("TextLabel")

					Keybind.Name = "Keybind"
					Keybind.Parent = Section
					Keybind.BackgroundColor3 = Color3.fromRGB(170, 108, 32)
					Keybind.BorderSizePixel = 0
					Keybind.Position = UDim2.new(0.0211081803, 0, 0.440677971, 0)
					Keybind.Size = UDim2.new(0, 363, 0, 34)
					Keybind.Font = Enum.Font.Creepster
					Keybind.Text = ""
					Keybind.TextColor3 = Color3.fromRGB(255, 255, 255)
					Keybind.TextSize = 24.000

					KBC.CornerRadius = UDim.new(0, 6)
					KBC.Name = "KBC"
					KBC.Parent = Keybind

					KBName.Name = "KBName"
					KBName.Parent = Keybind
					KBName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					KBName.BackgroundTransparency = 1.000
					KBName.Position = UDim2.new(0.0220385678, 0, 0.117647059, 0)
					KBName.Size = UDim2.new(0, 200, 0, 26)
					KBName.Font = Enum.Font.Creepster
					KBName.Text = Name or "Keybind"
					KBName.TextColor3 = Color3.fromRGB(255, 255, 255)
					KBName.TextSize = 24.000
					KBName.TextXAlignment = Enum.TextXAlignment.Left

					Bind.Name = "Bind"
					Bind.Parent = Keybind
					Bind.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					Bind.BackgroundTransparency = 1.000
					Bind.BorderSizePixel = 0
					Bind.Position = UDim2.new(0.625344336, 0, 0.117647059, 0)
					Bind.Size = UDim2.new(0, 131, 0, 26)
					Bind.Font = Enum.Font.Creepster
					Bind.Text = Options.bind
					Bind.TextColor3 = Color3.fromRGB(255, 255, 255)
					Bind.TextSize = 24.000
					Bind.TextXAlignment = Enum.TextXAlignment.Right
					default = Options.bind

					local SecPadding_Y = UDim2.new(0,0,0,8)
					Section.Size = UDim2.new(0, 379,0, SectionListL.AbsoluteContentSize.Y) + SecPadding_Y
					Page.CanvasSize = UDim2.new(0,0,0,PageListL.AbsoluteContentSize.Y) + UDim2.new(0,0,0,1)

					Keybind.MouseButton1Click:Connect(function()
						Bind.Text = ". . ."
						local a = uis.InputBegan:Wait()
						if a.KeyCode.Name ~= "Unknown" then
							default = a.KeyCode.Name
							Bind.Text = a.KeyCode.Name
						end
					end)
					
					uis.InputBegan:Connect(function(input,p)
						if not p then
							if input.KeyCode.Name == default then
								callback()
							end
						end
					end)
					
				end
			end
			return pgss
		end
		return secc
	end
	return tbss
end
return hl

--[[Adding of lib/tabs/Sections/features:
main = lib:MakeUI()

tab1 = main:AddPage("Tab1")
tab2 = main:AddPage("Tab2")

sec1 = tab1:AddSection("SecTest")

sec1:Add(
	"Button",
	"TestBttn",
	function()
		
	end,{
		txtanimated = true
	}
)
sec1:Add(
	"Toggle",
	"TstToggle",
	function()
		
	end,{
		enabled = false
	}
)
sec1:Add(
	"Slider",
	"YoSliderWorksFine",
	function()
		
	end,{
		min=1,
		max=500,
		default=190,
		percent=true
	}
)
sec1:Add(
	"DropDown",
	"DropTest",
	function()
		
	end,{
		option = {
			"Test","Hello","Bro","Work","As","Far"
		},
		autoclose = true
	}
)
sec1:Add(
	"Textbox",
	"Hello",
	function()
		
	end,{
		txt = "Bro"
	}
)
sec1:Add(
	"Keybind",
	"TestBro",
	function()
		
	end,{
		bind = "LeftControl"
	}
)]]--
