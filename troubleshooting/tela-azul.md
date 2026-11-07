# Tela azul (BSOD)

**Categoria:** Hardware/Sistema · **Nível:** N2 · **Tempo médio:** 30–90 min

## Primeiro passo: anotar o código de parada
A tela mostra um *stop code* (ex.: `MEMORY_MANAGEMENT`, `IRQL_NOT_LESS_OR_EQUAL`). Peça ao usuário uma **foto da tela**.

## Coletar informações
- **Event Viewer** → Logs do Windows → Sistema → evento **41 (Kernel-Power)** e **1001 (BugCheck)**
- Arquivos de despejo em `C:\Windows\Minidump` — analisar com **WinDbg** (`!analyze -v`) ou **BlueScreenView**
- Frequência: aconteceu uma vez ou se repete? Algo foi instalado antes?

## Códigos comuns

| Stop code | Causa provável | Ação |
|---|---|---|
| `MEMORY_MANAGEMENT` | Memória RAM com defeito | Diagnóstico de Memória do Windows (`mdsched.exe`) ou MemTest86 |
| `IRQL_NOT_LESS_OR_EQUAL` | Driver com defeito | Ver driver no minidump, atualizar/reverter |
| `CRITICAL_PROCESS_DIED` | Arquivos de sistema corrompidos | `sfc /scannow`, `DISM /RestoreHealth` |
| `INACCESSIBLE_BOOT_DEVICE` | Disco/controladora, modo SATA alterado na BIOS | Verificar BIOS (AHCI), saúde do disco |
| `VIDEO_TDR_FAILURE` | Driver de vídeo | Reinstalar driver com DDU |
| `NTFS_FILE_SYSTEM` | Sistema de arquivos corrompido | `chkdsk C: /f /r` |

## Roteiro
1. Se reiniciou após atualização/driver → **Restauração do Sistema** ou reverter o driver
2. Se não inicia → Inicialização Avançada → Modo de Segurança
3. `sfc /scannow` e `DISM /Online /Cleanup-Image /RestoreHealth`
4. `chkdsk C: /f /r` (agenda para o próximo boot)
5. Testar memória RAM
6. Verificar temperatura (superaquecimento) e saúde do disco

## Quando escalar
- Defeito de hardware confirmado (RAM, disco, placa-mãe) → troca/garantia
- Tela azul após atualização afetando várias máquinas → avisar a equipe e pausar a atualização
