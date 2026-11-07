# Sem acesso à internet

**Categoria:** Rede · **Nível:** N1 · **Tempo médio:** 10–20 min

## Sintomas
- Navegador mostra "Sem conexão" / "DNS_PROBE_FINISHED_NXDOMAIN"
- Ícone de rede com globo ou triângulo amarelo
- Alguns sites abrem e outros não

## Perguntas iniciais ao usuário
1. Só você está sem internet ou outras pessoas também? *(define se é problema local ou geral — muda a prioridade)*
2. Está no cabo ou no Wi-Fi?
3. Desde quando? Mudou algo (troca de lugar, atualização, novo equipamento)?

> Se **vários usuários** estão sem acesso → provável problema de infraestrutura (link, roteador, DHCP, DNS). Abrir como **P1** e escalar para N2/redes.

## Diagnóstico — de baixo para cima (camadas)

| Passo | Comando / Ação | Resultado esperado | Se falhar |
|---|---|---|---|
| 1. Física | Verificar cabo, luz da porta, Wi-Fi ligado, modo avião | Link ativo | Trocar cabo/porta, reconectar Wi-Fi |
| 2. IP | `ipconfig` | IP da rede (ex.: 192.168.0.x) | IP `169.254.x.x` = não recebeu do DHCP → `ipconfig /release` e `/renew` |
| 3. Gateway | `ping 192.168.0.1` (gateway do ipconfig) | Responde | Problema na rede local (switch, VLAN, Wi-Fi) |
| 4. Internet | `ping 8.8.8.8` | Responde | Problema no link/firewall → escalar |
| 5. DNS | `nslookup google.com` | Retorna IP | `ipconfig /flushdns`; testar DNS 8.8.8.8 |
| 6. Navegador | Testar outro navegador / aba anônima | Abre | Proxy configurado, extensão, cache |

**Dica:** se o `ping 8.8.8.8` funciona e o `ping google.com` não, o problema é **DNS**.

## Solução rápida (Windows, como administrador)
```cmd
ipconfig /flushdns
ipconfig /release
ipconfig /renew
netsh winsock reset
netsh int ip reset
```
Reiniciar o computador. Script automatizado: [`Reparar-Rede.ps1`](https://github.com/CassioX/scripts-suporte/blob/main/windows/Reparar-Rede.ps1)

## Outras causas comuns
- **Proxy** configurado errado: *Configurações → Rede e Internet → Proxy*
- **Conflito de IP**: aviso do Windows "conflito de endereço IP" → verificar IP fixo duplicado
- **Driver da placa de rede**: Gerenciador de Dispositivos → reinstalar/atualizar
- **VPN** conectada com rota errada

## Quando escalar (N2)
- Vários usuários afetados
- Gateway não responde para nenhum computador do setor
- DHCP sem IPs disponíveis
- Suspeita de bloqueio no firewall
