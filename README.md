-- [[ DASH HUB - PRIVATE LOADER ]] --
local IDs_Privados = {
    286090429, -- Seu ID
    -- Adicione o ID do seu amigo criador abaixo
    00000000, 
}

local player = game.Players.LocalPlayer
local autorizado = false

-- Verificação de Acesso
for _, id in pairs(IDs_Privados) do
    if player.UserId == id then
        autorizado = true
        break
    end
end

if autorizado then
    -- Variáveis de Autenticação para os scripts ofuscados
    _G.DashHub_Auth_Verified = true
    _G.DashHub_ExecutadoPeloLoader = true
    
    -- Carrega Script Arsenal
    loadstring(game:HttpGet("https://raw.githubusercontent.com/WB-LITEN/dash-hub-script-arsenal/refs/heads/main/README.md"))()
    
    -- Carrega Script UBG/BETA
    loadstring(game:HttpGet("https://raw.githubusercontent.com/WB-LITEN/Dash-Hub-BETA/refs/heads/main/Dash%20Hub%20BETA"))()
    
    print("✅ Dash Hub Privada carregada com sucesso!")
else
    player:Kick("❌ Acesso restrito apenas aos desenvolvedores.")
end
