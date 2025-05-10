-- Interface Profissional Estilo Redz Hub
-- Adaptado para uso em executores e edição via QuickEdit
-- Para uso em jogos privados com scripts customizados

local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Orion/main/source"))()
local Window = OrionLib:MakeWindow({Name = "⚙️ Meu Hub Privado", HidePremium = false, SaveConfig = true, ConfigFolder = "MeuHub"})

-- Aba principal
local MainTab = Window:MakeTab({
	Name = "🏠 Principal",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

-- Speed Hack
MainTab:AddButton({
	Name = "🏃‍♂️ Ativar Speed Hack",
	Callback = function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 100
  	end    
})

-- God Mode
MainTab:AddButton({
	Name = "🛡️ Ativar God Mode",
	Callback = function()
        local h = game.Players.LocalPlayer.Character:FindFirstChild("Humanoid")
        if h then
            h.MaxHealth = math.huge
            h.Health = math.huge
        end
	end    
})

-- No Clip
local noclip = false
MainTab:AddToggle({
	Name = "🌀 Ativar No Clip",
	Default = false,
	Callback = function(value)
        noclip = value
        local RunService = game:GetService("RunService")
        RunService.Stepped:Connect(function()
            if noclip then
                for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                    if v:IsA("BasePart") then
                        v.CanCollide = false
                    end
                end
            end
        end)
	end    
})

-- Créditos
Window:MakeTab({
	Name = "📜 Créditos",
	Icon = "rbxassetid://7733765398",
	PremiumOnly = false
}):AddParagraph("Desenvolvido por:", "SeuNome | Para uso privado")

OrionLib:Init()
