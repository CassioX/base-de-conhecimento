# Impressora não imprime

**Categoria:** Impressora · **Nível:** N1 · **Tempo médio:** 10–30 min

## Perguntas iniciais
1. Afeta só você ou todos que usam essa impressora?
2. Aparece alguma mensagem no visor da impressora?
3. O documento aparece na fila de impressão?

## Diagnóstico

**Se ninguém consegue imprimir → problema na impressora/rede/servidor de impressão.**
**Se só um usuário → problema no computador dele.**

1. **Impressora física**: ligada, papel, toner, atolamento, mensagem no visor
2. **Rede**: `ping IP_DA_IMPRESSORA` — sem resposta → cabo, IP mudou (DHCP), impressora fora da rede
3. **Porta de impressão**: `Test-NetConnection IP -Port 9100` (RAW/JetDirect)
4. **Fila travada**: Painel de Controle → Dispositivos e Impressoras → Ver o que está imprimindo
5. **Impressora padrão**: o usuário está mandando para a impressora certa?
6. **Driver**: imprime página de teste pelo Windows?

## Solução: limpar fila de impressão travada
```cmd
net stop spooler
del /Q /F %systemroot%\System32\spool\PRINTERS\*
net start spooler
```

## Outras soluções
- **IP da impressora mudou**: configurar IP fixo/reserva no DHCP e atualizar a porta no computador
- **Driver corrompido**: remover a impressora, remover o driver em *Propriedades do servidor de impressão → Drivers* e reinstalar
- **Impressão sai com caracteres estranhos**: driver errado (ex.: PCL x PostScript)
- **Impressora compartilhada**: verificar se o computador/servidor que compartilha está ligado

## Quando escalar
- Defeito de hardware (fusor, cilindro, erro de peça) → acionar fornecedor/contrato de locação
- Servidor de impressão com problema → N2
