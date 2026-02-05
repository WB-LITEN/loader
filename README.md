-- [[ DASH HUB - PRIVATE MULTI-GAME LOADER ]] --
local IDs_Privados = {
    286090429, -- Seu ID
    -- Coloque o ID do seu amigo aqui
}

local Jogos = {
    [286090429] = {
        Nome = "Arsenal",
        URL = "https://raw.githubusercontent.com/WB-LITEN/dash-hub-script-arsenal/refs/heads/main/README.md"
    },
    [11815767793] = {
        Nome = "Ultimate Battleground",
        URL = "https://raw.githubusercontent.com/WB-LITEN/Dash-Hub-BETA/refs/heads/main/Dash%20Hub%20BETA"
    }
}

local player = game.Players.LocalPlayer
local gameData = Jogos[game.PlaceId]

-- 1. Verificar se o jogo tem suporte
if not gameData then
    player:Kick("❌ Dash Hub: Este jogo não tem suporte!")
    return
end

-- 2. Verificar se o ID é de Moderador/Criador
local autorizado = false
for _, id in pairs(IDs_Privados) do
    if player.UserId == id then
        autorizado = true
        break
    end
end

if autorizado then
    _G.DashHub_Auth_Verified = true
    _G.DashHub_ExecutadoPeloLoader = true
    
    print("🎯 Jogo Detectado: " .. gameData.Nome)
    
    local success, result = pcall(function()
        return game:HttpGet(gameData.URL)
    end)
    
    if success then
        local func, err = loadstring(result)
        if func then
            func()
        else
            warn("❌ Erro no código do GitHub: " .. err)
        end
    else
        warn("❌ Falha ao baixar o script do GitHub.")
    end
else
    player:Kick("❌ Acesso negado! ID (" .. player.UserId .. ") não autorizado.")
end
