print("✅ kievinha - Auto Click Blocker")
print("🔴 Iniciando...\n")

local rs = game:GetService("ReplicatedStorage")

-- 🔴 BLOQUEIA O REMOTE DE DETECÇÃO
local autoClickerDetected = rs.Remotes.GameServices.ToServer:FindFirstChild("AutoclickerDetected")
if autoClickerDetected then
    autoClickerDetected:Destroy()
    print("✅ AutoclickerDetected DESTRUÍDO!")
else
    print("⚠️ AutoclickerDetected não encontrado")
end

-- 🔴 BLOQUEIA OUTRAS DETECÇÕES POSSÍVEIS
local toServer = rs.Remotes.GameServices.ToServer
if toServer then
    for _, remote in ipairs(toServer:GetChildren()) do
        if remote.Name:lower():find("detect") or remote.Name:lower():find("autoclick") then
            remote:Destroy()
            print("✅ " .. remote.Name .. " DESTRUÍDO!")
        end
    end
end

print("\n✅ Detecção de autoclicker BLOQUEADA!")
print("🟢 Pronto pra usar! 🎮\n")
