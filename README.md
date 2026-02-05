-- [[ DASH HUB LOADER - FIX FINAL ]] --

-- 1. Ativa as variáveis para o script não fechar sozinho
getgenv().DashHub_Auth_Verified = true
getgenv().DashHub_ExecutadoPeloLoader = true
_G.DashHub_Auth_Verified = true
_G.DashHub_ExecutadoPeloLoader = true

-- 2. Função que baixa e LIMPA o código antes de rodar
local function ForcaBrutaLoad(url, nomeJogo)
    print("[...] Tentando carregar: " .. nomeJogo)
    
    local success, content = pcall(function()
        return game:HttpGet(url)
    end)

    if not success then
        warn("❌ Erro de Rede: Não foi possível baixar o script do " .. nomeJogo)
        return
    end

    -- LIMPEZA AUTOMÁTICA DE LIXO DO GITHUB
    -- Remove cabeçalhos de README (# Titulo)
    local cleanCode = content:gsub("^#.-\n", "")
    -- Remove blocos de código markdown (```lua ... ```)
    cleanCode = cleanCode:gsub("
