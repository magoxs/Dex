-- Supondo que a variável 'money' armazene o dinheiro do jogador
local money = 1000 -- Valor inicial de dinheiro do jogador

-- Função para dobrar o dinheiro
function doubleMoney()
    money = money * 2
end

-- Chamando a função para dobrar o dinheiro
doubleMoney()

-- Exibindo o novo valor de dinheiro
print("Novo valor de dinheiro: " .. money)