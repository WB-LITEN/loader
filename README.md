-- [[ DASH HUB - LOADER INTELIGENTE ]] --

_G.DashHub_Auth_Verified = true
_G.DashHub_ExecutadoPeloLoader = true

local function ExecutarLimpo(url)
    local success, content = pcall(function() return game:HttpGet(url) end)
    
    if success then
        -- Remove linhas que começam com # (títulos de README.md)
        local codigoLimpo = content:gsub("^#.-\n", ""):gsub("\n#.-\n", "\n")
        
        local func, err = loadstring(codigoLimpo)
        if func then
            func()
        else
            warn("ERRO DE SINTAXE: Verifique se há texto no arquivo do GitHub. Erro: " .. tostring(err))
        end
    else
        warn("ERRO AO BAIXAR SCRIPT DO GITHUB")
    end
end

-- Seleção por PlaceId
if game.PlaceId == 286090429 then
    -- Arsenal
    ExecutarLimpo("https://raw.githubusercontent.com/WB-LITEN/dash-hub-script-arsenal/refs/heads/main/README.md")
elseif game.PlaceId == 11815767793 then
    -- UBG
    ExecutarLimpo("https://raw.githubusercontent.com/WB-LITEN/Dash-Hub-BETA/refs/heads/main/Dash%20Hub%20BETA")
else
    print("Jogo não suportado.")
end
