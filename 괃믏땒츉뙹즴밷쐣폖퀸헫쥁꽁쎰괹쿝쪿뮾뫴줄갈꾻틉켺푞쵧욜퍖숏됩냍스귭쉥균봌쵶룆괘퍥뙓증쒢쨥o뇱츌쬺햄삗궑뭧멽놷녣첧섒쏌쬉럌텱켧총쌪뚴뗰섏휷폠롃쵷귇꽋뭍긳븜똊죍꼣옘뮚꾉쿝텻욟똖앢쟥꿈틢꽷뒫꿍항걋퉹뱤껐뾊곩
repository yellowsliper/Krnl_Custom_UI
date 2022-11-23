local tool = GUI:Tab{
    Name = "Tools",
    Icon = "rbxassetid://6767454852"
}

tool:Button{
    Name = "Drop Tools",
    Description = "Drop all tools",
    Callback = function()
        for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
            if v:IsA("Tool") and v.Name ~= "radio" then
                v.Parent = GetCharacter()
            end
        end
        for i,v in pairs(GetCharacter():GetChildren()) do
            if v:IsA("Tool") and v.Name ~= "radio" then
                v.Parent = Services.Workspace 
            end
        end
    end
}

tool:Button{
    Name = "Drop Tools w/o Mesh",
    Description = "Drop all tools removed mesh",
    Callback = function()
        for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
            if v:IsA("Tool") and v.Name ~= "radio" then
                v.Parent = GetCharacter()
            end
        end
        for i,v in pairs(GetCharacter():GetChildren()) do
            if v:IsA("Tool") and v.Name ~= "radio" then
                if v.Handle:FindFirstChild("Mesh") then
                    Destroy(v.Handle.Mesh)
                end
                v.Parent = Services.Workspace 
            end
        end
    end
}

tool:Button{
    Name = "Grab Tools",
    Description = "Grab all tools in workspace",
    Callback = function()
        for i,v in pairs(game:GetDescendants()) do
            if v:IsA("Tool") then
                firetouchinterest(GetRoot(), v:FindFirstChild("Handle"), 0)
            end
        end
    end
}

tool:Button{
    Name = "Grab Guns",
    Description = "Grab all guns in workspace",
    Callback = function()
        for i,v in pairs(game:GetDescendants()) do
            if v:IsA("Tool") and v.Name == "pistol" then
                firetouchinterest(GetRoot(), v:FindFirstChild("Handle"), 0) 
            end
        end
    end
}

tool:Toggle{
    Name = "Auto Grab Tools",
    Description = "Loop grab tools",
    StartingState = _G.AUTOGETTOOL or false,
    Callback = function(bool)
        _G.AUTOGETTOOL = bool
        while _G.AUTOGETTOOL do
            pcall(function()
                for i,v in pairs(game:GetDescendants()) do
                    if v:IsA("Tool") then
                        firetouchinterest(GetRoot(), v:FindFirstChild("Handle"), 0) 
                    end
                end
            end)
            task.wait()
        end
    end
}

tool:Toggle{
    Name = "Auto Grab Guns",
    Description = "Loop grab guns",
    StartingState = _G.AUTOGETGUN or false,
    Callback = function(bool)
        _G.AUTOGETGUN = bool
        while _G.AUTOGEGUN do
            pcall(function()
                for i,v in pairs(game:GetDescendants()) do
                    if v:IsA("Tool") and v.Name == "pistol" then
                        firetouchinterest(GetRoot(), v:FindFirstChild("Handle"), 0) 
                    end
                end
            end)
            task.wait()
        end
    end
}

give_radio_menu = tool:Dropdown{
    Name = "Radio Giver",
    StartingText = "Select...",
    Description = "You can give radio other player",
    Items = plrs,
    Callback = function(text)
        local Target = Services.Players[string.split(text, " ")[3]]
        LocalPlayer.Character.Humanoid:UnequipTools()
        local Humanoid = LocalPlayer.Character.Humanoid:Clone()
        local Tool = FindTool(LocalPlayer, "radio")
    
        LocalPlayer.Character.Animate.Disabled = true
        LocalPlayer.Character.Humanoid:Destroy()
        Humanoid.Parent = LocalPlayer.Character
        Tool.Parent = LocalPlayer.Character
        if _G.RADIONOMESH then
        Tool.Handle.Mesh:Destroy()
        end
        firetouchinterest(Target.Character.HumanoidRootPart, Tool.Handle, 0); wait(0.1)
        LocalPlayer.Character = nil
    end
}
