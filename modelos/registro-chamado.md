# Como registrar um chamado

Um bom registro permite que **qualquer colega continue o atendimento** sem precisar perguntar tudo de novo ao usuário.

## Estrutura

```
SOLICITANTE: Nome - Setor - Ramal
EQUIPAMENTO: Hostname / Patrimônio
PRIORIDADE: P1 | P2 | P3 | P4  (impacto x urgência)

PROBLEMA RELATADO:
O que o usuário disse, com as palavras dele e a mensagem de erro exata.

ANÁLISE:
- O que foi verificado e o resultado de cada teste.

SOLUÇÃO:
- O que resolveu de fato.

CAUSA RAIZ:
- Por que aconteceu (se identificado).

VALIDAÇÃO:
- Como foi confirmado que está resolvido e com quem.
```

## Exemplo real

```
SOLICITANTE: Juliana Alves - RH - Ramal 2034
EQUIPAMENTO: RH-00412
PRIORIDADE: P3 (setor imprime pela impressora do corredor como contorno)

PROBLEMA RELATADO:
"Mando imprimir e não sai nada na impressora do RH." Sem mensagem de erro.

ANÁLISE:
- Outros 3 usuários do RH com o mesmo problema -> não é a máquina da usuária.
- ping 192.168.0.50 -> sem resposta.
- Visor da impressora mostra IP 192.168.0.87 (recebeu novo IP do DHCP após queda de energia).

SOLUÇÃO:
- Criada reserva DHCP para o MAC da impressora com o IP 192.168.0.50.
- Impressora reiniciada, voltou com o IP correto. Fila liberada.

CAUSA RAIZ:
Impressora configurada em DHCP sem reserva; IP mudou após reinício.

VALIDAÇÃO:
Página de teste impressa pela Juliana e por mais um usuário do RH. Encerrado com aprovação dela.
```

## Classificando a prioridade

|  | **Urgência alta** | **Urgência baixa** |
|---|---|---|
| **Impacto alto** (vários usuários / serviço crítico) | P1 | P2 |
| **Impacto baixo** (um usuário) | P2 | P3 / P4 |
