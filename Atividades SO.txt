Clear-Host

# 1)
Write-Host "`n1) Fibonacci" -ForegroundColor Yellow

[int]$qtd = Read-Host "Informe quantos termos deseja visualizar"

$n1 = 0
$n2 = 1

Write-Host "`nSequência gerada:" -ForegroundColor Green

if ($qtd -ge 1) {
    Write-Host $n1 -NoNewline
}

if ($qtd -ge 2) {
    Write-Host " - $n2" -NoNewline
}

for ($i = 2; $i -lt $qtd; $i++) {

    $prox = $n1 + $n2

    Write-Host " - $prox" -NoNewline

    $n1 = $n2
    $n2 = $prox
}

Write-Host ""


# 2)
Write-Host "`n2) Contagem" -ForegroundColor Yellow

[int]$inicio = Read-Host "Digite o valor inicial"
[int]$final = Read-Host "Digite o valor final"
[int]$incremento = Read-Host "Informe o incremento"

$ordem = Read-Host "Escolha Crescente ou Decrescente"

Write-Host "`nResultado da contagem:" -ForegroundColor Cyan

if ($ordem -match "^crescente") {

    if ($inicio -gt $final) {

        Write-Host "Erro: o início deve ser menor que o final." -ForegroundColor Red
    }
    else {

        for ($i = $inicio; $i -le $final; $i += $incremento) {

            Write-Host $i
        }
    }
}
elseif ($ordem -match "^decrescente") {

    if ($inicio -lt $final) {

        Write-Host "Erro: o início deve ser maior que o final." -ForegroundColor Red
    }
    else {

        for ($i = $inicio; $i -ge $final; $i -= $incremento) {

            Write-Host $i
        }
    }
}
else {

    Write-Host "Ordem inválida." -ForegroundColor Red
}


# 3)
Write-Host "`n3) Tabuada" -ForegroundColor Yellow

$numAleatorio = Get-Random -Minimum 1 -Maximum 21

Write-Host "Número sorteado: $numAleatorio`n" -ForegroundColor Green

for ($i = 1; $i -le 10; $i++) {

    $resultado = $numAleatorio * $i

    Write-Host "$numAleatorio x $i = $resultado"
}


# 4)
do {

    Write-Host "`n4) Matemática" -ForegroundColor Yellow

    $acertos = 0
    $jogando = $true

    while ($jogando) {

        $n1 = Get-Random -Minimum 2 -Maximum 101
        $n2 = Get-Random -Minimum 2 -Maximum 101

        $tipoConta = Get-Random -Minimum 1 -Maximum 4

        if ($tipoConta -eq 1) {

            $op = "+"
            $respostaCorreta = $n1 + $n2
        }
        elseif ($tipoConta -eq 2) {

            $op = "-"
            $respostaCorreta = $n1 - $n2
        }
        else {

            $op = "*"
            $respostaCorreta = $n1 * $n2
        }

        $palpite = Read-Host "Resolva: $n1 $op $n2"

        if ([int]$palpite -eq $respostaCorreta) {

            Write-Host "Resposta correta!" -ForegroundColor Green

            $acertos++
        }
        else {

            Write-Host "Resposta incorreta! Resultado correto: $respostaCorreta" -ForegroundColor Red
            Write-Host "Quantidade de acertos: $acertos" -ForegroundColor Cyan

            $jogando = $false
        }
    }

    $continuarMath = Read-Host "Deseja jogar novamente? (S/N)"

} while ($continuarMath -eq "S" -or $continuarMath -eq "s")


# 5)
do {

    Write-Host "`n5) Pedra, Papel ou Tesoura" -ForegroundColor Yellow

    $escolhaUsuario = Read-Host "Digite Pedra, Papel ou Tesoura"

    $numeroMaquina = Get-Random -Minimum 1 -Maximum 4

    if ($numeroMaquina -eq 1) {

        $escolhaMaquina = "Pedra"
    }
    elseif ($numeroMaquina -eq 2) {

        $escolhaMaquina = "Papel"
    }
    else {

        $escolhaMaquina = "Tesoura"
    }

    Write-Host "Computador escolheu: $escolhaMaquina"

    if ($escolhaUsuario -eq $escolhaMaquina) {

        Write-Host "Empate!" -ForegroundColor Cyan
    }
    elseif (
        ($escolhaUsuario -eq "Pedra" -and $escolhaMaquina -eq "Tesoura") -or
        ($escolhaUsuario -eq "Tesoura" -and $escolhaMaquina -eq "Papel") -or
        ($escolhaUsuario -eq "Papel" -and $escolhaMaquina -eq "Pedra")
    ) {

        Write-Host "Você venceu!" -ForegroundColor Green
    }
    else {

        Write-Host "Você perdeu!" -ForegroundColor Red
    }

    $continuarPPT = Read-Host "Deseja continuar? (S/N)"

} while ($continuarPPT -eq "S" -or $continuarPPT -eq "s")


# 6)
do {

    Write-Host "`n6) Adivinhação" -ForegroundColor Yellow

    $numeroSorteado = Get-Random -Minimum 50 -Maximum 101

    $tentativasMaximas = 6
    $ganhou = $false

    Write-Host "Você possui $tentativasMaximas tentativas."

    for ($i = 1; $i -le $tentativasMaximas; $i++) {

        [int]$palpite = Read-Host "Digite o palpite da tentativa $i"

        if ($palpite -eq $numeroSorteado) {

            Write-Host "Parabéns! Você acertou o número $numeroSorteado" -ForegroundColor Green

            $ganhou = $true

            break
        }
        elseif ($palpite -lt $numeroSorteado) {

            Write-Host "O número é maior..." -ForegroundColor Cyan
        }
        else {

            Write-Host "O número é menor..." -ForegroundColor Cyan
        }
    }

    if (-not $ganhou) {

        Write-Host "Fim de jogo! O número correto era $numeroSorteado" -ForegroundColor Red
    }

    $continuarAdivinha = Read-Host "Deseja jogar novamente? (S/N)"

} while ($continuarAdivinha -eq "S" -or $continuarAdivinha -eq "s")
```
