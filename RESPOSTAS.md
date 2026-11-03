# Respostas da dupla — Atividade PontoCerto

## Dupla

| Papel | Nome completo | Usuário do GitHub |
|---|---|---|
| Integrante 1 (dono do fork) | Vinicius Beleza Vidal | ViniciusBeleza |
| Integrante 2 (colaborador) | João Fernando Albuquerque| Joaofer984 |

## Explicação da solução

A função calculaPontos recebe a regra da campanha como argumento e a aplica ao valor da compra, então existe uma só função de cálculo para qualquer campanha. As regras são funções Int -> Int guardadas em variáveis, e as fábricas campanhaMultiplicadora e campanhaBonus devolvem regras novas a partir de um número, sem precisar escrever uma função para cada fator ou bônus. A função acumula combina duas regras aplicando uma depois da outra. Assim, uma campanha nova vira só um valor novo (uma lambda ou uma chamada de fábrica), e o código de cálculo não é repetido nem alterado.

## Desafio 2

As promoções duram só um dia e são usadas uma única vez. Uma função nomeada criaria um nome que ninguém vai reaproveitar e deixaria o código maior. Com a lambda, a regra fica escrita no próprio lugar da chamada, curta e fácil de ler.

## Desafio 3

campanhaMultiplicadora 5 devolve uma função, não um número: uma regra que multiplica os pontos por 5. O :t campanhaMultiplicadora 5 mostra Int -> Int, que é tipo de função. Se fosse um número, o :t mostraria só Int. O mesmo vale para :t blackFriday, que mostra blackFriday :: Int -> Int.

## Desafio 4

**a)** A ordem das regras importa, porque multiplicar e somar não podem ser trocados de lugar. Na primeira ordem, (150 × 5) + 200 = 950. Na segunda, (150 + 200) × 5 = 1750, pois o bônus entra antes e também é multiplicado.

**b)** Deve-se aplicar primeiro a blackFriday e depois o aniversarioCliente, ou seja, acumula blackFriday aniversarioCliente, que dá 950. Assim o bônus entra por último, depois da multiplicação, e não é multiplicado.

## Desafio 5 — revisão de código

| Erro | Função | O que estava errado | Como o GHC avisou (resumo da mensagem) | Como corrigimos |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |

## Desafio 6 — Haskell × C

Em Haskell dá para passar uma lambda direto na chamada, como calculaPontos (\p -> p * 3) 80. Em C não existe lambda: a função precisa ser declarada com nome antes de ser passada.
Em Haskell uma função pode devolver outra função que guarda valores, como campanhaMultiplicadora, que lembra o n. Em C isso não é natural, porque não dá para criar uma função nova que guarde um valor. Além disso, a sintaxe do tipo é mais pesada em C (int (*regra)(int)) do que em Haskell ((Int -> Int)).

## Evidência de execução

Saída do `main` de `fidelidade.hs`:

```text
120
240
170
240
--- Desafio 2 ---
80
160
130
240
170
--- Desafio 3 ---
750
350
100
55
--- Desafio 4 ---
950
1750
280
```

Saída do `main` de `revisao.hs` (depois de corrigido):

```text
40
100
400
200
```

Saída de `pontocerto.c`:

```text
160
130
250
300
```
