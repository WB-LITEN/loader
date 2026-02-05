-- [[ Smart Loader: Arsenal & UBG ]] --

local placeId = game.PlaceId

if placeId == 286090429 then
    -- SE FOR ARSENAL
    print("Jogo detectado: Arsenal. Carregando Script...")
    loadstring(game:HttpGet("https://raw.githubusercontent.com/WB-LITEN/dash-hub-script-arsenal/main/Source.lua"))()

elseif placeId == 11815767793 then
    -- SE FOR UBG (Untitled Boxing Game)
    print("Jogo detectado: UBG. Carregando Script...")
    loadstring(game:HttpGet("https://raw.githubusercontent.com/WB-LITEN/Dash-Hub-BETA/main/Dash%20Hub%20BETA"))()

else
    -- SE NÃO FOR NENHUM DOS DOIS
    warn("ERRO: Este script não é compatível com este jogo (ID: " .. placeId .. ")")
end
