# Computador lento

**Categoria:** Hardware/Software · **Nível:** N1 · **Tempo médio:** 20–40 min

## Sintomas
- Demora para ligar ou abrir programas
- Travamentos momentâneos, cursor "carregando"
- Ventoinha alta constantemente

## Perguntas iniciais
1. Lento o tempo todo ou só em algum programa/horário?
2. Começou depois de alguma atualização ou instalação?
3. Quando foi a última vez que o computador foi **reiniciado** (não só suspenso)?

## Diagnóstico

1. **Gerenciador de Tarefas** (`Ctrl+Shift+Esc`) → aba Processos, ordenar por CPU, Memória e **Disco**
   - Disco em 100% constante → HD mecânico lento/falhando ou processo de indexação/antivírus
   - Memória acima de 90% → pouca RAM para o uso ou programa com vazamento de memória
2. **Tempo ligado**: aba Desempenho → CPU → "Tempo de atividade". Dias sem reiniciar = reiniciar primeiro
3. **Espaço em disco**: menos de 15% livre no C: deixa o sistema lento
4. **Inicialização**: aba *Inicializar* → programas com impacto "Alto"
5. **Saúde do disco**:
   ```cmd
   wmic diskdrive get model,status
   ```
   Status diferente de `OK` → disco com problema, **fazer backup e escalar**
6. **Event Viewer** (`eventvwr.msc`) → Logs do Windows → Sistema → erros de disco (`disk`, `Ntfs`)
7. **Antivírus**: executar verificação completa

Script que coleta tudo isso: [`Diagnostico-Sistema.ps1`](https://github.com/CassioX/scripts-suporte/blob/main/windows/Diagnostico-Sistema.ps1)

## Soluções
| Causa | Ação |
|---|---|
| Muito tempo sem reiniciar | Reiniciar |
| Disco cheio | Limpeza de Disco (`cleanmgr`) ou [`Limpeza-Disco.ps1`](https://github.com/CassioX/scripts-suporte/blob/main/windows/Limpeza-Disco.ps1) |
| Muitos programas na inicialização | Desabilitar os desnecessários |
| Arquivos de sistema corrompidos | `sfc /scannow` e `DISM /Online /Cleanup-Image /RestoreHealth` |
| HD mecânico | Recomendar troca por SSD (maior ganho de desempenho) |
| Pouca RAM (≤ 4 GB) | Recomendar upgrade |
| Malware | Verificação completa, isolar da rede se confirmado |

## Quando escalar
- Disco com erros SMART / status diferente de OK
- Suspeita de malware que não é removido
- Necessidade de upgrade de hardware (aprovação do gestor)
